# SQL
This is for my SQL class notes from ISTM 624...

SELECT Buyer, Department 
FROM   SKU_DATA
ORDER BY Buyer DESC limit 5 ;

NaN: not a number; forget to type in data
Null: nothing, empty; usually hints to an error
So, we want to get rid of nulls

SELECT * (* means all)
FROM   SKU_DATA
WHERE  SKU >200000;

SELECT SKU_Description, Department 
FROM   SKU_DATA
WHERE  Department = 'Climbing';

SELECT Buyer, Department 
FROM   SKU_DATA
ORDER BY Buyer, Department DESC limit 5 ;

SELECT *
FROM ORDER_ITEM
ORDER BY OrderNumber, Price;

SELECT *
FROM ORDER_ITEM
ORDER BY Price DESC, OrderNumber ASC;
DefauLt: ASCENDING

Logical statement: T F 
Logical xxx : and , or, not

SELECT *
FROM SKU_DATA
WHERE Department = 'Water Sports'
OR Buyer = 'Nancy Meyers';  / AND NOT

VALUES: categories you want to compare

SELECT *
FROM SKU_DATA
WHERE Buyer IN ('Nancy Meyers', 'Cindy Lo', 'Jerry Martin');

SELECT *
FROM SKU_DATA
WHERE Department IN ('Camping', 'Climbing', 'Water Sports') AND NOT Buyer = 'Pete Hansen';


SELECT *
FROM SKU_DATA
WHERE Buyer = 'Nancy Meyers' OR Buyer = 'Cindy Lo' OR Buyer = 'Jerry Martin';

SELECT *
FROM ORDER_ITEM
WHERE ExtendedPrice BETWEEN 100 AND 200
ORDER BY ExtendedPrice;

SELECT *
FROM ORDER_ITEM
WHERE ExtendedPrice > 100
AND ExtendedPrice < 200
ORDER BY ExtendedPrice;   (this one might be better)

Wildcard: not in sports… buyer's name : just care about the first few letters Ara%... OR Ara__
Buyer LIKE 'Pete%';

SELECT *
FROM SKU_DATA
WHERE SKU_Description LIKE '%Tent%'

SELECT SUM(OrderTotal) AS test
FROM RETAIL_ORDER;

SELECT SUM(ExtendedPrice) AS orderitemsum,
AVG(ExtendedPrice) AS orderitemavg,
MIN(ExtendedPrice) AS orderitemmin,
MAX(ExtendedPrice) AS orderitemmx
FROM ORDER_ITEM;   (Seriously how to transpose this???)

Distinct to get rid of redundancy! 

SELECT COUNT(distinct Department) AS Deptcount
FROM SKU_DATA;

SELECT xx, xx, xx AS EP   3个colume名

SELECT SKU, SKU_Description, CONCAT(Buyer, 'in', Department) AS Sponsor
FROM SKU_DATA
ORDER BY SKU;

SELECT Department, COUNT(SKU) AS NumberOfCatalogItems
FROM CATALOG_SKU_2016
GROUP BY Department;

HAVING
