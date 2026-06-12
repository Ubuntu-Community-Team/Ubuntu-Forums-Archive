---
title: "Opinions Wanted: SATA HDD, RAID Controller, &amp; Linux"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by z-vap on 2008-03-26
Initially I had Winxp installed on hd0.  I wanted to start transitioning myself to use Ubuntu as my new primary operating system, so I created another partition (hd0,1) and put Ubuntu there.  

Here's where it get interesting.  I started running out of space, so I picked up a 500G WD SATA HDD from Best Buy.  Cool, right?  Wrong!!  I installed Ubuntu onto this HDD (hd2,0) but I keep getting GRUB: Error 17.  No matter what configuring I do, I cannot seem to get my PC to boot into this drive.  

Upon doing my research, it seems that there are quite a few problems with Linux & Grub understanding a Silicon Image sil3112 SATA/RAID Controller, or any motherboard RAID Controller for native Linux booting.   I **can** see the ext3 trhat I formatted onto this drive.  I can mount the filesystem from a Live CD or from my existing Ubuntu install.  A friend suggested that I may have success if /boot was on an IDE drive.  I've also read that others have had suggested SuperGrub LiveCD as a solution to various boot problems.  

By the end of business today, I will need to make a decision.  Can anyone here assist in my thinking.

1) Partition /boot onto the PATA hd0 disk, and have / exist on the SATA
2) Try the FakeRaidHowto
3) Give SuperGrub a try
4) Save the headaches, take the drive back and get a PATA drive


Please vote and let me know what you think.

---

### Post by z-vap on 2008-03-26
Thanks for all the replies.  Nice to know there's alot of help around here.  :mad:

I guess it's going to be taken back to the store.

---

