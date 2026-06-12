---
title: "since upgrade to 12.04 &gt; mysql insert statements very slow"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by loikiloik on 2012-05-08
Hello,

Since the update of ubuntu when I execute a SQL file (with a lot of insert statements), it takes very very long time (30 minutes !!!). Before the update, it took maximum one minute. Any idea ?

Thanks !

P.S. I use the command line :
mysql  --host=localhost --port=3306 --default-character-set=utf8 --comments  MY_DB < file.sql

---

### Post by eslin on 2012-05-11
Im also experiencing performance problems in ubuntu 12.04 with mysql 5.5.

I have no statistics of the time an import took before upgrading but now it takes foreever in my application.

this is a completley worhtless addon to this thread but I am hoping that someone that knows something about the mysql package and its implementation will pick this up and try something out.

---

### Post by aleq on 2012-05-18
It's probably not a right place to report this, but I also observe really slow inserts in mysql 5.5.22 under ubuntu 12.04 compared to ubuntu 11.10. Dropping a database is extremely slow as well.

Have anyone found a fix?

---

### Post by sloggerkhan on 2012-05-18
So I'm using MySQL also, and it's definately slower, but what I'm wondering is if it might be traceable to what seem like disk access/write issues to me?

I have a very basic bug filed, but if you guys could isolate whether you have a disk locking problem vs a MySQL issue maybe it would help clarify whether my bug report is on the right track.

[https://bugs.launchpad.net/ubuntu/+bug/999386](https://bugs.launchpad.net/ubuntu/+bug/999386)

---

### Post by aleq on 2012-05-18
Guys, I've found that it is a well-known issue with ext4 file system. Have a look at [http://ubuntuforums.org/showthread.php?t=1313834](http://ubuntuforums.org/showthread.php?t=1313834) and [http://blog.smartlogicsolutions.com/2009/06/04/mount-options-to-improve-ext4-file-system-performance/](http://blog.smartlogicsolutions.com/2009/06/04/mount-options-to-improve-ext4-file-system-performance/)

---

### Post by aleq on 2012-05-18
But I still don't understand the following. I try to import 2Gb of data in CSV format into my MySQL database. During the import iostat shows 30MB/s write performance. Thus, the data should be imported in ~80s. Instead, it took 35 min to import 500MB.

So what do these 30MB/s writes stay for if not just writing parsed data?

---

### Post by sloggerkhan on 2012-05-18
'Well known' doesn't make a non-issue. And the performance reported by some of you is not just slow, it's crippling.

---

### Post by serge_o on 2012-06-05
I can confirm the problem.

my config:

hardware:
Intel Hexacore server, 64GB of RAM,   3* 3TB SATA drives (not SAS), 2 of them in software RAID-1, the third is a separate backup drive.

software: a fresh install of 12.04 and then apt-get install php5 mysql-server apache2
so basicall this is a LAMP server with absolutely no config changes - everything "factory settings"

mysql insert statements have become 20-40 times slower than they should be.


I have multiple lamp installs on 8.04, 9.04, 10.04, 10.10, 11.04, 11.10 - never had such a problem with "factory settings" - i.e. never experienced that a fresh mysql server from apt-get shows any problems.


I am 100% sure that this is some problem concerning 12.04, maybe kernel, maybe mysql 5.5, maybe something else.

was anybody able to fix that or confirm that the exact same install works somewhere else

---

