---
title: "Laptop restarts from Ubuntu install screen"
date: 2015-12-29
forum: Installation &amp; Upgrades
---

### Post by allmin2 on 2015-12-29
I am trying to install 64bit Ubuntu 14.04.3 on my windows 7(32bit) laptop to make it dual boot. I am able to boot using a Live USB. but when I choose any option such as try ubuntu or install ubuntu or check disk etc, My laptop shows a blank screen for 1 second and restarts immediately.

I tried 
1)creating live USB using unetbootin, universal usb installer, win32diskimager. still, the problem persists.
2)tried using kernel options such as nomodeset, acpi=off, nolapic. still, the problem persists. 
3)tried installing earlier versions of ubuntu such as 12.04.5 and 10.04.4, still, the problem persists.
4)tried to install 32bit ubuntu, still, the problem persists.
5)tried installing other linux distros, still, the problem persists.
7)searched bios for any options such as UEFI,secureboot,fastboot, found none.
6)tried changing my usb drive, still, the problem persists.

Kindly help.

I am using a Fujitsu Lifebook s710 6GB RAM, 36GB unallocated space in Hard Disk, intel core i5 processor. I do not have a CD-DVD drive. 
Thank you in Advance.

---

### Post by Geoffrey_Arndt on 2015-12-29
1.   What graphics system does the laptop have?
2.   Are you using standard MBR (master boot record) DOS partitioning . . . or something else like Windows Dynamic Disk?   If the latter, that's a problem that could be causing usb boot operation failures.

---

### Post by allmin2 on 2015-12-29
1. My laptop has no graphics card. Just the intel(R) HD graphics
2. I partitioned my hard disk using the windows disk management tool and it shows that the type of partition as basic.

---

### Post by Geoffrey_Arndt on 2015-12-30
Well, that's good news.    So, just to be clear, UEFI is not a boot or bios option, it is a whole disk & mobo mgmt system that essentially replaces bios.    I was going to say to check the ISO integrity but with all the steps and distros you've already tried, that doesn't appear to be the issue.   So, one "out of the box" (so to speak) options is to install via a DVD optical drive.   If you have USB ports, you can connect an external cd/dvd drive and the odds of it booting are much better than USB sticks on a few rare machines like yours.    Amazon sells a basic optical drive for under 20. usd if I recall right.   Works well with Ubuntu also.    But, before deciding on that, perhaps other forum members will offer more advice.

By the way, have you tried the Pendrive Linux website for creating Live USB stick . . might be worth a shot.

---

### Post by allmin2 on 2015-12-30
I have tried the universal USB installer from the pendrivelinux.com but still same problem. Let me see if i can install through DVD.

---

### Post by allmin2 on 2016-11-24
Thank you all for the help. I fixed it at last. Looks like one of the RAM in my Laptop is bad. It is a 4GB DDR3 module. I just removed it and ran using the 2GB RAM that I had in spare. Now the setup is done. I am happy.

---

