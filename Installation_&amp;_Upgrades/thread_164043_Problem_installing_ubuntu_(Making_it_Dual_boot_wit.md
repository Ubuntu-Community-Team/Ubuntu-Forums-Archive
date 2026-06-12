---
title: "Problem installing ubuntu (Making it Dual boot with XP)"
date: 2006-04-22
forum: Installation &amp; Upgrades
---

### Post by cybaster80 on 2006-04-22
Hi ppl,
         I'm a newbie to ubuntu. I have tried using the LiveCD version and it works well in my desktop. The problem is I am unable to install the ubuntu into my current desktop. The problem is when the installations come to the partition disks portion. It is unable to detect any HDD. I have used partition magic to partition out my 40 GB HDD into this format 

(100MB FAT32 for bootmagic - F:, 20GB NTFS Win XP - C:, 8 GB FAT32 - ubuntu to be install here - G:, 10 GB FAT32 - this partition is to transfer files between xp and ubuntu - H:) 

It is a bit messy..hopefully someone can understand it :)

This is my hardware setup up, Intel P4 2.8GHz, 2 x 512MB Ram, 1 x Pioneer Dvd Drive at IDE 1, 2 x IDE Maxtor 40 GB HDD at IDE 2. MB gigabyte GA-8I945P-G with built in [COLOR="Red"]GigaRAID ITE8212 IDE RAID controller [/COLOR]
1 x PX6600 WinfastGT PCI-e

I believe the raid controller might be causing the problem..any solution to this?

I am unable to put my HDD at IDE 1 as the motherboard does not detect it :(
And my DVD rom won't work if i put it at IDE 2. This is due to manufacturer's setting.

Thanks for helping.

---

### Post by bscbrit on 2006-04-22
I think that you will have to delete your drive 'G' - Ubuntu is probably looking for empty space and you have formatted it as FAT32.  Ubuntu will format the empty space as ext2 when it installs.

I think the problem that you are having with drives on IDE1 and IDE2 is perhaps caused by the master/slave setting.  You can only have one master and one slave on each IDE connector.  I've never heard of a DVD player that is fixed by the manufacturer to a specific IDE cable. If you have changed the master/slave settings and you are convinced that is not the cause of the problem, then configure the BIOS to make sure it knows where to find the various devices.

You do know that drive names such as 'G' are absolutely meaningless to Linux, don't you?  If you are trying to find drive 'G' when you are installing then you never will. Drives under linux are known as /dev/hda, /dev/hdb etc, which indicates the first parallel hard drive (hda) and the second (hdb).  Partitions on those drives will be named as hda1, hda2 etc showing the first partitiion on hard drive a, and then the second.

---

### Post by cybaster80 on 2006-04-22
Hi bscbrit,
              Thanks for replying. Ya..i do know the Drive letters are meaningless in linux. But the problem is nothing shows up at the partition disks portion. That is even when i wipe out everything and started from scratch. 

For the IDE part...IDE 1 is connected to my Dvd Rom and set as master. 2 HDD at IDE 2 one as master the other as slave.

I suspected it might be the GigaRAID ITE8212 IDE RAID controller becaused even when installing XP in it, it needed to load the raid drivers b4 it can detect my HDD. (which i had no intention of using RAID)

Thanks again.

---

### Post by bscbrit on 2006-04-22
Yes - I would suspect the raid controller as well.  You might want to try switching the IDE1 and 2 cables although why that might cause Ubuntu a problem is uncertain.  I wouldn't use partitions for Linux that have been created using a Windows program.  More often than not, they work perfectly, but I have also experienced problems with the partitions created under one OS not being suitable for use on the other.

Sorry if I was stating the obvious to you - no offence intended.

---

### Post by cybaster80 on 2006-04-22
haha..Its ok.

Anyway, i tried the method from this [http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#installonnewhdd]("http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#installonnewhdd")

I booted into the Live CD from ubuntu and used the gpart to try to partition my HDD. This is wat i saw on the gparted.

/dev/mapper/casper-snapshot1 (2040)MB

/dev/mapper/caspter-cow(1020)MB

Instead of the hda or hda1 that is suppose to appear on the gpart.

Any Advice??

---

### Post by bscbrit on 2006-04-22
Yes,  when you are running a live disk, it creates imaginary partitions on your hard drive.  In this case it has called them casper-*.  However, they cannot be your standard partitions (just compare the sizes with the figures that you gave me in an earlier post).

I don't know enough about live distros to tell you how to get gparted to recognise them.  

If you are trying to install Ubuntu to your hardrive, follow it through until it gets to the partitioning stage, then select manual partitioning.  Use the ubuntu installer to delete the 'G' partition and then tell it to use the free space to install ubuntu.  Done.

---

### Post by cybaster80 on 2006-04-22
IC...i tried swapping IDE cablings, it is able to detect my HDD, but my optical drive is not detected. 

From the link that i have provided. The writer just booted from the Live CD and is able to use the gparted to format the partition.

I have tested out using my laptop. It is able to see the hda. But it doesn't shows up on my desktop.

:confused:

---

### Post by bscbrit on 2006-04-22
If you follow the procedure in the link that your provided, where do you have a problem?

---

### Post by cybaster80 on 2006-04-22
the problem is i still can't see the hda when i used gparted...it doesn't shows up....meaning there is no HDD in it.

---

### Post by bscbrit on 2006-04-22
What can you see in GParted?  Have you tried selecting /dev/hdb in the the right-hand icon at the top of the display in GParted?

---

### Post by cybaster80 on 2006-04-22
Ya...tried it b4

these are the only 2 things i see

/dev/mapper/casper-snapshot1 (2040)MB

/dev/mapper/caspter-cow(1020)MB

Maybe its becoz my MB is a new board?so ubuntu can't find the Hard disks?

---

### Post by bscbrit on 2006-04-22
I don't think that it is because the board is new, but there might be some hardware incompatiblities that are preventing it from working.  I'm afraid that I have got nothing useful to suggest at this stage.  I'll think about it overnight but I'm not too optimistic.

---

### Post by cybaster80 on 2006-04-23
Guess i can't install ubuntu for now...hopefully the next release will solve my problem..haha

---

