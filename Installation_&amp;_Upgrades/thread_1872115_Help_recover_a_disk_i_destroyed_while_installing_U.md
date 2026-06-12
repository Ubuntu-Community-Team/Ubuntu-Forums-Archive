---
title: "Help recover a disk i destroyed while installing Ubuntu"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by guric1van on 2011-10-30
I have a 1TB HDD which is a secondary disk used to store important data. My primary disk which is the boot disk is partitioned, which is where i had planned to install Ubuntu on. 

While doing the Ubuntu install and selecting the disks, i think I selected the wrong disk, and accidentally selected the 1TB disk as the swap space for Ubuntu.

This has resulted in the 1TB being reformatted, and is now only seen as ~32MB by every OS (i'm still using Windows as my primary desktop). I have lost all the other data on the disk. I am desparately trying to recover the disk as it was.

I have tried a few recover apps, and they can recover some files, but only those that reside on the 32MB segment of the disk, they wont look to the entire 1TB. 

How can i get the disk back to be seen as 1TB, and then recover all the files?

Very desparate and any help would be appreciated.

---

### Post by raja.genupula on 2011-10-30
Hi man Go with this 

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)


all the best

---

### Post by LinuxFan999 on 2011-10-30
> **guric1van said:**
> I have** a 1TB HDD** which is a secondary disk used to store important data. My primary disk which is the boot disk is partitioned, which is where i had planned to install Ubuntu on. 
 
While doing the Ubuntu install and selecting the disks, i think I selected the wrong disk, and accidentally selected the 1TB disk as the swap space for Ubuntu.
 
This has resulted in the 1TB being reformatted, and **is now only seen as ~32MB by every OS (i'm still using Windows as my primary desktop).** I have lost all the other data on the disk. I am desparately trying to recover the disk as it was.
 
I have tried a few recover apps, and they can recover some files, but only those that reside on the 32MB segment of the disk, they wont look to the entire 1TB. 
 
**How can i get the disk back to be seen as 1TB, and then recover all the files?**
 
Very desparate and any help would be appreciated.
How old is this hard drive?

---

### Post by Mark Phelps on 2011-10-31
Since you said you were using Windows as your primary desktop, if the 1TB disk was formatted with NTFS partitions, in my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

