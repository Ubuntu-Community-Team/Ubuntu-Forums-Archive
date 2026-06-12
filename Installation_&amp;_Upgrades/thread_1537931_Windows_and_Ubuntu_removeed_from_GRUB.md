---
title: "Windows and Ubuntu removeed from GRUB"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by rDwyP44y on 2010-07-24
Hey!
I am in need of some serious help here with my netbook!
Well i had Ubuntu 9.10 netbook remix installed... along side Win XP

I installed this via Wubi like 7 months ago...

I accidentally did "Sudo apt-get update" in terminal... and now when i boot my netbook, I cant get any other options than
**MEMTEST  and MEMTEST (with serial)**

But what I want to do now is basically get to my WIN XP recovery partition that came with the netbook, and reinstall XP (which should also remove all the partitions i made)

I want to make my netbook as if i just got it from Acer wint Win XP

and then  i will get back to installing ubuntu

**[SIZE="4"][COLOR="Green"]How do i fix my GRUB  /bootloader so I can see the WIN XP recovery partition?[/COLOR][/SIZE]**

---

### Post by Mark Phelps on 2010-07-24
Don't know if the instructions in the link below under "other means of system restore" will work, but they're worth a try:

[http://en.kioskea.net/faq/2040-acer-pc-restore-to-factory-settings]("http://en.kioskea.net/faq/2040-acer-pc-restore-to-factory-settings")

---

### Post by oldfred on 2010-07-25
If you have wubi are you still booting windows first and does not windows boot.ini give you a choice for the recovery partition?

If you are not booting windows. Restore the windows XP boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

