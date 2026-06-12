---
title: "Connecting to MS SQL 2000 from PHP"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by samalex on 2007-05-07
Hi...

I've followed the wonderful tutorial at [http://panthar.org/2006/06/15/php-with-mssql-on-ubuntu-606/](http://panthar.org/2006/06/15/php-with-mssql-on-ubuntu-606/) to install the mssql function into PHP, and the installation seemed to go perfectly.

I'm using Ubuntu 6.10 Server with LAMP installed at startup, and installing all the steps noted in this tutorial went exactly as expected.  Afterwards I had a number of .deb packages, two of which are for mssql:
php5-mysql_5.1.6-1ubuntu2.4_i386.deb
php5-mysqli_5.1.6-1ubuntu2.4_i386.deb

Already having php installed, I just used 'dpkg -i' to install both of these packages, and they seemed to install properly:

```

# dpkg -i php5-mysql_5.1.6-1ubuntu2.4_i386.deb
(Reading database ... 45397 files and directories currently installed.)
Preparing to replace php5-mysql 5.1.6-1ubuntu2.4 (using php5-mysql_5.1.6-1ubuntu2.4_i386.deb) ...
Unpacking replacement php5-mysql ...
Setting up php5-mysql (5.1.6-1ubuntu2.4) ...

```

```

# dpkg -i php5-mysqli_5.1.6-1ubuntu2.4_i386.deb
(Reading database ... 45397 files and directories currently installed.)
Preparing to replace php5-mysqli 5.1.6-1ubuntu2.4 (using php5-mysqli_5.1.6-1ubuntu2.4_i386.deb) ...
Unpacking replacement php5-mysqli ...
Setting up php5-mysqli (5.1.6-1ubuntu2.4) ...

```

Then I restarted Apache:

```

# /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                                                                                                                                             [ ok ]

```

My next test was to see if it worked.  Below is my code (but used valid login and db info on my server):

```

<html>
<body>
<?php
$con = mssql_connect ("10.0.0.86", "sa", "[password]");
mssql_select_db ("mydb", $con);
$sql= "SELECT * FROM mytable";
$rs= mssql_query ($sql, $con);
echo "The field number one is: ";
echo mssql_result ($rs, 0, 0);
mssql_close ($con);
?>
</body>
</html>

```

And I'm greeted with this:

```

Fatal error: Call to undefined function mssql_connect() in /home/webuser/public_html/test.php on line 4

```

Did I install everything correctly or did I miss something?  

Thanks for any suggestions or ideas on this.  I really need to get php to connect to MS SQL, and I still scratch my head wondering why php doesn't come with this feature outta the box.  

Thanks again --

Sam

---

### Post by cytherea on 2007-05-07
You have installed the MySQL php extension not the MS SQL extension so it is quite obvious that it isn't working.. 

See, the following URL for more information about the MSSQL extension:
[http://us.php.net/manual/nl/ref.mssql.php](http://us.php.net/manual/nl/ref.mssql.php)

---

