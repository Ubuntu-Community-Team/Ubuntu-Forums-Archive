---
title: "Dual boot, two HDs. Separate /boot partition advisable?"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by mailforbiz on 2007-06-12
Hi

Would like to know if I'm doing this right. I have two discs A & B with Xp on the first disc. There is unpartitioned space on the second one which I'm planning to install Feisty on. 

After researching a bit, this is the partition map I came up with. I know this is somewhat subjective but any comments if I'm heading in the right direction. 

My ideal setup is 
(a) to have a root partition that can easily be formatted/upgraded 
(b) not have to touch the main MBR if I can (hence  the separate  /boot). 
(c) as much isolation between the two OSs (hence the separate drives.unluckily, still need ntfs on HD B)
Are there any other advantages to having separate /boot? Also, how about /boot on a floppy or a CD? Is the numbering correct for grub menu.lst ? i.e root= /dev/hdb2 is the correct pointer? And how do I denote the "device for boot loader installation" which deaults to (hd0)?


/dev/hdb0   ntfs      windows (apps- can't get rid of this yet)
/dev/hdb1   /boot    primary ext3  300Mb
/dev/hdb2   /           primary ext3   10Gb
/dev/hdb4   /home   logical ext3 100Gb
/dev/hdb5   /usr       logical ext3 10Gb
/dev/hdb6   /usr/local        logical ext3 10Gb
/dev/hdb7   /var       logical ext3 10Gb
/dev/hdb8   swap     primary swap 2Gb


Feel free to point out alternatives (including different partition types) and logic behind using them.

Thanks in advance!
HT

---

### Post by MentholLite on 2007-06-13
You may also want to consider having both XP & Ubuntu on the 1st drive.
And have the 2nd drive as the **Data** drive for both XP & Ubuntu.

For me, is much straightforward.
I got 2 drives as well; 1st drive with XP and NTFS related files, 2nd drive with Ubuntu, /home & swap directory.

**1st drive**
/dev/hdb0 ntfs windows

**2nd drive**
/dev/hdb1 / primary ext3 10Gb
/dev/hdb2 /home primary ext3 40Gb
/dev/hdb5 swap logical swap 2Gb

LOL

---

