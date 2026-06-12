---
title: "Wubi: No root file system is defined."
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by jamesclish on 2009-12-04
Hi all.

[I couldn't see a dedicated area for Wubi installs; could a mod move it as necessary?]

Because my partition table is absolutely screwed (the regular installer sees no partitions, rather a whole, unpartitioned volume...), I need to install Ubuntu via Wubi.

Inside Windows Vista, I installed Ubuntu 9.10 through Wubi, and was told to restart.

On restarting, I get an error dialogue saying:

"No root file system is defined.
Please correct this from the partitioning menu."

Any ideas? As I said, I would install the usual way, but the partitioner on the cd doesn't recognise any partitions...

Thanks,
-James

---

### Post by darkod on 2009-12-04
I think it is much better to troubleshoot why you can't install in "normal" way. Wubi is a different type of install and plus it seems the same problem about the partition table is present there too.
You could boot with the ubuntu cd for example, select Try Ubuntu option and it will run from the cd.
Then you can open Gparted (System-Administration) and see what it shows about your disk and partitions.
Also, in Terminal (Applications-Accessories) execute:
sudo fdisk -l (small L)

that should list all partitions. Copy the results of fdisk here and/or attach screenshot of Gparted, we might figure it out. Using ubuntu like that from the cd will usually give you internet access too so you can post that easily, no rebooting, etc.

---

### Post by jamesclish on 2009-12-04
> **darkod said:**
> I think it is much better to troubleshoot why you can't install in "normal" way. Wubi is a different type of install and plus it seems the same problem about the partition table is present there too.
You could boot with the ubuntu cd for example, select Try Ubuntu option and it will run from the cd.
Then you can open Gparted (System-Administration) and see what it shows about your disk and partitions.
Also, in Terminal (Applications-Accessories) execute:
sudo fdisk -l (small L)

that should list all partitions. Copy the results of fdisk here and/or attach screenshot of Gparted, we might figure it out. Using ubuntu like that from the cd will usually give you internet access too so you can post that easily, no rebooting, etc.

I'm just waiting for a chkdsk in the hope that might fix something... Will post the fdisk output when it's finished - keep your eyes peeled!

Thanks,
-James

---

### Post by jamesclish on 2009-12-04
> **darkod said:**
> I think it is much better to troubleshoot why you can't install in "normal" way. Wubi is a different type of install and plus it seems the same problem about the partition table is present there too.
You could boot with the ubuntu cd for example, select Try Ubuntu option and it will run from the cd.
Then you can open Gparted (System-Administration) and see what it shows about your disk and partitions.
Also, in Terminal (Applications-Accessories) execute:
sudo fdisk -l (small L)

that should list all partitions. Copy the results of fdisk here and/or attach screenshot of Gparted, we might figure it out. Using ubuntu like that from the cd will usually give you internet access too so you can post that easily, no rebooting, etc.

Ok. The fdisk output is as follows:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+   6  FAT16
/dev/sda2   *          11       19070   153098240    7  HPFS/NTFS
/dev/sda3           19071       19458     3116610    f  W95 Ext'd (LBA)
/dev/sda5           19071       19130      481908   82  Linux swap / Solaris
/dev/sda6           19131       19458     2620416    c  W95 FAT32 (LBA)

```

Thanks,
-James

---

### Post by darkod on 2009-12-04
OK.
/dev/sda1 seems to be some small 80MB FAT16 partition. Maybe some kind of utility partition. Are you using it at all? Sometimes they can make real problem, but you should not delete it unless you're sure you don't need it.
Otherwise it looks normal. Did vista come preinstalled?
And do you know what is /dev/sda6, around 2.5GB FAT32? Recovery partition?

---

### Post by jamesclish on 2009-12-04
> **darkod said:**
> OK.
/dev/sda1 seems to be some small 80MB FAT16 partition. Maybe some kind of utility partition. Are you using it at all? Sometimes they can make real problem, but you should not delete it unless you're sure you don't need it.
Otherwise it looks normal. Did vista come preinstalled?
And do you know what is /dev/sda6, around 2.5GB FAT32? Recovery partition?

The 80MB FAT16 partition does indeed seem to be a utility partition. It has some Dell-related files floating around on it.

As for the 2.5GB FAT32, it's Dell's built-in "MediaDirect" utility, which, at the press of a button on the case, will boot into some sort of media center.

According to Wikipedia, it's a fairly common issue: "It is written for Microsoft Windows environments and provides many difficulties for users wishing to install Linux upon their Dell machine." ([http://en.wikipedia.org/wiki/Dell_MediaDirect](http://en.wikipedia.org/wiki/Dell_MediaDirect))

Any ideas?

Thanks,
-James

---

### Post by darkod on 2009-12-04
Hmmm... Get rid of both of them? :)
If you are SURE you have no use of them, it's really good practice to delete them. Not to mention you free up some space.
But deleting the 80MB utility might mess up slightly vista boot, depending how they organized it. You better have vista rescue disc ready if you don't have vista dvd. If you do have, you can restore the boot process with it (IF it breaks down, it don't mean it will).
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by jamesclish on 2009-12-04
Ok. I nuked both of those partitions. Vista still boots fine. However, gparted on the Ubuntu installer CD still can't see any of my existing partitions...

I'll do another fdisk and post it.

---

### Post by darkod on 2009-12-04
Does it show the disk at all, as empty, or not showing it like you have no hdd?
I've seen caes where there is no drive shown, and booting in Try Ubuntu and in terminal doing:
sudo apt-get remove dmraid

helps. Basically if the disk has some remains of raid settings. But I'm not sure this is the case. You can try it anyway, doesn't hurt.

---

### Post by jamesclish on 2009-12-04
It shows as one whole, unpartitioned, 160GB hard drive.

I tried the dmraid command. No dice.

The output of the fdisk:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          11       19070   153098240    7  HPFS/NTFS
/dev/sda2           19071       19458     3116610    f  W95 Ext'd (LBA)
/dev/sda5           19071       19130      481908   82  Linux swap / Solaris

```

Thanks,
-James

---

### Post by darkod on 2009-12-04
One option I've seen on the forum for repairing partition tables is this:
[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

I haven't used it myself, didn't need to so far. :) It seems to help some people if the partition table is actually damaged. You are probably aware any operation like this is risky. You better back up your data on external hdd in case.

PS. I looked in the last fdisk but can't see anything wrong. You can also delete that swap/extended partition too, you don't seem to have ubuntu installed. You will create swap during the install. I'm not sure if the wubi install made something to the partition table, just a guess of mine. I'm out of ideas, sorry.

---

### Post by jamesclish on 2009-12-04
I've actually used TestDisk in the past, but to no avail.

Really, if it meant I could return my partition table to normal, I'd be willing to reinstall windows and ubuntu fresh. Is there any way I can completely format the hard drive and repartition it?

---

### Post by darkod on 2009-12-04
Yeah, completely formatting should help. Boot with the vista dvd, delete all partitions, create just one ntfs partition you want with the size for vista, and install vista. But when creating the partition consider if you would like another separate ntfs partition for data, and what sizes they should be.
Once vista is running, create the second ntfs if you decided to have one, but leave some unpartitioned space for ubuntu.
And after all of that the ubuntu install should go just fine.

---

### Post by jamesclish on 2009-12-04
I'm reinstalling Vista as we speak (wish me luck). I'll let you know how I get on.

Thanks a lot for your help! Very much appreciated. :)
-James

---

### Post by jamesclish on 2009-12-04
All installed, perfectly dual-booting once again.

Thankyou, kind stranger :)

Now, I begin that awful struggle to find drivers and the like!

-James

---

### Post by darkod on 2009-12-04
Glad you got it going. :)

---

