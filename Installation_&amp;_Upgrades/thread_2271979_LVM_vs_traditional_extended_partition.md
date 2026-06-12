---
title: "LVM vs traditional extended partition"
date: 2015-04-03
forum: Installation &amp; Upgrades
---

### Post by HMN on 2015-04-03
Greetings

I find LVM to be of little advantage to desktop-pc setup. Instead, I would like to format the entire SSD with a single extended partition that I can manage in gparted. I also like to use the dd command to do occasional backups. This is simple and straightforward compared to learning and setting LVM.

Any thoughts would be appreciated.

Regards

---

### Post by dino99 on 2015-04-03
you should read about what LVM is and what it brings. your config with 1 ssd only does not file the required spec

---

### Post by grahammechanical on 2015-04-03
A lot also depends on the boot system on the motherboard. If it is BIOS, then indeed, we do get involved with primary, extended and logical partitions. If it is UEFI then we have GPT and I do not think we have to worry about the 4 primary partition limit with GPT.

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Regards.

---

### Post by HMN on 2015-04-03
I thought you can still use LVM on a single disk or even a single partition.

> **9d9 said:**
> you should read about what LVM is and what it brings. your config with 1 ssd only does not file the required spec

---

### Post by HMN on 2015-04-03
Thanks. Exact answer I was looking for. If I use GPT, then there is no need to worry about this.

> **grahammechanical said:**
> A lot also depends on the boot system on the motherboard. If it is BIOS, then indeed, we do get involved with primary, extended and logical partitions. If it is UEFI then we have GPT and I do not think we have to worry about the 4 primary partition limit with GPT.

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Regards.

---

### Post by oldfred on 2015-04-04
This is from the author of gpt's gdisk. He seems to like LVM, but I think he has larger drives & reconfigures a lot.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

I have never used it and thought it was mostly another work around to the 4 primary partition limit of MBR(msdos). But it does allow repartitioning on the fly and spanning multiple physical partitions or even drives with the risk of loss of all data if one drive fails. It is used for full drive encryption.
I tend toward reliability first.
I do prefer gpt and now use it for all new drive even my flash drives.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by UberGeekInc on 2015-04-04
Hi Hmn.

I can not think of a single install that would not benefit from using LVM.  From overly simplistic *single partition* installs to complex multi-disk.  The flexibility it gives you far outweighs its costs.

Yet  your questions sounds like you are comparing [GUID Partition Table]("https://wiki.archlinux.org/index.php/GUID_Partition_Table") and [Master Boot Record]("https://wiki.archlinux.org/index.php/Master_Boot_Record") configurations - and not LVM.

---

### Post by MikeMecanic on 2015-04-05
I"m having all kinds of problems each time I don't choose the LVM option during installation.  For me, to make it simple, LVM is one step above God.[IMG]http://ubuntuforums.org/images/icons/icon6.png[/IMG]

---

### Post by MAFoElffen on 2015-04-05
LVM is easy if you learn how to use the utilities, just like with mdadm. I use a lot of LVM... here's some pro's and con's.

Think of what you will have as an architecture and what your growth may be.

A default LVM install sort of hits a bump (boundary) after about a year of use. It sets a small boot partition of about 250MB. After about a year of kernel updates, you'll get an error saying the boot partition os running out of room and you'll need to purge old kernels.  Some say to up the /boot partition to 500MB. On my servers, that I set up with LVM... I set their LVM /boot partition to 1GB... on GPT disks.

The next con is that any striped volume is a risk for losing what is there if one of the physical volume extents has problems. But this is not a problem if you remember to actively backup your data!!! Any recovery plan should have backups as part of it.

Pro's- You can mirror volumes, You can take snapshots of increment changes as backups. You can define temp volumes to write those snapshots to, before writing to elsewhere. You can extend your space in minutes...

There is a lot of advantages to LVM, that make it flexible, adaptable and painless. (remember backups.) To me, the advantages outweigh any con's. 

But like I started out with-- It all depends on what you want to do and if you ever think you will grow.

My recommendations... for you? No. Why would I say no after talking up LVM?  --> SSD <-- A striped volume is only going to be as fast as it's slowest member. You can mirror ssd's. You can strip SSD's together, but not as common. You do not want to stripe SSD's with oitehr-than-SSD's, so what would that really bring to your table?

---

