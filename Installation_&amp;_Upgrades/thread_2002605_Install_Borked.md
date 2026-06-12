---
title: "Install Borked"
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by Nate15810 on 2012-06-12
Hey all,

As a last resort to my problem, I have come to the forums!
Alright, here it goes.

A while back, I installed Ubuntu over a copy of windows. At the end of the semester, I rm -rf'd the drive, rendering it useless. Now here comes summer and I feel like reinstalling Ubuntu. Start it up, stick in my bootable thumb drive with Ubuntu 12.04 on it, and I get a bootmgr error. I used LinuxLive and created another boot stickso I could install it and it still didn't work. SO I reformatted the hard drive in windows' partition manager on my other computer and plugged it into the nettop. 

For the problem, I cannot get the LinuxLive boot stick to run. I always get the error "error: unknown filesystem" in the boot screen. I tried playing around with switching the root drive to (hd1,msdos1), (hd1,0), and (hd1), which all don't work. As of right now, "set" is showing this:
```
prefix=(hd0,msdos1)/boot/grub
root=hd0,1

root was formally hd0,msdos1
```
Grub will also not recognize "sudo", "root", "setup", or "quit"

---

### Post by wilee-nilee on 2012-06-12
Boot the thumb with the per session from boot from menu, it is outside of the bios.

Mine is f12 at powering on, yours may be different the web will tell you what it is for your computer model.

Grub only works if it has all the files to access, those of which you removed with the OS.

---

### Post by Nate15810 on 2012-06-12
Apparently the boot stick that LinuxLive created can't be booted from for some reason...I disabled all boot devices other than the stick and it failed boot.

.:Edit:.
Remade the boot stick.
Found that it was classified as a hard disc, so I just swapped the priority of the two. 

Thanks for the help!

---

