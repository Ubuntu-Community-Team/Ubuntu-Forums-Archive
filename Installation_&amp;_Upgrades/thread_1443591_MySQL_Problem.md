---
title: "MySQL Problem"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by BalticSailor on 2010-03-31
Hi all,

I am new to Ubuntu and have set up a server from scratch

> Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/LinuxThen I installed some packages, PHP, perl and MySQL.

I tried to install the vTiger CRM and it told me that it can not do the installation because MySQL is not supporting UTF-8. I searched around a lot of forums but I have not found a solution.
I have used a lot of different LAMP systems before (but this is the first with Ubuntu) and all system I set up with a MySQL 5.1 have UTF-8 as default charset.

So my question: What do I have to do to get UTF-8 support into my MySQL?
I found some posts saying I have to change the my.cnf and add defualt_character_set = utf8 but when I do that I get

> mysql: Character set 'utf-8' is not a compiled character set and is not specified in the '/usr/share/mysql/charsets/Index.xml' file
Charset is not foundSo I looked around if there is a package I might need to install but everything I read looks to me that I have to re-compile MySQL. Is that true?

Thanks a lot for any help.

Thomas

---

