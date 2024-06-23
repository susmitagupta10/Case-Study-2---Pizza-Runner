# Case-Study-2---Pizza-Runner link https://8weeksqlchallenge.com/case-study-2/


![Screenshot 2024-06-23 191045](https://github.com/susmitagupta10/Case-Study-2---Pizza-Runner/assets/166834605/a699a55e-92c4-444b-b431-764c59e9f0ba)
![Screenshot 2024-06-23 191113](https://github.com/susmitagupta10/Case-Study-2---Pizza-Runner/assets/166834605/8a7595b5-9b1b-414e-a7a0-3b03ff764033)
![Screenshot 2024-06-23 191131](https://github.com/susmitagupta10/Case-Study-2---Pizza-Runner/assets/166834605/c0d1bb11-29c0-4df5-8e6c-61c69085327f)
![Screenshot 2024-06-23 191145](https://github.com/susmitagupta10/Case-Study-2---Pizza-Runner/assets/166834605/35808ef7-f738-4657-80f4-e3b216d7ecef)
![Screenshot 2024-06-23 191205](https://github.com/susmitagupta10/Case-Study-2---Pizza-Runner/assets/166834605/8f6f9dd1-8f4e-48e6-9cfd-6f683ff485c7)
![Screenshot 2024-06-23 191219](https://github.com/susmitagupta10/Case-Study-2---Pizza-Runner/assets/166834605/8984df37-4574-4299-8a02-f19c045ec13f)
![Screenshot 2024-06-23 191240](https://github.com/susmitagupta10/Case-Study-2---Pizza-Runner/assets/166834605/89d49356-163e-4a26-bd2b-062d568e115b)
![Screenshot 2024-06-23 191254](https://github.com/susmitagupta10/Case-Study-2---Pizza-Runner/assets/166834605/87809318-a862-4c3a-b78d-ea9ca01a2529)
![Screenshot 2024-06-23 191308](https://github.com/susmitagupta10/Case-Study-2---Pizza-Runner/assets/166834605/a55aef9d-7e98-4471-90d7-af936e976507)
![Screenshot 2024-06-23 191320](https://github.com/susmitagupta10/Case-Study-2---Pizza-Runner/assets/166834605/5d0c8801-6d3b-44bc-a337-f52c26f13179)

#CREATE SCHEMA#

CREATE SCHEMA pizza_runner;
USE pizza_runner;
CREATE TABLE runners (
  runner_id INTEGER,
  registration_date DATE
);
INSERT INTO runners
  (runner_id, registration_date)
VALUES
  (1, '2021-01-01'),
  (2, '2021-01-03'),
  (3, '2021-01-08'),
  (4, '2021-01-15');



CREATE TABLE customer_orders (
  order_id INTEGER,
  customer_id INTEGER,
  pizza_id INTEGER,
  exclusions VARCHAR(4),
  extras VARCHAR(4),
  order_time TIMESTAMP
);

INSERT INTO customer_orders
  (order_id, customer_id, pizza_id, exclusions, extras, order_time)
VALUES
  ('1', '101', '1', '', '', '2020-01-01 18:05:02'),
  ('2', '101', '1', '', '', '2020-01-01 19:00:52'),
  ('3', '102', '1', '', '', '2020-01-02 23:51:23'),
  ('3', '102', '2', '', NULL, '2020-01-02 23:51:23'),
  ('4', '103', '1', '4', '', '2020-01-04 13:23:46'),
  ('4', '103', '1', '4', '', '2020-01-04 13:23:46'),
  ('4', '103', '2', '4', '', '2020-01-04 13:23:46'),
  ('5', '104', '1', 'null', '1', '2020-01-08 21:00:29'),
  ('6', '101', '2', 'null', 'null', '2020-01-08 21:03:13'),
  ('7', '105', '2', 'null', '1', '2020-01-08 21:20:29'),
  ('8', '102', '1', 'null', 'null', '2020-01-09 23:54:33'),
  ('9', '103', '1', '4', '1, 5', '2020-01-10 11:22:59'),
  ('10', '104', '1', 'null', 'null', '2020-01-11 18:34:49'),
  ('10', '104', '1', '2, 6', '1, 4', '2020-01-11 18:34:49');


DROP TABLE IF EXISTS runner_orders;
CREATE TABLE runner_orders (
  order_id INTEGER,
  runner_id INTEGER,
  pickup_time VARCHAR(19),
  distance VARCHAR(7),
  duration VARCHAR(10),
  cancellation VARCHAR(23)
);

INSERT INTO runner_orders
  (order_id, runner_id, pickup_time, distance, duration, cancellation)
VALUES
  ('1', '1', '2020-01-01 18:15:34', '20km', '32 minutes', ''),
  ('2', '1', '2020-01-01 19:10:54', '20km', '27 minutes', ''),
  ('3', '1', '2020-01-03 00:12:37', '13.4km', '20 mins', NULL),
  ('4', '2', '2020-01-04 13:53:03', '23.4', '40', NULL),
  ('5', '3', '2020-01-08 21:10:57', '10', '15', NULL),
  ('6', '3', 'null', 'null', 'null', 'Restaurant Cancellation'),
  ('7', '2', '2020-01-08 21:30:45', '25km', '25mins', 'null'),
  ('8', '2', '2020-01-10 00:15:02', '23.4 km', '15 minute', 'null'),
  ('9', '2', 'null', 'null', 'null', 'Customer Cancellation'),
  ('10', '1', '2020-01-11 18:50:20', '10km', '10minutes', 'null');


DROP TABLE IF EXISTS pizza_names;
CREATE TABLE pizza_names (
  pizza_id INTEGER,
  pizza_name TEXT
);
INSERT INTO pizza_names
  (pizza_id, pizza_name)
VALUES
  (1, 'Meatlovers'),
  (2, 'Vegetarian');


DROP TABLE IF EXISTS pizza_recipes;
CREATE TABLE pizza_recipes (
  pizza_id INTEGER,
  toppings TEXT
);
INSERT INTO pizza_recipes
  (pizza_id, toppings)
VALUES
  (1, '1, 2, 3, 4, 5, 6, 8, 10'),
  (2, '4, 6, 7, 9, 11, 12');


DROP TABLE IF EXISTS pizza_toppings;
CREATE TABLE pizza_toppings (
  topping_id INTEGER,
  topping_name TEXT
);
INSERT INTO pizza_toppings
  (topping_id, topping_name)
VALUES
  (1, 'Bacon'),
  (2, 'BBQ Sauce'),
  (3, 'Beef'),
  (4, 'Cheese'),
  (5, 'Chicken'),
  (6, 'Mushrooms'),
  (7, 'Onions'),
  (8, 'Pepperoni'),
  (9, 'Peppers'),
  (10, 'Salami'),
  (11, 'Tomatoes'),
  (12, 'Tomato Sauce');




