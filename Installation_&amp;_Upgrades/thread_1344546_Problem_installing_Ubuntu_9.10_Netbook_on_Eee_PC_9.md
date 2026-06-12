---
title: "Problem installing Ubuntu 9.10 Netbook on Eee PC 901"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by Harters on 2009-12-03
I have a Eee PC 901 which has Windows XP running on it. I want to obliterate it and install Ubuntu Netbook on it instead. I have downloaded the Ubunto Netbook 9.10 ISO image and installed it to a 2GB flash drive using Ubuntu's USB Startup Disk Creator (I've also tried NetBootin) - all okay thus far!

I can boot the USB drive on the 901 and then I can select Install Ubuntu. The Ubuntu logo appears and then I get the following error message:-

[I]BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting aufs on /root failed: Invalid argument
aufs mount failed[/I]

Has anyone any ideas as to what's going wrong and how to get around this?

Thanks.

---

### Post by xoman on 2009-12-04
hi, i have similar problem as well, i was about to load the usb stick, and i can see the options to install ubuntu, however, it only loads up the ubuntu logo for about 10secs, then it just went black screen. with no sign of any activity at all. the harddisk light is not flashing. i wonder how i can fix it.

---

### Post by PoopyTheJ on 2009-12-16
Just type exit and hit enter it's a problem with the HDD controller I think taking a long to to wake up, anyways hitting enter then typing exit and then enter again after a second or two will continue the boot process. Let me know if you get a Kernel Panic though, that's what I'm running into currently after getting through the busybox thing...

---

### Post by thompcha on 2011-02-11
I get the same behavior when trying to boot Ubuntu 10.10 Netbook on my Eee 901. First, "aufs mount failed". After exit, I get a bunch of warnings about directories not found. Exit again, and it's kernel panic.

---

