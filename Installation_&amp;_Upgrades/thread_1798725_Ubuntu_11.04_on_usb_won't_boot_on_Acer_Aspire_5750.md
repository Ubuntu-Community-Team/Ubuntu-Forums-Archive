---
title: "Ubuntu 11.04 on usb won't boot on Acer Aspire 5750"
date: 2011-07-06
forum: Installation &amp; Upgrades
---

### Post by zbee on 2011-07-06
Boot fail symptoms:
-Stuck at Syslinux first boot line.
-Ctrl+alt+del can't work. need to shut down whole system by holding the power button for 3 secs.

System:
-New Acer Aspire 5750, a supposedly popular model.
-i5 2410M + HM55

Remark:
Can boot from CD Ubunutu 11.04.
But, what is a new laptop when it cant boot Ubuntu from USB??

:(

edit: model number edit

---

### Post by mörgæs on 2011-07-07
Why don't you just install from the CD? 

There are several programs for creating a bootable USB stick. It is best to try both USB Creator and Unetbootin.

---

### Post by zbee on 2011-07-12
> **mörgæs said:**
> Why don't you just install from the CD? 


If a new laptop cannot boot from USB, what the point??
USB boot is basic feature now and most commonly used for ubuntu boot.


> 
There are several programs for creating a bootable USB stick. It is best to try both USB Creator and Unetbootin.Had tried both. Cannot work. :(

Acer refused to provide technical support on this. F%#$%#

Im pretty sure its a bios issue.

---

### Post by dino99 on 2011-07-12
the latest kernel 3.0 rc7 have many fixes around acer issues, you might install it

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc7-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc7-oneiric/)

note: install both headers first, then image.

---

### Post by zbee on 2011-07-17
its probably not ubuntu issue.
since it got stuck at the firstline boot loader screen: Syslinux..

I tried creating a freedos usb boot , cant work too. :confused:

---

### Post by Quackers on 2011-07-17
What bios boot options are there?
Some bioses recognise some flash drives as USB HDD's, try that.

---

