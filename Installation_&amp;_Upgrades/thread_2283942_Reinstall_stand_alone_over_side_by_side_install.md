---
title: "Reinstall stand alone over side by side install"
date: 2015-06-25
forum: Installation &amp; Upgrades
---

### Post by padrejeff on 2015-06-25
Did a side by side install (Win7).
Would now like to do a stand alone install wherein all Win7 is gone.

Can I do this without loosing programs and data already installed to Ubuntu?

---

### Post by dino99 on 2015-06-26
if you already have a separate /home partition , then your data are safe until you format that partition. Otherwise backup your data first.

---

### Post by Bucky Ball on 2015-06-26
You don't need to format the partition to get rid of it. Just delete it.

Boot from the live media you install Ubuntu from and choose 'Try Ubuntu'. Open Gparted and delete the Windows partition. Expand the Ubuntu partition to fill the unallocated space the Win deletion creates. Hit the 'Apply' button. Reboot from the hard drive. Once at a desktop, open a terminal and:

```
sudo update-grub 
```

If the machine doesn't boot you may have to reinstall grub. Grub can be re-installed via a terminal on a live desktop or by using Boot Repair, which will fix things 'automagically' (90+% of the time). 

Boot repair links:

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

You don't need a separate /home partition  to do any of this (and if you do have one it is absolutely no guarantee against user error and therefore superfluous whether you do or don't have one ... a /home partition on the drive you're working on is no safeguard against user error nor an external backup of your data). What you do need to do is backup any valuable data before proceeding. One never knows ... keep the cat away from the keyboard while you're doing this! ;)

---

