---
title: "System does not load GRUB after Ubuntu install"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by raculot on 2007-01-02
I have installed Ubuntu on the same hard drive as my Windows install by re-sizing the drive for Ubuntu.   However, after installing Ubuntu and re-starting the computer, GRUB does not appear to load and the computer simply boots straight to Windows.  So for the moment, I'm at a loss for how to solve the issue.  I bassically installed the system normally and used the AMD64 desktop disc.

Here is the hardware of my computer.

AMD Athalon 64 3800+
ASUS A8N5X motherboard
nVidia GeForce 7600GS 
SCSI Seagate Cheetah 15K

I think it might have something to do with the SCSI drive but not completely sure.  

Does anyone have any suggestions on what I could do to fix this problem?

---

### Post by moffa on 2007-01-02
It seems as if Grub was not installed or removed.  I know it happens when you install Windows after Linux.

Use the Live-CD and reinstall grub.  That should work.

---

### Post by Zer0Nin3r on 2007-01-02
I think it's much simpler than that.  Are you going into your boot menu?  You may have to configure that through your bios.  I'm still trying to get the install to work with the current graphic card I have (GeForce 7900GS.)  You'll have to give your self the option of choosing which os you want to boot off of.  Hope this gives you some insight.

---

### Post by raculot on 2007-01-02
Well so far I have found out that if I leave a bootable CD in my CD drives, such as WinXP install disc or the Ubuntu install disc, and then boot to my hard drive after the CD has booted, Grub comes up just fine and I can boot Linux or WinXP no problem.  Otherwise, without a CD booting first, the system will just go straight to Windows.  

So it's really odd, and it's probably something really simple that I don't know about yet.  Any more incite is appreciated, thanks.

---

### Post by bulldog on 2007-01-02
If you can post the output of
 ```
sudo fdisk -l (l as in like)
cat /boot/grub/menu.lst
```
[two different commands]so we can have a look what's wrong.

---

