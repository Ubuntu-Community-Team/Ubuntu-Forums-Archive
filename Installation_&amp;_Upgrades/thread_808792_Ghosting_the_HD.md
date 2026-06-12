---
title: "Ghosting the HD"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by Matsuri on 2008-05-26
I just recently purchased a Dell Vostro 1510 and I have it dual booted with Ubuntu Hardy Heron and XP. I'm sure at some point in the life of this laptop XP will **** up my laptop and I will need to fix or rebuild it.

I know I can buy/download ghosting software but how exactly does it work? My hard drive is 160GB do I need that exact amount of space to store the Ghost image? Must I have a copy of Ghost or some other cloning software to install the newly created HD Image? Any help would be appreciated.

Matsuri

---

### Post by dmizer on 2008-05-26
here's a start.
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

another one that people have used successfuly:
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

and g4l (ghost for linux) is probably in the ubuntu repositories, but not a lot of documentation exists for it.

---

### Post by secondary on 2008-05-26
Good question, I'm waiting to hear the response(s) too!

..Patrick..

---

### Post by Matsuri on 2008-05-26
It is nice to know I can compress a 1GB to 400mb. While creating the image can I in the same swing compress it. Using Partimage can I preserve the entire hard drive or just the structure of how it was partitioned? Thanks to dell my hard drive has three partitions for whatever stupid reason. A FAT16, FAT32, and NTFS (Main Windows Install). The Ubuntu install is obviously on its default ext3. Will either of these methods work or must I use them in unison with each other?

---

### Post by dmizer on 2008-05-26
in the first link, everything should be done from a root terminal, otherwise the image will not be complete.

dd simply makes a raw image of the disk, so it doesn't really care what is on the disk, partitions or format or otherwise.

partimage does support ntfs: [http://www.partimage.org/Supported-Filesystems](http://www.partimage.org/Supported-Filesystems)

---

### Post by froy02 on 2008-05-27
Imaging a hard drive with Acronis True Image:
It creates an image of your hard drive and saves it as a file into another drive (internal, external or networked).  You can then use the image to restore your hard drive and it would boot up as if nothing happened.  It works with Windows and linux partitions (fat, ntfs, ext2, ext3).  You can use either the bootable CD or install the Windows True Image program in Windows (XP or Vista) and perform the back from it.  It can back up the drive it installed in.  

The hard drive that you restore it to does not have to be the same size as the previous one.  It will restore Windows proportionately as long as there is enough room for all the data in the new drive.  It does not seem to change the size of the Ubuntu  partition and the swap partition in my dual boot desktop. 

I use it to back up my daughter's laptop and my desktop which dual boots XP and Ubuntu.  This way if something goes I do not have to re-install the OS and all the software that were installed. 

 I also use it to try configurations which may cause my OS unstable.  I just back up then if something goes wrong I just do a restore.  Everything will be back  to normal.

Norton Ghost probably does the same thing.

---

### Post by VMC on 2008-05-27
> **Matsuri said:**
> It is nice to know I can compress a 1GB to 400mb. While creating the image can I in the same swing compress it. Using Partimage can I preserve the entire hard drive or just the structure of how it was partitioned? Thanks to dell my hard drive has three partitions for whatever stupid reason. A FAT16, FAT32, and NTFS (Main Windows Install). The Ubuntu install is obviously on its default ext3. Will either of these methods work or must I use them in unison with each other?

You might find backup software already installed there. What is on the Fat32 and Fat16? Can you view them from ubuntu?

I use both Ghost and Acronis. What I do is backup from one partition to another on the same HD. It is faster than to backup from one partition to external usb HD. I then can move to external HD. This may seem like a lot more work but it really is faster.
Most all Linux g4l and PartImage and/or dd and a few other backup schemes are much slower than their commercial counter parts.

---

### Post by dmizer on 2008-05-27
> **froy02 said:**
> Imaging a hard drive with Acronis True Image:
It creates an image of your hard drive and saves it as a file into another drive (internal, external or networked).  You can then use the image to restore your hard drive and it would boot up as if nothing happened.  It works with Windows and linux partitions (fat, ntfs, ext2, ext3).  You can use either the bootable CD or install the Windows True Image program in Windows (XP or Vista) and perform the back from it.  It can back up the drive it installed in.  

The hard drive that you restore it to does not have to be the same size as the previous one.  It will restore Windows proportionately as long as there is enough room for all the data in the new drive.  It does not seem to change the size of the Ubuntu  partition and the swap partition in my dual boot desktop. 

I use it to back up my daughter's laptop and my desktop which dual boots XP and Ubuntu.  This way if something goes I do not have to re-install the OS and all the software that were installed. 

 I also use it to try configurations which may cause my OS unstable.  I just back up then if something goes wrong I just do a restore.  Everything will be back  to normal.

partimage (mentioned earlier) performs all these tasks, with the added advantage of being foss, so it doesn't burn a $50 hole in your pocket.  it's also a part of that knoppix cd you have in your standard pc toolkit.

you can also accomplish the same effect (but greater effort) with dd and gparted.  only exception is that you may have to manually edit grub.

---

### Post by IgnorantGuru on 2008-05-27
I have a new Wikibook on this subject here...
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

---

### Post by Matsuri on 2008-05-27
> **dmizer said:**
> in the first link, everything should be done from a root terminal
I would never have guessed that ;)

Regarding the FAT16 and FAT32 partitions I do not know what is on them. The do not show up under windows or ubuntu as separate "drives". I have yet to call Dell and ask what exactly they are for. From what I have read online they may be partitions used to store finger prints, for the biometrics, or to quickly remove Dell's bloatware. This laptop is Dell's latest model, Vostro 1510 and there is little information out online regarding what they have done to it. I will call sometime tomorrow to inquire about them.

I would use Ghost but I don't really feel like paying 70$ for the software. I just wanted to make sure that with a Ghosting program that the HD image would be compressed into something smaller. I don't have a 160GB of space just laying around to simply store a HD image on it. I also just wanted to make sure that I didn't need said program to install the backup. The methods mentioned above seem to be the best so far as they are free and provide the services I require! :)

---

### Post by dmizer on 2008-05-27
> **Matsuri said:**
> I would never have guessed that ;)

Regarding the FAT16 and FAT32 partitions I do not know what is on them.

these are most likely your recovery partitions.  instead of shipping you a full windows install cd, dell ships you a recovery cd which draws information from these partitions in order to reinstall your windows when things go horribly wrong.

more information here: [http://www.goodells.net/dellrestore/](http://www.goodells.net/dellrestore/)

---

### Post by davec99 on 2008-06-21
One is probably the aformentioned recovery partition containing the software as-shipped and the other - probably the Fat16, is likely some system tools to test hardware, memory, etc. and maybe the software that initiates any restore your might try.  Dell systems are well-documented, so I also recommend you do some searching on their site.  Use the tag number on your case for system-specific searches.

---

