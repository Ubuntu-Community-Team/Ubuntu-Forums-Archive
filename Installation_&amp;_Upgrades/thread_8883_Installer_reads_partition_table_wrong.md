---
title: "Installer reads partition table wrong"
date: 2004-12-22
forum: Installation &amp; Upgrades
---

### Post by m29389 on 2004-12-22
Hi

I have been using linux as my primary OS for a couple of years now and thought I would quickly check out Ubuntu to see what everyone is talking about.

Unfortunateley there is a problem when I reach the partitioning section of the installation.  My hard disk is shown as having one 80GB FAT16 partition.  What it actually has is 1x25GB-NTFS 1x5GB-FAT32 1x20GB-ReiserFS 1x512MB-swap and 1x5GB-Reiserfs (or something like that).  The rest of the drive is empty, unallocated space.

I would appreciate it if anyone know why this is happening.

I have run testdisk and re-written the partition table with cfdisk from my slackware 10 (with kernel 2.4.28) setup which reads the partition table fine. Slackware and Windows XP both run fine on this setup.

I am trying to install on an 80GB Seagate Baracuda SATA drive through a Silicon Image 3112 sata raid controller card using an ubuntu cd.  But if there were a problem with the hardware I wouldn't expect to see any partitions, or no disk at all, not just the wrong information.

Why might Ubuntu's installation process not read my partition table right?

Thanks for any help.

---

### Post by ecc6 on 2004-12-22
[QUOTE=m29389]Hi

I have been using linux as my primary OS for a couple of years now and thought I would quickly check out Ubuntu to see what everyone is talking about.

Unfortunateley there is a problem when I reach the partitioning section of the installation.  My hard disk is shown as having one 80GB FAT16 partition.  What it actually has is 1x25GB-NTFS 1x5GB-FAT32 1x20GB-ReiserFS 1x512MB-swap and 1x5GB-Reiserfs (or something like that).  The rest of the drive is empty, unallocated space.

I would appreciate it if anyone know why this is happening.

I have run testdisk and re-written the partition table with cfdisk from my slackware 10 (with kernel 2.4.28) setup which reads the partition table fine. Slackware and Windows XP both run fine on this setup.

I am trying to install on an 80GB Seagate Baracuda SATA drive through a Silicon Image 3112 sata raid controller card using an ubuntu cd.  But if there were a problem with the hardware I wouldn't expect to see any partitions, or no disk at all, not just the wrong information.

Why might Ubuntu's installation process not read my partition table right?

Thanks for any help.[/QUOTE]
 I get this exact same error. I also get it with the new Debian installer, which the ubuntu installer is based on. I tried posting a bug report on it through debian but it's already been reported ([here](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=242114)). The problem is obviously with parted, because when I switched over into a console with the debian installer and tried to run parted it just complained about invalid partition table or something.

Anyway, ubuntu looks nice but I can't hose my windows partition just to install it. The crazy thing is that fdisk and cfdisk show the partitions correctly, as well as the version of parted contained in knoppix (1.6.9, i believe). Although it gives some complaint about disk geometry. Anyway, this is a definite bug (IMHO) and I'm not sure how to get around it, although it seems like it should be possible if you take care of partitioning first and somehow just point the installer to the right partition. I do have an extended partition with some other logical partitions in it but I don't know why that would create problems. I initially used an old version of partition magic and have since used the windows disk management tool to do partitioning. Something must be wrong with our partition tables.

---

### Post by m29389 on 2004-12-22
Thanks for the response.  I see what you mean about the bug report for parted.  That might narrow things down a bit.

At least I know that i'm not alone... it is frustrating not being able to install what looks like an interesting distro.

If i find a fix I will post it here.

---

### Post by Xian on 2004-12-22
[QUOTE=ecc6]The crazy thing is that fdisk and cfdisk show the partitions correctly, as well as the version of parted contained in knoppix (1.6.9, i believe). Although it gives some complaint about disk geometry. Anyway, this is a definite bug (IMHO) and I'm not sure how to get around it...[/QUOTE]
This is generally caused by the disk geometry being inconsistent with the bios settings. It often is the result of using a partitioning application that does not take these parameters and use them correctly when writing to the HD. It is usually not seen in the *fdisk tools, and unless an installer uses the parted software it will often go completely unnoticed. They may be some professional fixes, but it is not unusual for the disk to need to be partitioned from scratch. 

As to why parted does not "ignore" the problem like *fdisk is another issue.

---

### Post by ecc6 on 2004-12-22
[QUOTE=Xian]This is generally caused by the disk geometry being inconsistent with the bios settings. It often is the result of using a partitioning application that does not take these parameters and use them correctly when writing to the HD. It is usually not seen in the *fdisk tools, and unless an installer uses the parted software it will often go completely unnoticed. They may be some professional fixes, but it is not unusual for the disk to need to be partitioned from scratch. 

As to why parted does not "ignore" the problem like *fdisk is another issue.[/QUOTE]
 That makes sense, as I said I changed my partitions with an old version of Partition Magic and the windows Disk Management tool so I wouldn't be surprised if something went slightly awry there. But the thing that confuses me is that when I used parted on knoppix these partitions all showed up. Also everything works fine with the system, I had SUSE installed before and if a linux distro uses fdisk for partitioning it works fine. There should be a workaround for this.

---

### Post by Xian on 2004-12-23
[QUOTE=ecc6]But the thing that confuses me is that when I used parted on knoppix these partitions all showed up. Also everything works fine with the system, I had SUSE installed before and if a linux distro uses fdisk for partitioning it works fine. There should be a workaround for this.[/QUOTE]
I am curious if the version on Knoppix is different from the one used on the Debian installer. It would be nice if the installer would option out to *fdisk if and when parted encounters what it believes to be disk errors. That is not a real fix but it would at least allow many users with corrupted disk geometries to complete the install process.

---

### Post by m29389 on 2004-12-24
Well I said I would post if I found a solution so even though it was the result of an accident, this is how I got it sorted:

Whilst having a look at FreeSBIE, the FreeBSD live cd, I thought I would see what thier tools made of my partition tables.  Somehow (I must have given the wrong option to fdisk or something (I was too tired!!)) I managed to rewrite my partition table to read as one 80GB ext3 partition labeled FreeBSD.

Anyway using testdisk, on the latest INSERT live cd, I reconstructed my previous partition table and wrote it back onto the disk.

And that's it.  I thought that it would be worth trying ubuntu again and it installed fine, recognising my partition table as I would have expected it to.

a happy accident

---

### Post by cocoss1424 on 2007-05-15
> **m29389 said:**
> Thanks for the response.  I see what you mean about the bug report for parted.  That might narrow things down a bit.

At least I know that i'm not alone... it is frustrating not being able to install what looks like an interesting distro.

If i find a fix I will post it here.


[pollution blood pressure food science physics build](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/index.php)

---

