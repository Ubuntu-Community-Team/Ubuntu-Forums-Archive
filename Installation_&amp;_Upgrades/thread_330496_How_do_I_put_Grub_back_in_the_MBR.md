---
title: "How do I put Grub back in the MBR"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by charlie. on 2007-01-03
I have recently suffered the misfortune of (re)installing windows on my dual-boot machine. Because I installed Windows first (originally), I've always used the grub boot loader to boot either Windows or Linux. Re-installing Windows has stuffed Microsofts code into my MBR. (No, unlike Ubuntu, it does not give you a choice)

My /boot partition still exists and is unaltered.

I presume that all I have to do is from the live-cd and tell it to put grub back into the MBR in place of the NT loader. Unfortunately, I've forgotten how to do this. (I remember doing this some years back, although I don't think I was using Ubuntu back then.)

Please help, thanks.

---

### Post by confused57 on 2007-01-03
You can reinstall grub using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by meng on 2007-01-03
Also:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by charlie. on 2007-01-04
Thanks all, consider my question answered.

I wonder if anyone would be interested in including something like this as an OpenOffice document on the Live CD - in a folder called "Tutorials" or "Tasks", right next to "Examples". Some other documents might describe the install process, official upgrade method, etc. etc.

---

