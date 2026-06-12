---
title: "A New HP Laptop installation issues."
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by hellmet on 2007-10-31
My friend has the new dv6000 series HP laptop. Now, there were several problems installing GRUB. So, we decided to wipe off Vista, and the partition table and start from scratch. Once we did that, ubuntu no longer even installs. 
Once I click the last step "Install", it starts formatting the drive, after which it gives a dialog box that reads " Input/Output Error, There either is a problem with the cd or the HDD. I've tried both Feisty and Gutsy, so its not the cd. The HDD was completely formatted and I also tried Gudied Partitioning. All in vain. Even Feisty alternate fails. Any help appreciated.

---

### Post by mikewhatever on 2007-10-31
Have you tried [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29") checking the isos and running integrity checks of the CD? Trying two different releases does not make sure the CD is OK.

---

### Post by vmaric on 2007-10-31
hi everyone .

I just upgraded ubuntu feasty 7.04 on version 7.10 and i have a litl problem like in 7.04 
 i havent sam things, like a can not see battery on gnome panel and i cant put it there.

meesage  of my ubuntu is:

The panel encounterd a problem, while loading. (And when reboot it I have same things)

OAFIID:GNOME_MixerApplet_BattstatApplet

Have somebody eny idea?

I reinstall gnome-panel and gnome-panel-data and it dont help my!

---

### Post by one4many on 2007-10-31
i had a similar problem - try booting with a windows boot disk and useing fdisk to _remove_ all partitions.  Then start the install by booting your Gutsy CD.  For some reason the install partitioner does not like HD already partitioned and formatted. Make sure to set LILO so you can later install windows

---

### Post by hellmet on 2007-10-31
I've tried all kinds of partitioning, but in vain. XP installs a breeze. But, no Linux. When I try the alternate disc, at the Select and Install software part, it gets stuck at 6%, and then says "Can't write to HDD, step failed"

---

