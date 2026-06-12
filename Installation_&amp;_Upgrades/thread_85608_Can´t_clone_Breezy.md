---
title: "Can´t clone Breezy"
date: 2005-11-03
forum: Installation &amp; Upgrades
---

### Post by radza on 2005-11-03
We have got 18 similar comuters.
Can´t clone Ubuntu Breezy with the programme Norton Ghost
Starting the clone I get the message:

mount: Mounting /dev/hda1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or dir.
mount: Mounting /dev on /root/dev failed: No such file or dir.
Target filesystem dosen´t have /sbin/init
/bin/sh: can´t access tty; job control turned off


Previous version (Ubuntu 5.04) everything worked OK?!

---

### Post by frodon on 2005-11-03
Which version of norton ghost do you use ? 
it works really well for me, i never add any problems with the latest version.

---

### Post by radza on 2005-11-03
I used Symantec Gost 7.0 enterprise.

I clone over LAN for a lot of computers at a time.

---

### Post by frodon on 2005-11-03
See this link : [http://service1.symantec.com/SUPPORT/ghost.nsf/docid/1999021909463125?Open&src=&docid=2000033111503625&nsf=ghost.nsf&view=docid&dtype=&prod=&ver=&osv=&osv_lvl=](http://service1.symantec.com/SUPPORT/ghost.nsf/docid/1999021909463125?Open&src=&docid=2000033111503625&nsf=ghost.nsf&view=docid&dtype=&prod=&ver=&osv=&osv_lvl=)
it seems that your version doen't support ext3 File System, which is the ubuntu partition File System.

---

### Post by WOteB on 2005-11-03
Nearly correct, ext3 + / (Root partition). I'm using Paragon backup, that's wordking correct with images of partitions or complete drives. It's a fully menudriven Linux or DOS environment.

---

