# SQl Test Suites


## Table Structure

#### `employee` Table

| employee_id | user_name | employee_name | mobile | password | user_role_id | Dept_id | is_active | is_verified | Is_deleted | salary | created_at | updated_at
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 1	| albert | albert einstein    | +65 12312334 | ********* | 1 | 4 | True| True| False| 4920 |2021-03-24 02:06:52.404160| 2021-03-24 02:06:52.404160
| 2	| nizam  | nizam ismail 	| +65 11312355 | ********* | 2 | 2 | True | True | 	False | 6873 |2021-03-24 02:06:52.404160 | 2021-03-24 02:06:52.404160
| 3	| john	 | john monash   | +65 66312339 | ********* | 3 | 3 | True | True | 	False | 5487 |2021-03-24 02:06:52.404160 | 2021-03-24 02:06:52.404160
| 4	| robbin | robbin tan	| +65 76312456 | ********* | 4 | 3 | True | false |	False | 5596 |2021-04-24 02:06:52.404160 | 2021-04-26 02:06:52.404160
| 5	| patric | patric lee	| +65 45312543 | ********* | 5 | 4 | True | True | 	False | 4569 |2021-04-24 02:06:52.404160 | 2021-04-24 02:06:52.404160
| 6	| Jon    | john wick		| +65 96312435 | ********* | 6 | 2 | False | False |	False | 4676 |2021-04-24 02:06:52.404160 | 2021-04-24 02:06:52.404160
| 7	| stephens | stephen mil	| +65 87412743 | ********* | 7 | 1 | True | True | 	False | 5735 |2021-05-24 02:06:52.404160 | 2021-05-48 02:06:52.404160
| 8	| mike   | mike jackson		| +65 12326775 | ********* | 8 | 1 | True | True | 	False | 3934 |2021-05-24 02:06:52.404160 | 2021-05-27 02:06:52.404160
| 9	| hillyer| hillyer forman	| +65 18367456 | ********* | 9 | 3 | False | True | 	False | 7743 |2021-05-24 02:06:52.404160 | 2021-05-29 02:06:52.404160
|10	| robbin | robbin hood	| +65 99312343 | ********* | 10 | 4| True | True | 	False | null |2021-05-24 02:06:52.404160 | 2021-05-24 02:06:52.404160
___
#### `employee_role` Table

| employee_role_id | employee_id | role_id |
| :---: | :---: | :---: |
|1	| 1	| 1
|2	| 2	| 3
|3	| 3	| 2
|4	| 4	| 3
|5	| 5	| 4
|6	| 6	| 2
|7	| 7	| 5
|6	| 6	| 2
|8	| 8	| 5
|9	| 9	| 5
|10	| 10| 1
|11	| 2	| 4
|12	| 5	| 3
___
#### `role` Table

| role_id | role |
| :---: | :---: | 
|1	| SuperAdmin
|2	| admin
|3	| collector
|4	| trainer
|5	| officer
___
#### `department` Table

| dept_id | department |
| :---: | :---: | 
|1  | ADMIN
|2	| HR
|3	| ACCOUNT
|4	| ENGINEERING
___

## Question List

### Write sql queries for below scenarios

 - Fetch the department, no. of employees for each department in the descending order.

 - Fetch user name, role and department of the employee who are under role trainer and officer.

 - Fetch duplicate records if any and delete dullicate records in employee role table.

 - Update is_deleted:True and is_updateted:current_time for inactive and not verified user in HR department.

 - Update is_active:false for all employees working under engineering department.

 - Fetch Employee First Name, Department name, heighst salary and lowest salary by departments.

 - Fetch roles name if have multiple users.


### Fix the below error in the following provided SQL query. Implement your changes in the same query or change query to fix error.

 - `Cannot insert a NULL value into column transaction_tstamp` 

```
    INSERT INTO temp.transaction_dates (
        process_tstamp,
        transaction_tstamp )
        (
            WITH max_start_time AS(
                select max(transaction_tstamp) as transaction_tstamp
                from temp.transaction_start_dates
            ),
            max_complete_time AS (
                select max(transaction_tstamp) as transaction_tstamp
                from temp.transaction_end_dates
            )
            SELECT  getdate() as process_tstamp, max(transaction_tstamp) as transaction_tstamp
            FROM (
                    SELECT DISTINCT transaction_tstamp
                    FROM max_start_time
                    UNION ALL
                    SELECT DISTINCT transaction_tstamp
                    FROM max_complete_time
                )
        );
```