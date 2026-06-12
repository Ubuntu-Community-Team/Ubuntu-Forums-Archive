---
title: "Sources.list error"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by xebitx on 2005-04-10
When trying to install w32codecs I get this:

Preconfiguring packages ...
Selecting previously deselected package w32codecs.
(Reading database ... 58206 files and directories currently installed.)
Unpacking w32codecs (from .../w32codecs_1%3a20050216-0.0_i386.deb) ...
Setting up w32codecs (20050216-0.0) ...
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/mai Packages (/var/lib /apt/lists/ftp.nerim.net_debian-marillat_dists_testing_mai_binary-i386_Packages) - stat  (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
martin@ubuntu:~$

Is is the stable source in the sources.list which is not responding?

---

### Post by dusu on 2005-04-10
Hi,
Can you check that in your sources.list file, main has not been replaced by mai ? (It seems so from your post). 
If not, could you post your sources.list file ?

---

### Post by xebitx on 2005-04-10
[QUOTE=dusu]Hi,
Can you check that in your sources.list file, main has not been replaced by mai ? (It seems so from your post). 
If not, could you post your sources.list file ?[/QUOTE]
 You are right ...I used ubuntuguide.org to edit my sources.list and it seems that main is mispelled...

Thx for the heads up :)

---

