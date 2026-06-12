---
title: "Hash sum mismatch during upgrading"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by techbrainless on 2010-05-11
Hi All, 

I am trying to upgrade from 9.10 to 10.04 (upgrade through alternate cd) but getting error ( hash sum mismatch) for some of the packages , 

how i do fix this issue

---

### Post by techbrainless on 2010-05-11
Hi I have successed to upgrade from 9.10 to 10.04 after executing some commands like 

apt-get update
apt-get upgrade 
apt-get clean
apt-get autoclean


after rebooting the system , and in the login screen , the keyboard and the mouse are not working 

by the way  i have dual boot and the during the selection the keyboard was working.

---

### Post by techbrainless on 2010-05-12
Any reply ....

---

### Post by techbrainless on 2010-05-15
Hi All,

Any one can help me to fix this issue my keyboard and mouse are not working and am not able to login to 10.04 after my upgrade ...............

---

### Post by itsonlybarney on 2010-05-17
Does anyone have any ideas on how to fix this problem?  I have the Alternate CD and getting the Hash Sum errors as well.  Any way to upgrade from the CD?


> **techbrainless said:**
> Hi All, 

I am trying to upgrade from 9.10 to 10.04 (upgrade through alternate cd) but getting error ( hash sum mismatch) for some of the packages , 

how i do fix this issue

---

### Post by techbrainless on 2010-05-17
You can fix the errors of hash sum using the following ( as i did)

1) execute the following commands before upgrading using alternate CD

apt-get update
apt-get upgrade 
apt-get clean
apt-get autoclean

2) upgrade using the alternate CD


by the way  for me i have successed to upgrade but now am not able to login because my laptop keyboard and mouse are not recognized by ubuntu 10.04 ......... [http://ubuntuforums.org/showthread.php?t=1484741](http://ubuntuforums.org/showthread.php?t=1484741)

---

