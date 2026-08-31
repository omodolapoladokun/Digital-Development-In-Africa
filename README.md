# Digital Development in Africa

### Internet Adoption, Connectivity and Infrastructure Across 11 Selected African Countries | 2010–2024

This project examines how digital development has changed across 11 selected African countries using the World Bank World Development Indicators (WDI) dataset.

The analysis focuses on five areas that shape digital participation:

* Internet usage
* Mobile connectivity
* Fixed broadband access
* Electricity access
* Secure internet infrastructure

The central question behind the project was:

> **How has digital development changed across the selected African countries, where do major gaps remain, and which infrastructure differences deserve greater attention?**

The project covers the complete analytics workflow, from narrowing a very broad global development dataset to a focused analytical problem, cleaning and restructuring the data in Power Query, creating analytical measures in Power BI, comparing countries and trends, and translating the findings into recommendations for development and investment decisions.

---

## Dashboard Preview

<img width="632" height="368" alt="Digital Development In Africa Dashboard " src="https://github.com/user-attachments/assets/bce5665e-956f-4152-a7c0-4b5c3078403a" />


---

# Project Objective

Digital access is becoming increasingly important for economic participation, education, innovation, business growth, public-service delivery and inclusion.

However, progress in digital development is not evenly distributed across African countries.

This project was developed to understand:

* whether internet adoption has improved over time;
* which countries are progressing faster or slower;
* whether high mobile connectivity translates into actual internet usage;
* how electricity access relates to digital participation;
* whether fixed broadband infrastructure remains limited;
* how secure internet infrastructure differs across countries.

The aim was not simply to rank countries, but to understand the different components that contribute to digital development and identify areas where infrastructure gaps remain.

---

# Data Source

The analysis uses the **World Bank World Development Indicators (WDI)** dataset.

The original WDI dataset contains country-level development indicators across many areas, including:

* Economy
* Education
* Health
* Environment
* Infrastructure
* Technology
* Governance
* Trade

The original file contained country identifiers, indicator names, indicator codes and yearly columns from **1960 to 2025**.

Because the dataset was much broader than the project objective, I narrowed it to a digital-development theme and selected five indicators directly related to connectivity and enabling infrastructure.

---

# Selected Indicators

| Indicator                                        | Indicator Code   | Purpose                                  |
| ------------------------------------------------ | ---------------- | ---------------------------------------- |
| Individuals using the Internet (% of population) | `IT.NET.USER.ZS` | Measures actual internet adoption        |
| Mobile cellular subscriptions (per 100 people)   | `IT.CEL.SETS.P2` | Measures mobile connectivity             |
| Fixed broadband subscriptions (per 100 people)   | `IT.NET.BBND.P2` | Measures fixed digital infrastructure    |
| Access to electricity (% of population)          | `EG.ELC.ACCS.ZS` | Measures enabling infrastructure         |
| Secure Internet servers (per 1 million people)   | `IT.NET.SECR.P6` | Measures digital infrastructure capacity |

These indicators were selected because digital development is not determined by one measure alone.

For example, a country may have high mobile subscription rates while still having lower internet usage, weak fixed broadband infrastructure or limited secure internet capacity.

---

# Analysis Period

The main analysis period was restricted to:

**2010–2024**

The original dataset contained yearly observations from 1960 to 2025, but the selected indicators had more useful and comparable coverage within the 2010–2024 period.

**2024** was used as the latest comparison year in the Power BI dashboard.

---

# Data Preparation

The raw WDI dataset was originally stored in a **wide format**, where each year appeared as a separate column.

This structure was not ideal for time-series analysis in Power BI, so the dataset was transformed into a long format.

### Cleaning and transformation steps

1. Imported and inspected the original WDI dataset.
2. Filtered the dataset to the **11 selected African countries**.
3. Filtered the dataset to the **five selected digital-development indicators**.
4. Unpivoted the year columns into a single `Year` column.
5. Renamed the unpivoted `Attribute` column to `Year`.
6. Renamed the unpivoted `Value` column to `Indicator Value`.
7. Corrected data types.
8. Checked data coverage across countries and indicators.
9. Restricted the main analytical period to **2010–2024**.
10. Used **2024** as the latest year for cross-country comparison.

### Missing values

Missing values were retained as **null** rather than replaced with zero.

This distinction is important.

A missing observation means that no value was available for that country, indicator and year.

Replacing missing values with zero would incorrectly imply that the measured indicator was actually zero.

---

# Final Data Structure

After transformation, each row represented:

> **One country + one indicator + one year + one indicator value**

This long-format structure made it easier to:

* build time-series visuals;
* compare countries;
* filter indicators;
* create DAX measures;
* analyse relationships between infrastructure variables.

---

# Analytical Questions

The analysis was structured around seven main questions:

1. How has internet usage changed across the selected African countries over time?
2. Which countries currently have the highest and lowest internet adoption?
3. How has mobile connectivity changed across the selected countries?
4. Are there countries with high mobile subscriptions but lower internet usage?
5. How does electricity access relate to internet adoption?
6. Which countries show stronger digital infrastructure?
7. What digital-development gaps remain across the selected countries?

---

# Analysis Methodology

The project followed a structured analytical workflow:

**Theme Selection**

↓

**Indicator Selection**

↓

**Country Selection**

↓

**Data Cleaning**

↓

**Data Transformation**

↓

**Data Investigation**

↓

**KPI Creation**

↓

**Trend Analysis**

↓

**Relationship Analysis**

↓

**Dashboard Design**

↓

**Interpretation and Recommendations**

The analysis combined:

* Trend analysis
* Country comparison
* KPI analysis
* Relationship analysis
* Infrastructure comparison
* Business/development interpretation

---

# Power BI Dashboard

The final report was designed as a **one-page executive dashboard**.

The objective was to make the major findings understandable without requiring users to inspect the raw WDI dataset.

The dashboard contains:

### KPI Cards

* Average Internet Usage %
* Average Mobile Subscriptions
* Average Fixed Broadband
* Average Electricity Access %

### Main Visuals

* Internet Adoption Trend, 2010–2024
* Internet Adoption by Country, 2024
* Mobile Connectivity vs Internet Adoption, 2024
* Electricity Access vs Internet Adoption, 2024
* Secure Internet Servers by Country, 2024

### Interaction

* Country slicer
* Interactive filtering
* Key takeaway section

---

# DAX Measures

Several measures were created to isolate 2024 indicator values.

Example:

```DAX
Internet Usage 2024 =
CALCULATE(
    AVERAGE('WDICSV'[Indicator Value]),
    'WDICSV'[Indicator Code] = "IT.NET.USER.ZS",
    'WDICSV'[Year] = 2024
)
```

```DAX
Electricity Access 2024 =
CALCULATE(
    AVERAGE('WDICSV'[Indicator Value]),
    'WDICSV'[Indicator Code] = "EG.ELC.ACCS.ZS",
    'WDICSV'[Year] = 2024
)
```

```DAX
Mobile Subscriptions 2024 =
CALCULATE(
    AVERAGE('WDICSV'[Indicator Value]),
    'WDICSV'[Indicator Code] = "IT.CEL.SETS.P2",
    'WDICSV'[Year] = 2024
)
```

```DAX
Secure Servers 2024 =
CALCULATE(
    AVERAGE('WDICSV'[Indicator Value]),
    'WDICSV'[Indicator Code] = "IT.NET.SECR.P6",
    'WDICSV'[Year] = 2024
)
```


# Key Findings

## 1. Internet adoption improved between 2010 and 2024

Internet usage increased across the selected African countries over the analysis period.

However, progress was not uniform.

Some countries advanced considerably faster than others, meaning that digital development cannot be described using a single continental average.

### Interpretation

The improvement shows that digital participation is expanding, but substantial differences remain in the pace and level of adoption.

---

# 2. Mobile connectivity is generally higher than actual internet usage

Mobile cellular subscriptions were generally higher than the percentage of people actually using the internet.

### Interpretation

A high mobile-subscription rate does not automatically mean that the same proportion of the population is meaningfully participating online.

Mobile connectivity therefore represents an important access channel, but it should not be treated as the final measure of digital inclusion.

---

# 3. Fixed broadband remains limited

Fixed broadband access remained much lower than mobile connectivity across the selected countries.

### Interpretation

This suggests that digital access across much of the sample remains heavily dependent on mobile infrastructure.

The gap matters because fixed broadband can support higher-capacity activities such as:

* business operations;
* remote work;
* digital education;
* cloud-based services;
* research;
* advanced digital platforms.

---

# 4. Electricity access appears to support digital adoption

The electricity-versus-internet comparison showed that countries with stronger electricity access were generally better positioned for stronger internet adoption.

### Interpretation

Reliable power is an important enabling condition for digital participation because internet infrastructure, devices, businesses and digital services depend on electricity.

However, the analysis does not prove that electricity access alone causes higher internet usage.

Other factors such as affordability, infrastructure investment, income, education, regulation and service availability may also contribute.

---

# 5. Secure internet infrastructure remains uneven

Secure internet server availability differed considerably across the selected countries.

### Interpretation

Digital development is not only about whether people can connect to the internet.

Countries also require infrastructure capable of supporting:

* secure digital services;
* e-commerce;
* e-government;
* digital payments;
* online business;
* secure data exchange.

Differences in secure server availability therefore provide another view of digital infrastructure maturity.

---

# 6. Digital development is multidimensional

One of the most important findings from the project is that no single indicator is sufficient for evaluating digital progress.

A country may have:

* high mobile subscriptions;
* lower internet usage;
* weak fixed broadband;
* limited secure infrastructure;
* or electricity-access constraints.

Digital development therefore depends on a combination of:

* connectivity;
* infrastructure;
* affordability;
* electricity;
* digital services;
* policy support;
* access quality.

---

# Key Insights

The analysis suggests that the digital divide is both:

### An access problem

Some populations still have limited access to internet services.

### An infrastructure-readiness problem

Even where mobile connectivity exists, countries may still lack:

* sufficient broadband;
* reliable electricity;
* secure internet infrastructure;
* affordable access.

This means that increasing mobile subscriptions alone is not enough to guarantee meaningful digital inclusion.

---

# Recommendations

## 1. Expand affordable broadband infrastructure

Countries where mobile subscriptions are high but internet usage remains lower should investigate barriers preventing mobile connectivity from translating into meaningful internet access.

Broadband affordability and availability should remain important development priorities.

---

## 2. Continue investment in electricity infrastructure

Reliable electricity remains an important foundation for digital participation.

Governments and development partners should continue improving power access, particularly in underserved areas.

---

## 3. Prioritise rural and underserved connectivity

National-level indicators can hide significant differences between urban and rural populations.

Infrastructure programmes should therefore pay particular attention to areas where connectivity remains limited.

---

## 4. Avoid measuring digital progress using mobile subscriptions alone

Mobile subscription rates should be treated as one indicator of connectivity, not as a complete measure of digital development.

Decision makers should combine:

* internet usage;
* broadband access;
* electricity access;
* secure infrastructure;
* and other affordability or access indicators.

---

## 5. Strengthen secure internet infrastructure

Countries should invest in the infrastructure required to support:

* digital business;
* e-government;
* secure online transactions;
* digital financial services;
* broader participation in the digital economy.

---

## 6. Use country-level evidence to guide digital investment

The selected countries do not face identical digital-development challenges.

Investment priorities should therefore reflect the specific combination of access, infrastructure and connectivity gaps present in each country.

---

# Limitations

Several limitations should be considered when interpreting this analysis.

### 1. Selected countries only

The project covers **11 selected African countries**, not all African countries.

The findings therefore describe the selected sample rather than the entire continent.

### 2. Country-level averages hide internal inequality

National averages may hide differences between:

* rural and urban populations;
* income groups;
* regions;
* age groups;
* education levels.

### 3. Mobile subscriptions can exceed population size

Mobile cellular subscriptions are reported per 100 people.

One person may own multiple SIM cards or subscriptions, so values above 100 do not necessarily mean that every individual has mobile access.

### 4. Relationships do not prove causation

The electricity-versus-internet visual identifies a relationship in the data.

It does not establish that electricity access directly causes higher internet adoption.

### 5. Missing data varies across indicators

Not every country has equally complete data for every indicator and year.

Missing observations were therefore retained as null rather than treated as zero.

### 6. Latest-year comparisons depend on data coverage

The dashboard uses **2024** for latest-year comparisons, but indicator availability may differ across countries.

---

# Skills Demonstrated

This project demonstrates practical experience in:

### Data Analysis

* Problem framing
* Data investigation
* Indicator selection
* Trend analysis
* Comparative analysis
* Relationship analysis
* Insight development

### Data Preparation

* Power Query
* Data filtering
* Wide-to-long transformation
* Data-type correction
* Missing-value handling
* Data-quality review

### Business Intelligence

* Power BI
* DAX
* KPI design
* Dashboard development
* Executive reporting
* Interactive filtering
* Data storytelling

### Analytical Judgment

* Distinguishing missing values from zero
* Separating correlation from causation
* Interpreting multiple indicators together
* Identifying analytical limitations
* Translating findings into development recommendations

---


# What I Learned

The most important lesson from this project was that a broad dataset does not automatically produce a useful analysis.

The original World Bank dataset contained many countries, indicators and decades of observations.

The analytical work began by narrowing that information into a specific problem, selecting only the indicators relevant to that problem, and deciding what each indicator could and could not explain.

The project also reinforced that:

> **a measure is not meaningful simply because it is available.**

Mobile subscriptions, for example, provide useful information about connectivity, but they do not completely explain actual internet participation.

Similarly, a relationship between electricity access and internet adoption does not automatically establish causation.

Understanding those distinctions helped make the final dashboard more useful than simply presenting country rankings.

---

# Conclusion

Digital access improved across the selected African countries between 2010 and 2024, but the analysis shows that progress remains uneven.

Mobile connectivity has expanded strongly, yet actual internet participation, fixed broadband, electricity access and secure internet infrastructure still differ substantially across countries.

The main conclusion is that digital development should be viewed as an **ecosystem rather than a single connectivity measure**.

Meaningful digital participation depends on several conditions working together:

* access;
* infrastructure;
* electricity;
* affordability;
* secure digital systems;
* policy support.

The dashboard provides a focused view of these differences and can support further discussion around digital investment, infrastructure planning and development priorities across the selected countries.


## Author

**Omodolapo Oladokun**
Data Analyst

[LinkedIn](https://www.linkedin.com/in/omodolapoladokun)
[GitHub](https://github.com/omodolapoladokun)
