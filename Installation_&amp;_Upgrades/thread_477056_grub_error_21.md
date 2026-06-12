---
title: "grub error 21"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by RadarListener on 2007-06-17
I have been trying to install Ubuntu on a computer for two days now. When I insert the 7.04 Feisty Desktop Standard CD, my screen is scrolled with -bash: Permission denied /dev/null errors, and I posted in this thread: [http://ubuntuforums.org/showthread.php?t=474411](http://ubuntuforums.org/showthread.php?t=474411) about them. The CD fails to start X and the HP printing "program", it also scrolls some Squash_FS superblock errors too.

So I took the hard drive out and stuck it in an identical computer and installed it there. It installed and booted fine. I put the hard drive back in and I received the error 21 message.

Today I tried again, using just the minimal CD and I was able to get into actually installing it. The install completed perfectly and when I rebooted I got the error 21 message again.

All it says is:

GRUB Loading stage 1.5


GRUB loading, please wait...
Error 21

There is no menu or anything. There is only one hard drive in the machine and it is detected on startup.

---

### Post by confused57 on 2007-06-18
> **RadarListener said:**
> I have been trying to install Ubuntu on a computer for two days now. When I insert the 7.04 Feisty Desktop Standard CD, my screen is scrolled with -bash: Permission denied /dev/null errors, and I posted in this thread: [http://ubuntuforums.org/showthread.php?t=474411](http://ubuntuforums.org/showthread.php?t=474411) about them. The CD fails to start X and the HP printing "program", it also scrolls some Squash_FS superblock errors too.

So I took the hard drive out and stuck it in an identical computer and installed it there. It installed and booted fine. I put the hard drive back in and I received the error 21 message.

Today I tried again, using just the minimal CD and I was able to get into actually installing it. The install completed perfectly and when I rebooted I got the error 21 message again.

All it says is:

GRUB Loading stage 1.5


GRUB loading, please wait...
Error 21

There is no menu or anything. There is only one hard drive in the machine and it is detected on startup.

You might try entering bios setup & make sure the hard drive controller is set to "auto" and other hard drive controllers not being used are set to "off"...may not be the problem, but worth trying.

---

### Post by RadarListener on 2007-06-18
Thanks, but I have tried that already.

I was thinking of things I haven't tried, and I thought of changing over the SATA cable from SATA1 on the motherboard to SATA2.

Beleive it or not, that actually fixed the problem!

I'm still, however, having the /dev/null problem when I try to install, but that's easily bypassed by installing it on the duplicate system in the other room and then moving the hard drive back.

Thanks again.

---

