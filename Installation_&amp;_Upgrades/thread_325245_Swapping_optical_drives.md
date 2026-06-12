---
title: "Swapping optical drives"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by DarkHorizon on 2006-12-25
Hi all, and Merry Christmas!

I've just physically installed a new optical drive (Lite-On SHM-165H6S).

The drive works in Windows (XP, SP2).

I'd like to do what's necessary to use the drive in Linux (Ubuntu Edgy 6.10) as well, but I don't know where to start! Any help is appreciated :)

---

### Post by taurus on 2006-12-25
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by DarkHorizon on 2006-12-25
I have no problems mounting NTFS drives in Linux... my question pertains to changing optical drives, and what is necessary (driver-related, mounting point related) under Linux. My mentioning of "working under Windows" is only intended to indicate physical install and test success...

I have an existing mount point which seems to mount the drive alright (/media/cdrom1 ... /media/cdrom0 is my other dvdr drive), but I am unaware of anything which must be done in order to explicitly use the new optical drive, and is what I'm asking about.

---

### Post by taurus on 2006-12-25
Plug it in.  Then look at the log message, **dmesg | tail**, to see which device it is, /dev/sda1, then mount it by hand if the automount doesn't start mounting that drive automatically!!!

---

