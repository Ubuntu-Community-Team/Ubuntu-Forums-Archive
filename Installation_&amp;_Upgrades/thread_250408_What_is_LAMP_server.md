---
title: "What is LAMP server"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by Lualah on 2006-09-04
I want to install server on my computer and i see option to install LAMP server. I search what is this but i can not get directly the answer what is this and for what is using for.

Can someone tell me please?

---

### Post by FakeOutdoorsman on 2006-09-04
If you want to install a local development server then try XAMPP.  There are [detailed instructions]("http://www.ubuntuforums.org/showthread.php?t=223410").

XAMPP is great for local development and is easy to install.  If you want a public server, then read [ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP") at the Ubuntu Wiki.

---

### Post by Lualah on 2006-09-04
thx for answer

is it possible to install mysql4.1 and mysql5.0 in the same computer?

---

### Post by pufuwozu on 2006-09-04
LAMP stands for "Linux, Apache, MySQL and PHP". These are the essential applications that a web-server needs.

---

### Post by Lualah on 2006-09-04
I already read this in howto which FakeOutdoorsman give it to me.
Now i would just like to know if is posible to install two mysql servers in one computer?

---

### Post by CameronCalver on 2006-09-04
what exacly is mysql and php?

---

### Post by Lualah on 2006-09-04
```
what exacly is mysql and php?
```

how do you mean that?

mysql is an open-source database where you can store your data informations.

# PHP: Hypertext Preprocessor. A script language and interpreter that is freely available and used primarily on Linux Web servers. PHP is an alternative to Microsoft's Active Server Page (ASP) technology. As with ASP, the PHP script is embedded within a Web page along with its HTML. Before the page is sent to a user that has requested it, the Web server calls PHP to interpret and perform the operations called for in the PHP script.



I am searching in ubuntu forum but can not fin if is possible to have 2 mysql server s in one comp-

---

### Post by cantormath on 2006-09-04
> **Lualah said:**
> I want to install server on my computer and i see option to install LAMP server. I search what is this but i can not get directly the answer what is this and for what is using for.

Can someone tell me please?

[This is an awesome picture by picture howto from install to server.]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06")

Lamp=linux apache mysql php

---

### Post by cantormath on 2006-09-04
> **CameronCalver said:**
> what exacly is mysql and php?

Lets say you what to have a website that acts as a forum, like ubuntuforums.org.
**_mysql_**
all the users passwords etc can be help in a database of info. Mysql is the database server you would use to run this site, you can have several different db's or just one.

**_php_**
So say you make this forum website.  And it has a search engine, well people could search anything.  And say you wanted it so when some search something, it was completely tailored to whatever was searched, well, if you were using html pages, you would have write every possible search.....not likely.
So, you write a script, in php, that will take whatever is search, match it to your database and printout the appropriate results...or closest to.

---

### Post by FakeOutdoorsman on 2006-09-04
Yes, you can install both mysql 4 and mysql 5 onto the same computer.  There are instructions on the MySQL 5.1 Reference Manual - [Running Multiple Servers on Unix]("http://dev.mysql.com/doc/refman/5.1/en/multiple-unix-servers.html").

---

