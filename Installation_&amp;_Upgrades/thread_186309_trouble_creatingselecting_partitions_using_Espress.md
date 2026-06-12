---
title: "trouble creating/selecting partitions using Espresso...please help"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by Loungefly on 2006-06-01
Hellooo

I'm using the liveCD to install Dapper and I'm having a hell of a time setting up the partitions for Dapper to dual boot with XP.

First off, I have a standard primary NTFS partition for XP and I have an extended partition that's 34gb, inside that extended partition is a FAT32 of 25gb for sharing between Linux and Windows, so inside that extended partition I have 9gb let over that I'm wanting to use for Dapper (and the swap partition).

I get to the part in Espresso where I manually edit the partition tables. Out of that extra 9gb inside the extended partition I created a 1 gig partition for the swap and used the rest to create the root partition for Dapper. It creates everything ok, but then I go to the next screen and it asks me where I want to mount my installation. It lists the NTFS partition, then it lists the FAT32 partition. Nowhere does it give me an option to select the newly created swap and root partitions. It's as if it will only allow me to overwrite the existing FAT32 and NTFS partitions. 

I confused as to what I'm doing wrong here.  Any help would be greatly appreciated.

Thanks :)

---

### Post by frodon on 2006-06-02
hehe, i got the same issue, just run gparted in system > Administration > Gnome Partition Editor, make all your partition with gparted then start the installer and it will be good.

Good luck ;)

---

