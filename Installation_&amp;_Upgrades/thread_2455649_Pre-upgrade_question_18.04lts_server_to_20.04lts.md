---
title: "Pre-upgrade question 18.04lts server to 20.04lts"
date: 2020-12-24
forum: Installation &amp; Upgrades
---

### Post by Frank P on 2020-12-24
I have a Ubuntu server running apache2, php7.2, mysql 5.7
I did a new install of apache2, php, mysql on a test 20.04 LTS  desktop
Apache2 and php7.4 installed and ran okay; problems with mysql. It installed 8.0
Loading the mysqldump from mysql5.7 fails due to the mysql 5.7 database using Isam for some tables.
I can load individual databases but not mysql
Questions:
If I do a 18.04 to 20.04 will it keep the mysql 5.7 or will it install 8.0
If it installs 8.0 can I modify the 5.7 mysql tables to use InnoDB

Would you instead recommend wiping the 18.04 and doing a new install  
Thanks
Frank

---

### Post by #&amp;thj^% on 2020-12-24
It is possible to keep MySQL 5.7: [https://computingforgeeks.com/how-to-install-mysql-on-ubuntu-focal/](https://computingforgeeks.com/how-to-install-mysql-on-ubuntu-focal/)

---

### Post by SeijiSensei on 2020-12-24
If you dump the database with mysqldump, then read the file into an 8.0 instance, would it resolve the problem?  Perhaps you'll need to edit out references to isam in the dump file and replace them with references to innodb.

I never use MySQL unless an application requires it like WordPress. I've used PostgreSQL for decades.

---

### Post by #&amp;thj^% on 2020-12-24
> **SeijiSensei said:**
> 
I never use MySQL unless an application requires it like WordPress. I've used PostgreSQL for decades.

+1;)

---

### Post by Frank P on 2020-12-24
1fallen
I'll check the link.Thanks


> **SeijiSensei said:**
> If you dump the database with mysqldump, then read the file into an 8.0 instance, would it resolve the problem?  Perhaps you'll need to edit out references to isam in the dump file and replace them with references to innodb.

I never use MySQL unless an application requires it like WordPress. I've used PostgreSQL for decades.

If you mean "mysql -u user -p mysql <dumpfile" I tried that and that's  when it errored on the Isam. If I dump/restore individual databases it works ok.
I'm not familiar with PostgresSQL. Does it work better with Ubuntu than mySQL?
Thanks
Frank

---

### Post by SeijiSensei on 2020-12-27
Many of the tables in my MySQL dump files include "ENGINE=MyISAM " in their definitions. Maybe you can specify a different engine instead.

Neither of these database servers "work better" on Ubuntu. They provide the same SQL services though their SQL languages are a bit different.

I began using PostgreSQL because it was entirely free. When I first started building Linux servers for clients, MySQL was encumbered by copyrights and the like. Thus I couldn't sell a server to a client that included MySQL without paying licensing fees. PostgreSQL has been free from the start. In the couple of decades that I used PostgreSQL, it has progressed to being a major competitor in the database market.

One thing I like about PostgreSQL is its collection of command-line tools for simple tasks like adding and deleting users, creating databases, and the like. I always have to look up MySQL's more obscure authentication methods in the documentation.

---

### Post by rsteinmetz70112 on 2020-12-27
One option would be to convert the tables before upgrading. It seems likely that MyISAM will become less and less used as time goes on.
I don't know how much work that would be for you.

---

### Post by Frank P on 2020-12-27
I'll likely try to convert the tables but I want to get some more info first; don't want to mess up the original database

Interesting about PostgresSQL. This is a personal server so I don't have licencing issues but I'll check it out
Thanks
Frank

---

### Post by Frank P on 2020-12-27
> **rsteinmetz70112 said:**
> One option would be to convert the tables before upgrading. It seems likely that MyISAM will become less and less used as time goes on.
I don't know how much work that would be for you.
Yes I read that about Isam. I'm looking inot converting the tables.
Thanks
Frank

---

### Post by #&amp;thj^% on 2020-12-27
Frank P have you seen this yet? [https://mysqlserverteam.com/inplace-upgrade-from-mysql-5-7-to-mysql-8-0/](https://mysqlserverteam.com/inplace-upgrade-from-mysql-5-7-to-mysql-8-0/)

---

### Post by Frank P on 2020-12-27
Never saw it. Just did a quick read; looks promising. Will give it try tomorrow
Thanks !!

---

