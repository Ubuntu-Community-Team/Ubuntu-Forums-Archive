---
title: "Gparted sees ext3, GRUB doesn't"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by dme7 on 2007-04-10
G'day ...

I've successfully installed 6.10 on a multi-boot system, and been running it (and rebooting) with no proiblems for weeks.  Twice, now, I've booted back into XP in order to apply patches, and when trying to get back into 6.10 I've encountered GRUB error-17 issues.  

Running off of the CD, I find that GParted recognizes the 6.10 installation as ext3, and I can mount it and everything's there, but GRUB insists that it can't recognize the partition (labels it type-93), and refuses to "find" anything in it (claims that the partition can't be mounted).  Super GRUB has the same issues.  A thread I just found claims that type-93 means that the partition is hidden, and that fdisk can change it back to 83 (or 82, whichever is normal-unhidden) ... can someone confirm this, please?  

And I'd very much like to understand why this occured in the first place ... I have to change the boot-order in the BIOS in order to boot 6.10 (XP requires the first HD first, 6.10 requires 'bios boot devices' first), and I seem to run into problems after having made this mod.

Many thanks, folks.

doug

---

### Post by john_spiral on 2007-04-10
Please have a look at the below thread:

[http://ubuntuforums.org/showthread.php?t=396706](http://ubuntuforums.org/showthread.php?t=396706)

you will need to edit your /boot/grub/menu.lst file 

more than likely you will need to change your Windows entry to the below:

title Microsoft Windows XP Professional
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
savedefault

---

