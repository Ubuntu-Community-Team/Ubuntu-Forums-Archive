---
title: "Mailwasher"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by kjaada on 2006-10-18
When installing Mailwasher using Gdebi package installer I get this message.
rror:Dependency is not satisfiable:libqt3c102-mt but the package is installed.
What am I doing wrong ???

---

### Post by crazedgremlin on 2006-10-18
sounds like you're installing a kde app....
I thought that mailwasher was a windows application for anti-spam..... I'm confused :-k 

Thunderbird has some pretty sweet spam-blocking if you wanna do that....

otherwise.. I dunno...

---

### Post by kjaada on 2006-10-18
Mailwasher is a neat app which allows one to see the guts of yr mail before it is downloaded on to yr puter.I know there are other apps available now but
I paid for MW years ago and have used it ever since on windows and Xandros.
and I am comfortable with it.I feel naked without it.
Now to my problem.How do I get around it ? I would like to be running KDE as my desktop but have not worked that out either.

---

### Post by gaet on 2006-10-30
> **kjaada said:**
> When installing Mailwasher using Gdebi package installer I get this message.
rror:Dependency is not satisfiable:libqt3c102-mt but the package is installed.
What am I doing wrong ???

I tried to install wailwasher too and I have a similar message, if I try to install libqt3c102-mt I get the error message :
conflicts with the installed package libqt3-mt

What can we do?:confused:

---

### Post by gaet on 2006-11-01
Hi,
I've solved the problem.:D 
libqt3c102-mt is in conflict with libqt3-mt so you have to force Synaptic to use libqt3-mt.
I put the walwasher package in a new directory (deb_pack) and did in this way:

1.~$ cd /home/gaetano/deb_pack
2.~/deb_pack$ mkdir mailwasher.tem
3.~/deb_pack$ dpkg-deb --extract  mailwasher_1.1.2_i386_ kubuntu.deb mailwasher.tem
4.~/deb_pack$ dpkg-deb --control mailwasher_1.1.2_i386_kubuntu.deb mailwasher.tem/DEBIAN
5.with a tex editor open control and add the red part:
Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:4.0-0pre6ubuntu4), libqt3c102-mt (>= 3:3.3.3) | libqt3-mt, libssl0.9.7, libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), zlib1g (>= 1:1.2.1)
6.save and close
7.~/deb_pack$ dpkg –build mailwasher.tem 
8.~/deb_pack$ sudo dpkg-scanpackages./dev/null|gzip -9c> packages.gz
9.open Synaptic and install.

  I hope this can help.
  bye

---

