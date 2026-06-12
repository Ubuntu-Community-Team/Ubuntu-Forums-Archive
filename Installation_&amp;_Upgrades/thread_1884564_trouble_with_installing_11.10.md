---
title: "trouble with installing 11.10"
date: 2011-11-21
forum: Installation &amp; Upgrades
---

### Post by robbiejormerod on 2011-11-21
Hi all. I'm quite, no very new to this so please forgive anything stupid I may say.
 I'm trying to install ubuntu on to a 44gb hard drive partision the other 120 gb has vista running on it. When I try to install from a disk when I get to the point to select a drive no drives are shown in the dialog box and I cant go any further. 
  Also if i try to run firefox when I'm in the Try Ubuntu section it keeps saying there is a error and won't start, I dont know if thats relevent. Its probably something simple but I'm just learning so any pointers would be welcome.

---

### Post by mikewhatever on 2011-11-22
Hello, and welcome to the forums.

You might have a problem with the installation media, perhaps a bad burn or something. To check if the disk is good, hit any key as soon as you see the purple background (right after the BIOS screen), and select "Check the installation media" from the menu.

Generally, it's advisable to burn installation CDs at the lowest speed possible (x4 or so).

---

### Post by robbiejormerod on 2011-11-24
Thanks for that I'll retry burning the cd, last time I did it at max speed. I'll have to learn to be in less of a rush. :o

---

### Post by robbiejormerod on 2011-11-26
Ok I've tried reburning the iso image but no joy. I get as far as the connect to a network, can do that ok,then I get a screen that says installation type but it just isn't displaying any of my drives. I have two sata drives on my system, one split in to two partitions one with vista on the othe empty and the other drive is compleatly empty with no partition split. They are being detected in bios in IDE 2 & 5. I've tried disconnecting them one at a time but still nothing. Please help. :confused:

---

### Post by darkod on 2011-11-26
If the disks were ever used in RAID they have remains of meta data on them and in such case the ubuntu installer is ignoring them.

According to your post, you are not running any raid right now, so first use the Try Ubuntu option to boot into live mode, open terminal and execute:

(DO THIS ONLY IF YOU ARE NOT RUNNING RAID!!! It will destroy any raid array you might have!)

sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

If it asks confirm you want to remove the meta data. Reboot and start the install process and it should be fine.

---

### Post by robbiejormerod on 2011-11-26
Thanks for that, Ill give it a try when i get home.I'm not that bothered about losing anything on the hard drives as this is a project box for learning Linux, I have another PC for my main day to day computing. :o

---

### Post by robbiejormerod on 2011-11-26
Woo Hoo. Thanks for that I'm well under way now but I'm sur I'll be back with loads more questions. :KS

---

