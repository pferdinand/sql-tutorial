# Introduction

Download and load a sample database:

https://www.mysqltutorial.org/mysql-sample-database.aspx

## Switch to a database

```
mysql> use classicmodels;
```

## Display the list of tables in the database

```
mysql> show tables;
+-------------------------+
| Tables_in_classicmodels |
+-------------------------+
| customers               |
| employees               |
| offices                 |
| orderdetails            |
| orders                  |
| payments                |
| productlines            |
| products                |
+-------------------------+
```

## Describe a table

```
mysql> desc customers;
+------------------------+---------------+------+-----+---------+-------+
| Field                  | Type          | Null | Key | Default | Extra |
+------------------------+---------------+------+-----+---------+-------+
| customerNumber         | int           | NO   | PRI | NULL    |       |
| customerName           | varchar(50)   | NO   |     | NULL    |       |
| contactLastName        | varchar(50)   | NO   |     | NULL    |       |
| contactFirstName       | varchar(50)   | NO   |     | NULL    |       |
| phone                  | varchar(50)   | NO   |     | NULL    |       |
| addressLine1           | varchar(50)   | NO   |     | NULL    |       |
| addressLine2           | varchar(50)   | YES  |     | NULL    |       |
| city                   | varchar(50)   | NO   |     | NULL    |       |
| state                  | varchar(50)   | YES  |     | NULL    |       |
| postalCode             | varchar(15)   | YES  |     | NULL    |       |
| country                | varchar(50)   | NO   |     | NULL    |       |
| salesRepEmployeeNumber | int           | YES  | MUL | NULL    |       |
| creditLimit            | decimal(10,2) | YES  |     | NULL    |       |
+------------------------+---------------+------+-----+---------+-------+
```

## Displaying the records in a table

```
mysql> SELECT * FROM customers;
+----------------+------------------------------------+-----------------+------------------+--------------------+----------------------------------+--------------------------+-------------------+---------------+------------+--------------+------------------------+-------------+
| customerNumber | customerName                       | contactLastName | contactFirstName | phone              | addressLine1                     | addressLine2             | city              | state         | postalCode | country      | salesRepEmployeeNumber | creditLimit |
+----------------+------------------------------------+-----------------+------------------+--------------------+----------------------------------+--------------------------+-------------------+---------------+------------+--------------+------------------------+-------------+
|            103 | Atelier graphique                  | Schmitt         | Carine           | 40.32.2555         | 54, rue Royale                   | NULL                     | Nantes            | NULL          | 44000      | France       |                   1370 |    21000.00 |
|            112 | Signal Gift Stores                 | King            | Jean             | 7025551838         | 8489 Strong St.                  | NULL                     | Las Vegas         | NV            | 83030      | USA          |                   1166 |    71800.00 |
|            114 | Australian Collectors, Co.         | Ferguson        | Peter            | 03 9520 4555       | 636 St Kilda Road                | Level 3                  | Melbourne         | Victoria      | 3004       | Australia    |                   1611 |   117300.00 |
|            119 | La Rochelle Gifts                  | Labrune         | Janine           | 40.67.8555         | 67, rue des Cinquante Otages     | NULL                     | Nantes            | NULL          | 44000      | France       |                   1370 |   118200.00 |
|            121 | Baane Mini Imports                 | Bergulfsen      | Jonas            | 07-98 9555         | Erling Skakkes gate 78           | NULL                     | Stavern           | NULL          | 4110       | Norway       |                   1504 |    81700.00 |
...
```

### Filtering records

```
mysql> SELECT * FROM customers WHERE postalcode='44000';
+----------------+-------------------+-----------------+------------------+------------+------------------------------+--------------+--------+-------+------------+---------+------------------------+-------------+
| customerNumber | customerName      | contactLastName | contactFirstName | phone      | addressLine1                 | addressLine2 | city   | state | postalCode | country | salesRepEmployeeNumber | creditLimit |
+----------------+-------------------+-----------------+------------------+------------+------------------------------+--------------+--------+-------+------------+---------+------------------------+-------------+
|            103 | Atelier graphique | Schmitt         | Carine           | 40.32.2555 | 54, rue Royale               | NULL         | Nantes | NULL  | 44000      | France  |                   1370 |    21000.00 |
|            119 | La Rochelle Gifts | Labrune         | Janine           | 40.67.8555 | 67, rue des Cinquante Otages | NULL         | Nantes | NULL  | 44000      | France  |                   1370 |   118200.00 |
+----------------+-------------------+-----------------+------------------+------------+------------------------------+--------------+--------+-------+------------+---------+------------------------+-------------+
2 rows in set, 20 warnings (0.00 sec)
```

### Explicitly selecting columns

```
mysql> select contactFirstName, contactLastName, postalCode FROM customers WHERE postalcode=44000;
+------------------+-----------------+------------+
| contactFirstName | contactLastName | postalCode |
+------------------+-----------------+------------+
| Carine           | Schmitt         | 44000      |
| Janine           | Labrune         | 44000      |
+------------------+-----------------+------------+
2 rows in set, 20 warnings (0.00 sec)
```

