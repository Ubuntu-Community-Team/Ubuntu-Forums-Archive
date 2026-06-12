---
title: "PHP/MySQL connection not working"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by hanzi on 2006-10-15
I am trying to set up my Ubuntu Desktop to be a PHP/MySQL server. 

PHP works fine. [COLOR="Blue"]mysql[/COLOR] runs from the shell if I become root. [COLOR="Blue"]mysqld[/COLOR] is running.

Here is the problem: If I put this  into a PHP file:

[INDENT]$con = mysql_connect();
if (!$con)
die('Could not connect to MySQL: ' . mysql_error());
else
echo "MySQL is connected.";[/INDENT]

I get this error:

[INDENT]Could not connect to MySQL: Access denied for user 
'www-data'@'localhost' (using password: NO)[/INDENT]

What's wrong?
Thanks.

---

