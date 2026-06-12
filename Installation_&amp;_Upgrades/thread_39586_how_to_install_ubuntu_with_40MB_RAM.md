---
title: "how to install ubuntu with 40MB RAM?"
date: 2005-06-05
forum: Installation &amp; Upgrades
---

### Post by cristianommxp on 2005-06-05
I'm trying to install Ubuntu by LocalNet.

On Server I did:

$ sudo aptitude install apache2
$ cd /var/www
$ sudo mkdir ubuntu
$ sudo mount /dev/hdc /var/www/ubuntu


The PC I'm trying to install Ubuntu is an old Pentium 100 with 40MB RAM (with out CD-ROM) and HD 4GB.

The installation program works fine , but threre is an error when it is downloading the "partman" package:

- The screen to be black
- The instalation stop
- In other terminal (CTRL+ALT+F4) an log error do loop. There's a strange messagem: 
            "kernel - memory out"

So, ..., how to intall Ubuntu in an Pentium100?



10ks 


Cristiano Meira Magalhães

---

### Post by mingus on 2005-06-05
you need a swap partition

---

