---
title: "Ubuntu 10.04 is NOT Bootable OS ?????"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by Alexdelpiero1974 on 2010-05-10
Hello All ,

I tired so many times to install Ubuntu 10.04 on my harddisk 80GB and i also tried to install it in USB drive 8GB , but the problem is not booting @ all from either of those 

i had PC work with XP , then i reboot , and start my pc using Ubuntu Bootable CD
and i go directly to install Ubuntu , i tried first on my harddisk , everything gone good 
and 100 % complete Installation without any errors @ all 
but after pc reboots it login to XP as normal but 
there is no any multiple screen to choose boot 

i also do this again but in my USB drive 8 GB and it's the same login to XP
without any multiple screen to choose boot

What's Going on ??????????????????

---

### Post by darkod on 2010-05-10
Do you have only one hdd in the PC? If you have more, the grub bootloader might go to the other one and you are still booting from the first disk directly XP. Windows can't see linux and will never offer a menu for dual boot.

Grub is the one doing that, but it depends on which disk it is installed and which disk you are booting from.

Also, disconnect any external usb hdds during install if you don't need them. Eliminates confusion.

---

### Post by kansasnoob on 2010-05-10
Please post the output of the Boot Info Script using the Live CD as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

