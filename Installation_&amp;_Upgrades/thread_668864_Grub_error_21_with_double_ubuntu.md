---
title: "Grub error 21 with double ubuntu"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by bruno9779 on 2008-01-15
I have just installed ubuntu 7.10 on my new external HD, in the hope of being able to use it as a portable computer (the idea is probably insane I realize, but i wanted to try and see if by installing ububtu on the external drive i could have my PC everywhere just by carring the external drive)
The installation went great. I can start up my original ubuntu or the external one as I please (I haven't tried it on other PCs, and I guess it wouldn't work).
The problem is that if I unplug the external drive I get GRUB error 21 (I have already searched the forums and I understand what the error message is about, but not how to fix it).
I consider my experiment failed, but I need to get my PC's GRUB back on how it was: I mean I need to start my pc also if the external drive is elsewhere (and that is the case half of the times).

Thanks in advance

Bruno9779

---

### Post by shane2peru on 2008-01-15
What happened when you installed to your external hdd, it set grub up on the external, so it automatically looks to it for grub.  You need to boot into a live CD and do this:

> 
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.


I found this here:  [http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub)

They also have a GUI way, but I have never done it that way.  If you need more specific instructions just post back.

Shane

---

### Post by ataxicwolf on 2008-01-15
aww, I typed a whole thing on it, and when I looked up you already posted ;)

You win this round!

-Stephen

---

### Post by shane2peru on 2008-01-15
> **ataxicwolf said:**
> aww, I typed a whole thing on it, and when I looked up you already posted ;)

You win this round!

-Stephen

Ha ha, I copied and pasted, I really don't type that fast. :)  

Shane

---

### Post by bruno9779 on 2008-01-15
I have already tried with the live cd, but i still get the grub error 21 thing.
to be able to boo,t my external drive must be connected.
when trying the command line way i get :

grub> root (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

If i type root (hd0,0) and setup (hd0,0) I get:

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

nothing changes

If I type root (hd0,4) no setup option is recognized (I get a "Cannot mount selected partition" error)



Talking of the 2 options I am very surprised that I cannot boot with live cd but with both ubuntus (given that the ext drive is connected.

Thanks for your swift reply!!!

---

### Post by shane2peru on 2008-01-16
Wait a minute, hold it, you mean you can't even boot off your Ubuntu CD without having your external hdd plugged in?  That isn't right.  Somehow I think your bios was set to boot off the external hdd.  You should be able to always boot from 1.  The internal hdd  2.  a USB device (external hdd)  or 3.  your CD  That is all set in the bios, and doesn't have anything to do with grub.  What I think happened somehow, is that your bios was set to **ONLY** boot from a USB device.  You need to check that first and then we can go from there.

Shane

---

