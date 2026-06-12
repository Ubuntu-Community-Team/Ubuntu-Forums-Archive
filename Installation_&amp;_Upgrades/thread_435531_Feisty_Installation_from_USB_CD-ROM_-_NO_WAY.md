---
title: "Feisty Installation from USB CD-ROM - NO WAY?"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by larsw on 2007-05-07
Good day all.

YES THERE IS A WAY.

This post is for you if you have only an external USB CD-ROM available which is not recognized by your bios as a bootable drive (even SMB would not help you in this case) and you can not install an external USB drive (because you have an older laptop). See HERE [http://ubuntuforums.org/showthread.php?p=1971521#post1971521]("http://ubuntuforums.org/showthread.php?p=1971521#post1971521") for my original guide on how to install edgy using a dos floppy with USB drivers and then linld to call the kernel from the CD in dos. 

HOWEVER - For Xubuntu 7.04: 
The standard Xubuntu "Desktop" image has no vmlinuz contained in the /install folder which could be called by loadlin or linld.com 
HOWEVER: There is a vmlinuz on the "Alternate" installation ISO in the /install folder. 
So with that, above instructions using linld should work just fine. Off testing it NOW...

Update: Yes, it WORKS! Make sure you obey the notes on the cdrom selection (/dev/scd0) during installation startup in above instructions! The installer can still not detect the CD in the USB drive on its onw, but it can perfectly access scd0 once you tell it about it.

regards
Lars

---

