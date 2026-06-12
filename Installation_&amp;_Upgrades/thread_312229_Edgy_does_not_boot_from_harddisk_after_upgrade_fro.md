---
title: "Edgy does not boot from harddisk after upgrade from Dapper"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by joachimS on 2006-12-04
Ubuntu Linux Version: 6.10

My Computer: Fuijits Notebook Amillo M 7400

On this notebook I have Ubuntu running for over a year. I upgrade to 6.06 in spring an now wanted to upgrade to 6.10. I used the DVD, which was included in the german computer magazin CT.

I started 
sudo sh /media/cdrom/cdromupgrade

that started and told me, that it would take an hour to upgrade. Since it was late at night, I went to bed. In the next morning the laptop had booted from DVD. I tried to reboot from hd, but that fails, even for all older kernels. 

If I boot in recovery mode, the last lines shown are:
Begin: Runnning /scripts/local-bottom ...
Done.
Begin: Runnning /scripts/init-bottom ...
[17179578.016000] kjournald starting. commit interval 5 seconds.
Done.

I can boot from CDRom or DVD.


What is the next step after running /scripts/init-bottom

---

### Post by gdselzer on 2006-12-30
Bump!

Does anyone have any help for joachimS (and me)?  I ran into almost the exact same issue.  I was upgrading from Dapper to Edgy via the Update Manager and my system hung.  Now my boot process stops in the same place.

I tried the method in this thread [http://www.ubuntuforums.org/showthread.php?t=287756]("http://www.ubuntuforums.org/showthread.php?t=287756") but when I typed 

dpkg --configure -a

nothing happened.

---

### Post by ankitsahai on 2008-04-23
hi
I am facing the same problem. However, when I append "init=/bin/bash" as suggested, I get a prompt (root@(none):/#)but after that i am able to type but on giving the command mount /dev/<root partition> / -o remount,rw , nothing happens....

---

