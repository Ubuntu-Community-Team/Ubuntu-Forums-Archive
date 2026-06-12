---
title: "PHP and MySQL - can't call MySQL from PHP"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by BillRebey on 2007-02-18
After a long battle wtih Apache, MySQL, PHP, PHPMyAdmin, and Virtual Hosting, I though everything was good to go.

Somehow I can't call MySQL from PHP.  I've installed Apache2, MySQL 5.0.24a, PHP 5.1.6, and even PHPMyAdmin 2.8.2.  I've installed php5-mysql.

I can run PHP, well enough, but I can't call any mysq_ functions.  I get things like:

   Fatal error: Call to undefined function mysql_connect()

Strangely, though, I can use PHPMyAdmin just fine - I imported my old database, and can select it, browse it, etc.  from within PHPMyAdmin.

What gives?  Isnt PHPMyAdmin using the SAME DANGED set of installed PHP and MySQL components as I am?  

Here's my test code (it's in a file called test.php):

<?php
	echo "-- Connecting something... ";
	mysql_connect("localhost","","") 
                        or die( "Unable to connect to MySQL Server on localhost");
	echo "<br>  --  It worked.  We're Connected! -- <p>";
?>

I don't expect it to connect with no username or password, of cousre, I jsut want the "connect" call to actually get called.

I'm very confused and very frustrated.  

I also have a nagging PHP problem:  I can run scripts just fine explicitly ([www.foo.com/index.php)](www.foo.com/index.php)), but I can't run them implicitly via DirectoryIndex, despite having put index.php in the list.  Anyone got any ideas what that's all about?

I can live with the failed DocumentIndex problem.  THat's trivial.  What I can't live with is MySQL & PHP not working together.

Any ideas at all would be appreciated.  


Thanks!

---

### Post by gvoima on 2007-02-19
hmmm, that's odd. Should work based on the packets you've installed.
You know, you could try to reconfigure the php5-mysql package just in case.
dpkg-reconfigure php5-mysql

The code is ok, it just can't find the function. So I hope reconfiguring helps, or then you could check if you have the mysql module loaded in your php.ini.

---

