# Automotive Manufacturing Optimization

## Problem Statement
To improve the operational efficiency and profitability of an automotive manufacturing company by analyzing production, costs, employee productivity, and sales data to identify areas for process optimization, cost reduction, and sales growth.

## Problem Statement
To improve the operational efficiency and profitability of an automotive manufacturing company by analyzing production, costs, employee productivity, and sales data to identify areas for process optimization, cost reduction, and sales growth.

---

## Objectives

1. **Maximize Production Efficiency**: Analyze production performance and identify bottlenecks to improve output.
2. **Optimize Operational Costs**: Investigate areas where costs can be reduced without sacrificing quality or productivity.
3. **Enhance Employee Productivity**: Identify trends in employee efficiency and recommend training or process improvements.

---

## Insights

### Operations and Cost
- Pending status accounted for **36.41%** of the Total Amount.
- Model Z had the highest Total Defective Units at **5,391**, which was **60.69%** higher than Model A (lowest at 3,355).
- There is a positive correlation between the Total Number of Defective Units and the Total Number of Units Produced.
- The largest divergence between Units Produced and Total Defective Units occurred for Model Z, with **52,270 more units produced** than defective units.
- Plant B (Approval Status: Approved) contributed **9.40%** to the Total Amount (INR).

### Revenue
- Revenue trended downward, decreasing by **80.37%** between 2023 and 2025.
- The decline began in 2023, resulting in a drop of **$737,509,948** over 2 years.
- Revenue experienced its steepest drop, falling from **$917,598,374** to **$180,088,426** between 2023 and 2025.
- Model Y recorded the highest Sum of Units Sold (**164,690**) and Sum of Revenue (**$43,440,760**).
- Model Y contributed **21.34%** to the total Revenue.

### Employee Performance
- **Moderately Efficient** had the highest employee count at **400**, followed by **Inefficient** at **323** and **Highly Efficient** at **179**.
- **Moderately Efficient** accounted for **44.35%** of the workforce.
- **EMP_1** had the highest Average Efficiency at **4.1**, which was **235.03% higher** than EMP_281 with the lowest Average Efficiency of **1.2**.

---

## Measures

1. **LM Revenue**: 
   ```DAX
   LM Revenue = CALCULATE([Revenue], PREVIOUSMONTH('Vehicle Sales Data'[Sale Date]))
   ```
2. **MoM Change**: 
   ```DAX
   MoMChange = IF(ISBLANK([LM Revenue]), BLANK(), [Revenue] / [LM Revenue] - 1)
   ```
3. **No Of Employees**: 
   ```DAX
   NoOfEmployees = COUNT('Employee Productivity'[Employee ID])
   ```
4. **Revenue**: 
   ```DAX
   Revenue = SUM('Vehicle Sales Data'[Revenue])
   ```
5. **Revenue MTD**: 
   ```DAX
   RevenueMTD = TOTALMTD([Revenue], 'Vehicle Sales Data'[Sale Date].[Date])
   ```
6. **Target**: 
   ```DAX
   Target = (CALCULATE([Revenue], PREVIOUSMONTH('Vehicle Sales Data'[Sale Date].[Date])) * 1.02)
   ```

---

## Calculated Columns

1. **Efficiency**: 
   ```DAX
   efficiency = 'Employee Productivity'[Units Handled] / 'Employee Productivity'[Hours Worked]
   ```
2. **Employee Type**: 
   ```DAX
   EmployeeType = SWITCH(TRUE(),
                          'Employee Productivity'[efficiency] > 4, "Highly Efficient",
                          'Employee Productivity'[efficiency] >= 2, "Moderately Efficient",
                          'Employee Productivity'[efficiency] < 2, "Inefficient")
   ```
---

## How to Use

1. Clone this repository:
   ```bash
   git clone https://github.com/your-organization/automotive-optimization.git
   ```

2. Navigate to the repository folder:
   ```bash
   cd automotive-optimization
   ```

3. Explore the `notebooks` directory for detailed analysis or use the `scripts` for automated data processing.

4. Open dashboards in Power BI or Tableau to visualize insights.

---

## Contributing

Contributions are welcome! Please fork the repository and create a pull request with your changes.

---

## License

This project is licensed under the MIT License. See the LICENSE file for details.

---

## Contact

For questions or support, please contact [email@example.com].
