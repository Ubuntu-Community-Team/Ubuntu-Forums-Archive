---
title: "Ubuntu 10. LAMP---PHP file not executed and offered as a download"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by ivikas on 2011-05-11
Hi,

PHP file is not being executed,it is offered as a download.I installed LAMP as

apt-get install apache2
apt-get install php5
apt-get install mysql-server

I have tried everything like
sudo a2enmod php5
Module php5 already enabled

even re-installing libapache2-mod-php5

sudo apt-get purge libapache2-mod-php5

sudo apt-get install libapache2-mod-php5

I am using public_html directory and it is working fine.MySQL is working perfect and i can access it from the Terminal.

Note:
My computer Hard disk is faulty and i had sent it for a repair.I am using Ubuntu 10.10 as Live CD and installing lamp on it and intent to save the source php files on an external hard-disk.

I have tried the ApachePHPMySQL ubuntu documentation and whole lot of online resource.Nothing works.Any Idea will be appreciated.

Thanks in Advance

---

### Post by milindras on 2011-05-25
Hi,
I have the same issue. I installed Virtualmin on a ubuntu server 10 LTS.
When I execute phpinfo.php file it gives me
[B]
Forbidden[/B]

 *You don't have permission to access /phpinfo.php on this server.*
 
I put a HTML file & thats working fine.

I can see the php5 mod is already enabled on my server.

So where is problem?

Many Thanks

---

### Post by milindras on 2011-05-26
Looks this forum is dead????

---

