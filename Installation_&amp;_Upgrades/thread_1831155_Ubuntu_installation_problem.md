---
title: "Ubuntu installation problem"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by aditya10 on 2011-08-23
Hey guys, 
I'm running into a lot of problems while installing Ubuntu. This is my story-
I originally had Maverick installed on my laptop(HP dv4 Core2duo, dual-boot with 32-bit Ubuntu 10.10 and Vista), but once while I was working, my laptop experienced a strong jerk(strong enough to momentarily move the hardware inside), and the screen went blank. I rebooted and then persistently got the same message: **Kernel panic: attempted to kill init.** I then uninstalled ubuntu(used EasyBCD on Vista to restore vista bootloader entry to mbr)

Since then I have tried to install both maverick and natty with similar error messages during installation(somewhere in between 'Configuring hardware'):
**E:Sub-process /usr/bin/dpkg returned an error code(1)**
and then there was an explanatory msg saying this could be due to old installer image, these packages could not be installed, more info can be found in some log, this could also be coz of bad CD/DVD. Or if it installed smoothly, gave a kernel panic error during boot. I tried everything...downloaded the image again(even checked the md5), used a LiveUSB instead of CD, but with same error messages. Its like after the accident, my laptop is refusing to install ubuntu again.

Also a weird thing(i don't know if its normal or not or at all related to above problem) but while installing, ubuntu shows already present windows partitions sda1, sda3, sda4, then starts with sda5 for linux partitions...i don't see sda2 anywhere.

I feel there might be some problem with the hardware...but Vista seems to be working perfectly...
Advice really appreciated,
Thanks you.

---

### Post by dino99 on 2011-08-23
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by aditya10 on 2011-08-23
Hey dino99,
How to install is not a problem(although i don't use gparted or partedmagic)
This is what I do: I have resized windows partition, and now I have 30GB of free disk space. I boot into the ubuntu CD, and make /, swap, /home partitions there and install...
Its the error messages and the fact that I cannot boot into ubuntu that's bothering me.
Thanks for the reply anyway...

---

