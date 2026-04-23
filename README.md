# 242002017-CSE210-242D3-LabReport04-Constraints-AlterUntitled-
# Faculty Salary Automation System (SQL Triggers)

This repository contains the implementation of **Database Triggers** to automate salary management and audit logging for a faculty database. The project was developed as part of the **CSE210 (Database Management Systems)** course.

## 📌 Project Goals
- To automate salary increments based on job tenure and research publications.
- To maintain a secure audit trail (Salary Log) of every update made to the employee records.
- To demonstrate the use of `BEFORE UPDATE` and `AFTER UPDATE` triggers.

## 📊 Business Logic (Increment Policy)
The system automatically calculates the `UpdatedSalary` according to the following criteria:

| Condition | Increment % |
| :--- | :---: |
| Experience > 1 Year AND Publications > 4 | **20%** |
| Experience > 1 Year AND Publications = 2 or 3 | **10%** |
| Experience > 1 Year AND Publications = 1 | **5%** |
| Experience ≤ 1 Year OR Publications = 0 | **0%** |

## 🛠️ Database Schema

### 1. EMPLOYEE Table
Stores the main profile of the faculty members.
- `EmpID`: Primary Key.
- `NoOfPub`: Number of publications (must be ≥ 0).
- `IncrementRate`: Calculated automatically by the trigger.
- `UpdatedSalary`: Final salary calculated after increment.

### 2. SALARY_LOG Table
Stores history of all salary changes for transparency.
- `OldSalary`: Salary before the change.
- `NewSalary`: Salary after the change.
- `Note`: Automatically generated message explaining the increment.

## 🚀 How to Run
1. Clone this repository.
2. Open your MySQL environment (Workbench, XAMPP, or Terminal).
3. Import and run the `ID-CSE210-242D3-LabReport04-Triggers.sql` file.
4. To test the triggers, run an update statement:
   ```sql
   UPDATE EMPLOYEE SET NoOfPub = 5 WHERE EmpID = 101;
