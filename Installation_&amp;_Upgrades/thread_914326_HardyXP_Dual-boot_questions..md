---
title: "Hardy/XP Dual-boot questions."
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by ShakeyJake on 2008-09-08
Right, so Im currently running Gutsy and I would like to upgrade to Hardy but my course kind of requires me to have Windows too so I was thinking of dual booting when I move up. I have an external hard drive that has backups of everything so reformatting the entire HDD isnt an issue. 


I was thinking of using GParted on the live CD (or even on my installed 7.10 if that's possible) to format my disk into three separate partitions now and then install my OS's and data what do you think? Its a 300GB HDD.

 50GB ntfs XP
 50GB jfs Hardy (inc some swap space)
~200GB ??? shared data between OS's

Is this even possible? Ive had a look through some of the guides online, but they seem to mess around with slowly changing/partitioning the disk, is there something wrong with my plan?

Cheers guys,
Jack

---

### Post by Pumalite on 2008-09-08
Post:
sudo fdisk -lu

---

### Post by caljohnsmith on 2008-09-08
Yes, you can still use gparted from the 7.10 Live CD to do your partitioning if you want. Your plan looks good I think; make sure you install Win XP first and then Hardy after that to minimize your hassles, because installing XP after Hardy will overwrite Grub in the master boot record and make it so you can't boot Ubuntu until you put Grub back into the MBR. Another thing, keep in mind you can have only 4 primary partitions, or you can 3 primary partitions and one extended partition that has up to 63 logical partitions. So if in the future you might want to add more partitions, it would be good to set up an extended partition at the outset. Good luck and let us know how it goes. :)

---

