---
title: "Preventing &quot;VGA not support&quot; after upgrade"
date: 2014-03-24
forum: Installation &amp; Upgrades
---

### Post by matt81 on 2014-03-24
Hi all

I've been running ubuntu 10.04 for a long time, but when I tried upgrading to 12.04 I kept on getting VGA not support error.

I reinstalled 10.04 and that is what I am using currently. How can I avoid or prevent VGA not support error if i try upgrading again?
I have a 32" lcd monitor with nVidia GeForce 6100 & nForce 405.

Many thanks

NOTE Trying to avoid / prevent it when i upgrade rather than have to solve it?

---

### Post by fantab on 2014-03-24
How exactly were you trying to upgrade, from 'update manager'?
Try installing directly from DVD/USB, a fresh clean install of 12.04.

Post some info about your computer, how old is it?

---

### Post by matt81 on 2014-03-24
Yeah, upgrading from update manager, computer is about 6 years old, 2* AMD Athlon 64 dual core processors, kernel version 2.6.32-57-generic.

Is there any way I could upgrade with update manager without having to use DVD or USB?

---

### Post by matt81 on 2014-03-24
Would changing the resolution from "auto" to an actual resolution on my nVidia settings applet solve the problem?

---

### Post by fantab on 2014-03-24
> **matt81 said:**
> Yeah, upgrading from update manager, computer is about 6 years old, 2* AMD Athlon 64 dual core processors, kernel version 2.6.32-57-generic.

Is there any way I could upgrade with update manager without having to use DVD or USB?

> **matt81 said:**
> Would changing the resolution from "auto" to an actual resolution on my nVidia settings applet solve the problem?

The problem is 10.04 has reached its 'end of life', which means no more updates, and the 10.04 repos don't really exist.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

If you encounter Graphics related issue like you are facing, then use '[NOMODESET]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997")' option until you install 12.04, then you can choose the appropriate Graphics driver from System Settings -> Additional Drivers.

IMHO fresh and clean install of 12.04 is recommended.
BACKUP ALL YOUR IMPORTANT DATA...

If you have 2Gb or more RAM then install Ubuntu, but if less then consider Xubuntu or Lubuntu which require far less system resources than Ubuntu.

---

### Post by matt81 on 2014-03-24
10.04 reaching its end of life is the reason why I'm upgrading. I have 2gb RAM so 12.04 shouldn't be a problem. But how do I use 'NOMODESET' option? 

I know how to select additional drivers, the problem is getting the system to load up in the first place without an error message.

---

### Post by fantab on 2014-03-24
Check the links I have shared in my previous post....

---

### Post by matt81 on 2014-03-24
thanks very much for your help, i think i've done it. i'll try upgrading now and if it doesn't work i'll put a clean new installation on.

---

