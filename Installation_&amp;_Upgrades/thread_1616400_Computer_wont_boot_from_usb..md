---
title: "Computer wont boot from usb."
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by plusle on 2010-11-08
Hey, I'm currently running ubuntu 9.04 32 bits which I installed with my usb stick. Now the problem is when I try to boot Windows 7 from usb drive it won't boot. Have checked bios that removeable dev is prio 1 and I even tried to delete any other option then boot from usb.

Tried the usb stick on my HP desktop and it booted from the usb stick without any problems. I have an ATI motherboard and i'm quite new in linux so can't realy provide any information about the motherboard but I'll show a pic.

Don't know what i'm doing wrong since I can boot another computer with the usb stick.



Motherboard: [http://data.fuskbugg.se/dipdip/motherboard.png](http://data.fuskbugg.se/dipdip/motherboard.png)

---

### Post by efflandt on 2010-11-08
I don't quite understand what you are trying to do.  Linux on USB should be able to boot itself from various computers as long as that computer is compatible with its default drivers or installed proprietary drivers, proper syslinux (for bootable iso) or grub (regular install) is on the mbr of the USB drive, and UUID's are used in /etc/fstab.

If you are trying to boot Win7 on your internal drive from USB with grub on it, you would first need to do sudo update-grub on that computer, because Win7 might boot from a different partition on different computers.

If you are trying to boot Win7 installed on a USB drive, that might only have drivers enabled for the particular computer it was installed from, and may not be able to boot from a different computer.  So don't expect Win7 installed on USB to be able to boot on different computers.  Even the wrong video resolution or refresh rate (or driver) could leave you with a dark screen, if it gets that far.  And if it is OEM Windows for a particular manufacturer, it may not boot from another brand of computer because it may check the manufacturer ID.

---

### Post by plusle on 2010-11-08
Thanks for your answer, i'm trying to install Win7 on my desktop which runs ubuntu 9.04. An downloaded version of windows with an iso and created in unetbootin. It worked smoothly the last time i tried to install Win7 for roughly 7 - 8 months ago. So my problem is that the computer ain't accepting my usb stick as an driveable media for installing. But it works on my other computer.

My english is quite bad thats why you might not understand what i want to say. But I guess that you understands now. Any idea of what to do?

---

### Post by thegod_slayer on 2010-11-08
> **plusle said:**
>  i'm trying to install Win7 on my desktop which runs ubuntu 9.04. 

i hope by this you mean you want a computer which will have both win7 and ubuntu.

> An downloaded version of windows with an iso and created in unetbootin. It worked smoothly the last time i tried to install Win7 for roughly 7 - 8 months ago. So my problem is that the computer ain't accepting my usb stick as an driveable media for installing. But it works on my other computer.
if this is the problem, the boot loader that win has dosen't recognise grub (linux boot loader). but grub can recognise win, so it's advicable to install win first then any linux distro.

but it's not mandatory. you can get some help on the following website.....

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by plusle on 2010-11-08
Hey i read everything about dual boot. But should i remove this ubuntu dist and then install win7 via the usb stick? And how do I do such thing?

---

### Post by thegod_slayer on 2010-11-08
try formatting your usb stick using ubuntu.
then try installing win 7 with unetbootin

---

### Post by plusle on 2010-11-08
> **thegod_slayer said:**
> try formatting your usb stick using ubuntu.
then try installing win 7 with unetbootin

Thats exactly what i've tried to done so far. The usb stick easily boots on one of my other windows machines but not on this one with linux.

---

### Post by plusle on 2010-11-08
Just want an quick answer here. If i completley swipe my computer of everything on the hdds and yep EVERYTHING with random nukeing program. Then tries with the usb, will it work then?

---

