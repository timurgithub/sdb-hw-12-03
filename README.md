
# Домашнее задание к занятию «SQL. Часть 1» - `Акаев Тимур`

### Задание 1

Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.

```sql
SELECT DISTINCT district AS Название_районов FROM sakila.address 
WHERE district LIKE 'K%'
  AND district LIKE '%a'
  AND district NOT LIKE '% %';
```

### Задание 2

Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года **включительно** и стоимость которых превышает 10.00.

```sql
SELECT * FROM sakila.payment p 
WHERE p.payment_date BETWEEN '2005-06-15 00:00:00' AND '2005-06-18 23:59:59'
AND p.amount > 10;
```

### Задание 3

Получите последние пять аренд фильмов.

```sql
SELECT * FROM sakila.rental r 
ORDER BY r.rental_date DESC
LIMIT 5;
```

### Задание 4

Одним запросом получите активных покупателей, имена которых Kelly или Willie. 

Сформируйте вывод в результат таким образом:
- все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
- замените буквы 'll' в именах на 'pp'.

```sql
SELECT 
  LOWER(REPLACE(LOWER(c.first_name), 'll', 'pp')), 
  c.active
FROM sakila.customer c
WHERE (LOWER(c.first_name) = 'Kelly' OR LOWER(c.first_name) = 'Willie')
  AND c.active = 1;
```