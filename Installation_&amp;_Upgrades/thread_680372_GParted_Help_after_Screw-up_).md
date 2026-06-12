---
title: "GParted Help after Screw-up :)"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by zoso375 on 2008-01-27
So, here's what a genius I am.  I had XP/ Ubuntu dual-booted.  I decided to test out geubuntu, or openGEU, whichever you like.  After installing geubuntu on a third partition, I decided it wasn't all it was cracked up to be.  Problem was geubuntu became the primary partition as far as grub was concerned.  I posted in the forums on the best way to remove geubuntu and reinstate Ubuntu as the primary OS, to no answer.  Moron that I am, I got impatient and deleted the geubuntu partition with gparted.  Of course, the linux swap partition was there, so once deleted I could no longer boot grub, and hence I couldn't get into any of the three OSs.  So I decided to reinstall geubuntu on the now empty ext3 space, hoping I could at least revert to the previous state, again proving my genius.  So, now this is what I have:

Device Boot         Start         End      Blocks        Id  System
/dev/sda1             545       10230    77802795    7   HPFS/NTFS
/dev/sda2               1         544       4369648+    b   W95 FAT32
/dev/sda3           10231      15046    38684520   83  Linux
/dev/sda4           15047      19457    35431357+   5  Extended
/dev/sda5           19274      19457     1477948+  82  Linux swap / Solaris
/dev/sda6           19094      19273     1445818+  82  Linux swap / Solaris
/dev/sda7   *       15047      18920    31117842   83  Linux
/dev/sda8           18921      19093     1389591    82  Linux swap / Solaris


via gparted, using the geubuntu live CD.  My objective is to keep the XP and the Ubuntu partitions intact, remove the geubuntu partition, and make Ubuntu again the "primary" partition.  Is there a way to do this?  Anybody that can save me from my own brain fart, much thanks in advance.

---

### Post by chewearn on 2008-01-27
Based on info from [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), follow the instruction under Quick Start to recover grub to your previous ubuntu installation (before deleting GeUbuntu).

---

### Post by ryanVickers on 2008-01-27
ok ok ok Everyone MUST have a copy of Super Grub Tool, maybe even 2! :p

---

### Post by zoso375 on 2008-01-27
Ok, I'll give it a shot in the am...seems simple enough.  Follow-up:  do I need to create a linux-swap partition for /dev/sda3 (ubuntu) with gparted first?  Another follow-up:  assuming all goes well, it seems everything in the geubuntu partition, including linux-swaps, extended, and the ext3 are locked.  How will I be able to delete them?  

PS- I promise I'll be more careful in the future, so as not to pester you fine fellows ;p

---

### Post by chewearn on 2008-01-28
1. Ubuntu in sda3 originally has a swap; if you have not touch it, then it will still work.
2. If the partitions are locked, right-click on it, and select unmount.

---

### Post by zoso375 on 2008-01-28
Okay, so all went according to plan...thanks for the help. I deleted /dev/sda6. 7. 8.   However, now when I boot into GG, run gparted, and try to delete /dev/sda4 (extended), it's locked.  It appears to be mounted.  But, when I tried to umount via bash, it appears that /dev/sda4 does not exist.  How in the world do I get all of that space back onto my GG partition?

Oh, and I almost forgot...in the process of installing geubuntu, it screwed with my intel loader, and I now have to boot with a live CD, select "boot from first hard disk" and then I get to grub, and all is good to go.  Any ideas?

---

### Post by chewearn on 2008-01-28
> **zoso375 said:**
> Okay, so all went according to plan...thanks for the help. I deleted /dev/sda6. 7. 8.   However, now when I boot into GG, run gparted, and try to delete /dev/sda4 (extended), it's locked.  It appears to be mounted.  But, when I tried to umount via bash, it appears that /dev/sda4 does not exist.  How in the world do I get all of that space back onto my GG partition?

sda4 is extended partition; it's a "container" for all logical partitions (from sda5 to sda8 in your case).  In order to delete sda4, you have to first delete sda5 to sda8.  I think one of the swap is being used by ubuntu; this cause it to be locked, which cause sda4 to be locked as well.

Actually, you don't have to delete sda4; you can simply create a logical partition inside sda4, and use it for data storage.


> Oh, and I almost forgot...in the process of installing geubuntu, it screwed with my intel loader, and I now have to boot with a live CD, select "boot from first hard disk" and then I get to grub, and all is good to go.  Any ideas?

Not sure about intel loader, never heard of it, sorry.

---

