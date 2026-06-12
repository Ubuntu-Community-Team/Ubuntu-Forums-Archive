---
title: "Ubuntu Vps Urgent, I need anyone who install nginx"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by santimonevito on 2012-09-17
Hi to all!

i had a vps server unmanaged, buyed for an amateur ads site, now i need to install and setup nginx to save memory (in this moment im using apache but sistem crach out of memory!)

anyone can install it? i can send in pm password and user...

i hope someone can help me...

best

---

### Post by Lars Noodén on 2012-09-17
You'll find it in the [repository](https://help.ubuntu.com/community/Repositories/Ubuntu) with all the other packages for Ubuntu.

```

sudo apt-get update
sudo apt-get remove apache2
sudo apt-get install nginx
sudo apt-get autoremove

```

---

### Post by santimonevito on 2012-09-17
already done!

im not an expert...so i cant configure webserver...for that im searching a persone who i can send user and password to do it in 5 minutes for me!

can you?

---

### Post by santimonevito on 2012-09-17
ps

vps is 

System hostname	[http://www.vendiamolosubito.it](http://www.vendiamolosubito.it) (5.9.252.143)
Operating system	Ubuntu Linux 10.04.3
Webmin version	1.590
Time on system	Mon Sep 17 10:30:17 2012
Kernel and CPU	Linux 2.6.32-33-server on x86_64
Processor information	Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz, 4 cores
System uptime	0 hours, 28 minutes
Running processes	107
CPU load averages	0.23 (1 min) 0.14 (5 mins) 0.19 (15 mins)
CPU usage	0% user, 1% kernel, 1% IO, 98% idle
Real memory	995.06 MB total, 435.37 MB used

Virtual memory	1023.99 MB total, 27.41 MB used

Local disk space	59.06 GB total, 5.62 GB used

Package updates	All installed packages are up to date

---

### Post by SlugSlug on 2012-09-17
whats the actual error your getting? a gig of ram should be enough for a single webpage

---

### Post by santimonevito on 2012-09-17
all problem! infact i removed!

need a full installation

---

