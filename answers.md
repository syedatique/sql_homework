
## SQL Questions

Using the SQLite3 Database file given to you as the source of data to answer the questions.  Copy and the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.



1. Select the names of all users.
Ans : select name from users;
Rick Henri
Michael Pavling
Sandy McMillan
Chae Cramb
Syed Atique
Simon Osborne
Kieran Pringle
Craig Lamont
Zsolt Podoba
Keith Martin
Peter Hyder
Alaere Samuel
Kathryn Kiernan
Iwona Sztorc
Nevin Officer
Graeme Stewart
Neil McGuire
Graeme Kean


2. Select the names of all shows that cost less than £15.
Ans: select name from shows where price < 15.00;
Le Haggis
Paul Dabek Mischief
Best of Burlesque
Two become One
Urinetown
Two girls, one cup of comedy

3. Select the names and prices of all shows, ordered by price in ascending order.
Ans: select name, price from shows order by price;
Two girls, one cup of comedy|6.0
Best of Burlesque|7.99
Two become One|8.5
Urinetown|8.5
Le Haggis|12.99
Paul Dabek Mischief |12.99
Shitfaced Shakespeare|16.5
Game of Thrones - The Musical|16.5
Joe Stilgoe: Songs on Film – The Sequel|16.5
Camille O'Sullivan|17.99
Aaabeduation – A Magic Show|17.99
Balletronics|32.0
Edinburgh Royal Tattoo|32.99

4. Select the average price of all shows.
Ans:
select avg(price) from shows;    15.9569230769231

5. Select the price of the least expensive show.
ANS: select min(price) from shows;    6.0

6. Select the sum of the price of all shows.
Ans: select sum(price) from shows;  207.44

7. Select the sum of the price of all shows whose prices is less than £20.
Ans: select sum(price) from shows where price < 20;    142.45

8. Select the name and price of the most expensive show.
Ans: select name, price from shows where price = (select max(price) from shows);     Edinburgh Royal Tattoo|32.99

9. Select the name and price of the second from cheapest show.
Ans: select name, price from shows order by price LIMIT 1 OFFSET 1; Best of Burlesque|7.99

10. Select the time for the Edinburgh Royal Tattoo.
Ans:  select time from times where id = ( select id from shows where name = 'Edinburgh Royal Tattoo'); 22:00

11. Select the names of all users whose names start with the letter "N".
Ans:  select name from users where name like 'N%';
      Nevin Officer
      Neil McGuire

12. Select the names of users whose names contain "mi".
Ans: select name from users where name like '%mi%';
      Michael Pavling
      Sandy McMillan

13. Select the number of users who want to see "Shitfaced Shakespeare".
Ans:  select count(*) as 'id' from users where id in (select user_id from shows_users where show_id = ( select id from shows where name = 'Shitfaced Shakespeare'));   7

TODO: 14. Select all of the user names and the count of shows they're going to see. {-- don't work ---select user_id, count(show_id) as show_id from shows_users group by user_id join users on users.id = ;}

15. SELECT all users who are going to a show at 17:15.
Ans: select name from users where id in (select user_id from shows_users where show_id = (select show_id from times where time = '17:15'));
Rick Henri
Sandy McMillan
Syed Atique
Craig Lamont
Zsolt Podoba
Kathryn Kiernan
Nevin Officer

16. Insert a user with the name "Antonio Goncalves" into the users table.
Ans: insert into users (name) values ('Antonio Goncalves');

17. Select the id of the user with your name.
Ans: select id from users where name = 'Syed Atique';    5

18. Insert a record that Antonio Goncalves wants to attend the show "Two girls, one cup of comedy".
Ans : insert into "shows_users" (show_id, user_id) values ((select id from shows where name = 'Two girls, one cup of comedy'), (select id from users where name = 'Antonio Goncalves'));

19. Updates the name of the "Antonio Goncalves" user to be "Tony Goncalves".
Ans: update users set name = 'Tony Goncalves' where name ='Antonio Goncalves';

20. Deletes the user with the name 'Tony Goncalves'.
Ans: delete from users where name = 'Tony Goncalves';

21. Deletes the shows for the user you just deleted.
Ans: delete from shows_users where user_id > (select count(id) from users);


## Hints

  - As with anything, if you get stuck, move on, then go back if you have time.
  - Don't spend all night on it!
  - Use resources online to solve harder ones - there are solutions to these questions that work with what we've learnt today, but other tools exist in SQL that could make the queries 'better' or 'easier'.
