---
title: "How to completely reinstall a package (eg mysql)"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by mr.f on 2006-09-15
Hi,

I'm new to Ubuntu and apt-get. I installed mysql earlier today. Unfortunately, while fiddling around I accidentaly deleted /var/lib/mysql. In order to get it back, I've tried to remove and reinstall mysql, but I can't seem to get this directory back.

I tried with apt-get --purge remove mysql-server mysql-client to get rid of everything. Then I've tried both apt-get install, and apt-get --reinstall install (which is supposed to help me if I damage a package, right?), but still no /var/lib/mysql.

Help! How do I get the packages back to the way it was after the first install??

---

### Post by jmwhokie on 2006-09-15
ME TOO. I'm having the SAME problem with apache2!.....:confused:

---

### Post by mr.f on 2006-09-15
Ok, I think I've solved my problem. I found that I could list my mysql packages with:

> dpkg -l mysql* 

which gave the following result (sorry, the install is in swedish, but I hope you'll understand what you need to know anyway):


```
||/ Namn                  Version               Beskrivning
+++-=====================-=====================-==========================================================
un  mysql                 <ingen>               (beskrivning saknas)
un  mysql-base            <ingen>               (beskrivning saknas)
pn  mysql-client          <ingen>               (beskrivning saknas)
un  mysql-client-4.1      <ingen>               (beskrivning saknas)
ii  mysql-client-5.0      5.0.22-0ubuntu6.06.2  mysql database client binaries
ii  mysql-common          5.0.22-0ubuntu6.06.2  mysql database common files (e.g. /etc/mysql/my.cnf)
un  mysql-common-4.1      <ingen>               (beskrivning saknas)
un  mysql-dev             <ingen>               (beskrivning saknas)
un  mysql-devel           <ingen>               (beskrivning saknas)
un  mysql-gpl-client      <ingen>               (beskrivning saknas)
un  mysql-gpl-dev         <ingen>               (beskrivning saknas)
pn  mysql-server          <ingen>               (beskrivning saknas)
un  mysql-server-4.1      <ingen>               (beskrivning saknas)
ii  mysql-server-5.0      5.0.22-0ubuntu6.06.2  mysql database server binaries

```

So, I did "apt-get --purge remove mysql-server-5.0" instead of just mysql-server, and then "apt-get --reinstall install mysql-server-5.0". Voila, the package is reinitialized and my "/var/lib/mysql" directory is back!

Maybe something similar will work for apache2 as well? I have not yet installed apache (though I'll get to it soon) so I don't know which packages are involved.

One thing is strange though. After the reinstall, when issuing the same command, ie "dpkg -l mysql*" the result is:

[INDENT]un  mysql                 <ingen>               (beskrivning saknas)[/INDENT]

That is, dpkg does not seem to find the mysql packages, even though they are installed. However, if I instead write "dpkg -l *server* the following line appears (among other server packages):

[INDENT]ii  mysql-server-5.0      5.0.22-0ubuntu6.06.2  mysql database server binaries[/INDENT]

Anyone has an idea why this happens??

---

