---
title: "LAMP Issues Persist..."
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by throese on 2010-08-25
Okay, I've tried everything.

Ubuntu Software Center
Synaptic Package Manager
Terminal by installing everything individually
Terminal by using the "sudo tasksel lamp-server" (did that just now)

But even with all of that I DON'T know how to configure the MySQL and PHPMyAdmin stuff.

Does anyone have any idea as to what to do or how I can fix my problems? I can't log into PHPMyAdmin, and idk what to do about MySQL at all.

I'm teaching myself web development, I know plenty about HTML (certified), XHTML, CSS, and a little bit of JavaScript. Working on PHP and MySQL, but I can't do that without the proper tools and if said tools don't work. I can get it all to work on my Windows 7 partition just fine, but here's the thing, I want to COMPLETELY transition over to Ubuntu and obliterate Windows 7 from my hard drive entirely. Will someone please help me so I don't have to deal with Windows anymore, please?

I absolutely love Ubuntu and everything it stands for. I want to be able to help the community and fix bugs etc. etc., but I need more experience. I hope that after a few more months I'll be able to help others.

Thank you to everyone that helps me! =D

---

### Post by theDaveTheRave on 2010-08-25
throese,

first off lets see if there is a mysql server running on your system. 

```

ps aux | grep mysql

```

with luck you'll have a report of the process that is running.

if not follow [this link]("http://dev.mysql.com/doc/refman/5.0/en/installing.html") to the installation pages of the manual.

I used this when I have installed MySQL on various systems.

Also you need to have the correct modules turned on on the Apache web server for the php-mysql communication to work.

But we should get to that after you have success on the mysql side.

Also, if mysql isn't running, to check to  confirm your version
```

mysql --version

```
and then if still nothing, try to start the process

```

sudo /etc/init.d/mysql start

```

although on some systems you need

```

sudo /etc/rc.d/init.d/mysql start

```

If either one of these fails to work (no such file / directory errors), you may need to change the location of the target?

I am assuming that the 'rc.d' is a determiner for the run level that the service is run as.

I don't believe that ubuntu has an rc.d directory, but this signifies the 'top run level' without which nothing else will work.

I will admit to installing from source so my setup may be a bit 'different' to an install via synaptic or similar.

write back if any of the above has helped, and with any error messages.

David

ps  here is a quick link to the debian page regarding run levels.

[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

If you have the process going with 
```

sudo /etc/init.d/mysql start

```

you will need to add the script into the default run levels (it is run a root).

so if the above has worked the command

```

sudo update rc.d mysql default

```

should put the script to start automatically.

---

### Post by throese on 2010-08-25
I did the ```
ps aux | grep mysql
``` command and I got this:

[http://i33.tinypic.com/zlvgj.png](http://i33.tinypic.com/zlvgj.png)

What does it mean and what steps do I take now?

Thanks, theDaveTheRave

---

### Post by theDaveTheRave on 2010-08-26
> **throese said:**
> I did the ```
ps aux | grep mysql
``` command and I got this:

[http://i33.tinypic.com/zlvgj.png](http://i33.tinypic.com/zlvgj.png)



That result suggests that mysql is running, oddly I would have expected to see 3 lines of info, for clarity here is the result of my output

```

 ps aux|grep mysql
root      2925  0.0  0.0   1876   460 ?        S    11:25   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     2967  0.0  0.5 131748  2832 ?        Sl   11:25   0:08 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3307 --socket=/var/run/mysqld/mysqld.sock
davem    23586  0.0  0.1   3344   796 pts/0    R+   15:41   0:00 grep mysql

```

If you did the command after a re-boot, you will know that the service start running during boot, which is good.

Your next step is to 'secure' your mysql server.

This link is for '[post instalation]("http://dev.mysql.com/doc/refman/5.0/en/unix-post-installation.html")' which will give full details, follow it through step by step. 

Remember to check your version of MySQL, 
```
mysql --version
```as the documentation may be slightly different, the page I linked to has the docs for the other version on the left hand side, select yours and then use the menu on the right to find the page you need (should be section 2.18 or there abouts).

For getting php and perl to work with webpages, you need to have your Apache directives set correctly in the httpd.conf file. That however should be for another thread, have a search around the forums, I'll sure you'll find something. If not start a new thread and I'll help you out on that as well.

For now though lets concentrate on getting your mysql server running, and configured securely etc.

Hope that is good for you.

David

---

### Post by throese on 2010-08-28
Thanks, but I have a new problem: [http://ubuntuforums.org/showthread.php?t=1562575](http://ubuntuforums.org/showthread.php?t=1562575) =(

---

### Post by theDaveTheRave on 2010-08-28
put an answer on your other thread... briefly.

install the ubuntu-desktop (gnome) or another.

search for backup utilities / use a cron job.

make a separate /home partition to retain the info from one install to the next.

David

---

### Post by throese on 2010-08-29
It's alright. Once I get my old desktop back, I'll wipe all Windows stuff from it and install Ubuntu Server Edition onto it and use it as my web server (offline) for local use like anyone (who uses Windows) would do with WAMP, if that makes sense

---

