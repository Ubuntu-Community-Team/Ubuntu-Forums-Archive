---
title: "I just upgraded to ubuntu 8.10 and now I can't start apache."
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by tsimpo on 2008-11-03
I just upgraded to ubuntu 8.10 and now I can't start apache.

The following error occurs

[B][I]Starting XAMPP for Linux 1.6.8a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Error 139! Couldn't start Apache!
XAMPP: Starting diagnose...
XAMPP: Sorry, I've no idea what's going wrong.
XAMPP: Please contact our forum [http://www.apachefriends.org/f/](http://www.apachefriends.org/f/)
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.[/I][/B]


Tried to start apache and I got the following error


**Segmentation fault**


any suggestions?

I have already ask at [http://www.apachefriends.org/f/viewtopic.php?t=31825](http://www.apachefriends.org/f/viewtopic.php?t=31825)

---

### Post by hydr0 on 2008-11-04
what about just using apache2.2-common php5-common and mysql-common
and phpmyadmin which is nearly all you may need from xampp, maybe add proftpd or vsftpd to it for ftp support, okay needs some time for proper configuration but does the job.

openssl for https support
lighttpd if you like to play a bit around check out lighttpd which is a smaller, maybe faster replacement for apache 

i found some config tuning for lighttpd on the net at: [https://calomel.org/lighttpd.html](https://calomel.org/lighttpd.html)  just in case...


--if you like to keep your xampp you should post some of the error log messages which normaly can be found under /var/log

else there is no real chance to track down the error


greedies

---

### Post by iponeverything on 2008-11-04
Did you install apache from source originally?

Ether -- rebuild from source 
or
Remove and purge apache (maybe all of lamp) with dpkg and use apt-get to reinstall.

---

### Post by tsimpo on 2008-11-05
Thank you for your response. 

I have installed xampp because in every forum I read, everybody was saying to if you want apache php and mysql in ubuntu the easyest way is xampp. 

and I have installed it since 7.10 that was the first release I used. since then I have upgraded to 8.4 and now to 8.10. 

I now changed the httpd.conf file with the default one and I have started apache but I have lost all my settings.

I'll try to find the differences in two files and I'll add line by line restarting apache, so I'll catch the problem. 

Thank you all for your time and your consultations and I'll inform you for the problem if I could find it.

---

