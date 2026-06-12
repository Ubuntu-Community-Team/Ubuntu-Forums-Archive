---
title: "Install Dual Boot Hardy gives Grub Error"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by jcscowtown on 2008-04-27
I have Windows XP installed on my notebook. I have only one Hard Drive. I installed Ubuntu 8.04 to dual boot.  When i turn on the computer I get a grub error 18.  I have read on the forums here and done what people suggest which is:

sudo grub
find /boot/grub/stage1
(hd0,1)
root (hd0,1)
setup (hd0)

it returns several lines saying everything succeeded.  So I reboot and the same thing happens - I get Grub Error 18 and cannot go into Ubuntu or Windows.  I have also run the above with "setup (hd1) and it did not work either.  I have gone into the partition manager and windows partition is sda1 and the Ubuntu partition is sda2.  I would sure appreciate some help here.  I am pretty new to Linux and have exhausted what I know to do.
Thank You.

---

### Post by Pumalite on 2008-04-27
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by mnord00 on 2008-04-27
> **jcscowtown said:**
> I have Windows XP installed on my notebook. I have only one Hard Drive. I installed Ubuntu 8.04 to dual boot.  When i turn on the computer I get a grub error 18.  I have read on the forums here and done what people suggest which is:

sudo grub
find /boot/grub/stage1
(hd0,1)
root (hd0,1)
setup (hd0)

it returns several lines saying everything succeeded.  So I reboot and the same thing happens - I get Grub Error 18 and cannot go into Ubuntu or Windows.  I have also run the above with "setup (hd1) and it did not work either.  I have gone into the partition manager and windows partition is sda1 and the Ubuntu partition is sda2.  I would sure appreciate some help here.  I am pretty new to Linux and have exhausted what I know to do.
Thank You.
I have a similar problem. After a dual boot install with Kubuntu 8.04 KDE 3.9 on an ECS GF7050VT-M motherboard. It comes up with a grub error 17. I used a Grub boot disk and typed in the following at the grub>
rootnoverify (hd0,0)
makeactive
chainloader +1
boot

Windows XP started right up with no data lost. I reinstalled Kubuntu and watched the screen more carefully this time. The install failed about 1 or 2 minutes into formatting and setting up the disks. The error scrolled by fast but said something like CPU temp too high 127c shutting down. I rebooted into my bios to check the temp and it was at 62c. I bumped up the shut down temp but came up with the same error.

---

