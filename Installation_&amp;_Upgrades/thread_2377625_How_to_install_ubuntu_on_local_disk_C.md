---
title: "How to install ubuntu on local disk C?"
date: 2017-11-15
forum: Installation &amp; Upgrades
---

### Post by napra on 2017-11-15
I can't give screenshoot, but my question is, what must I do to install ubuntu on my local disk C without formatting entire disk or without deleting local disk D data?
In installation process I'm stuck at choosing disk partition. im afraid I will deleting my data by accident.
im stuck in here:
............................................................................
| devices          | Type | Mount Point | Format? | Size |
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
|/dev/sda/blabla|
|/dev/sda/blabla|
|/dev/sda/blabla|
'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
____________________________[new partition] [revert]

what must i do to install ubuntu on my local C system without deleting my local D data?

---

### Post by coldraven on 2017-11-15
You are attempting to make a major change to your computer. Installing a new OS is not a trivial thing so **before you start backup your data.** 
Another option would be to remove the hard drive buy a new one, put it in your computer and install Ubuntu onto it. If you have a desktop then you can add the old drive later on, or (for laptops) buy a cheap enclosure and use the old drive as an external USB drive.

Edit: An enclosure will cost you $10 or less. Here is a typical one for laptop drives
[https://www.amazon.com/Sabrent-Tool-free-Enclosure-Optimized-EC-UASP/dp/B00OJ3UJ2S/ref=sr_1_3?s=pc&ie=UTF8&qid=1510747288&sr=1-3&keywords=hard+drive+enclosure&dpID=31nOEoFxlKL&preST=_SY300_QL70_&dpSrc=srch](https://www.amazon.com/Sabrent-Tool-free-Enclosure-Optimized-EC-UASP/dp/B00OJ3UJ2S/ref=sr_1_3?s=pc&ie=UTF8&qid=1510747288&sr=1-3&keywords=hard+drive+enclosure&dpID=31nOEoFxlKL&preST=_SY300_QL70_&dpSrc=srch)

---

### Post by The Cog on 2017-11-15
I strongly advise taking a backup before partitioning and installing a new OS. Especially if you are not familiar with the install procedure.

If this disk is used for booting Windows, it probably won't be able to after installing Ubuntu. Especially since you want to wipe "disk C" which is where windows is normally installed.

First you need to understand what disks and partitions you have and which Linux name corresponds to which Windows name. If C and D are on the same drive then they will have the same drive name, probably /dev/sda. If you run the Try Ubuntu option in the installer you will be able to open a terminal window and enter the command **lsblk** (short for list blocks) that will show you. Partitions on /dev/sda will be nummbered, possible /dev/sda1 and /dev/sda2 but the order won't necessarily match Windows's letter ordering so you need to use other means (partition size) to figure out which is which.

Then in the installer/partitioned you need to choose the "something else" option (which I guess you have already found). Select the partition that corresponds to C (double-click I think), choose to format it to ext4, don't change the size, and choose the mount point "/". This will leave you without a swap partition unless there was some spare space on the drive where you could create a swap partition (a few gig will do). 

Alternatively you could delete the C partition, and use the space to create a slightly smaller ext4 partition and a swap partition of a few gig. You could use the installer partitioner for this.  I prefer to use gparted to create the partitions, and then just tell the installer which partitions to use, rather than creating and deleting them with the installer..

Alternatively you could just delete the C partition (again, gparted might be better than using the installer for this) and then the installer should offer to use the free space though I've never tried this approach personally. 

Coldraven's suggestion of using a different disk is the safest approach of course. You can copy the data over once Ubuntu is installed and then have a spare disk.

---

### Post by yancek on 2017-11-15
Just to clarify what your intentions are, you cannot install any Linux system on a windows formatted partition which is what your "C" would be.  If you install Ubuntu there your windows will be overwritten/gone.  So if you want Ubunt and windows, you will need to post the information requested above and you will probably need to shrink one of your windows partitions to create unallocated space for Ubuntu.  This should be done from windows Disk Management.  Please clarify what exactly your intentions are.

---

### Post by napra on 2017-11-15
thanks for the answer guys, I just want to install ubuntu only, so i no need dualboot :D
here, please take a look at attached file, is it correct setting?
I want formatting my local C but want to keep my local D data.
in windows Im usually formatting local C to clean install, so i want do same thing to ubuntu, i want clean install ubuntu on my local C without formating entire disk.
in attached file based on its size, /sda2 is my local C, and /sda4 is my local D

---

### Post by yancek on 2017-11-15
If you want to overwrite the windows system partition and install Ubuntu to it, the settings in your last post image are correct.  That is if sda2 is your "C" partition with windows system files.

---

### Post by The Cog on 2017-11-16
I agree that sda2 and sda4 will be C and D. sda4 is larger so you can use the size to tell which is which. So you want to install to sda2 and not do anything with sda4 (leave it unused for now). I can't imagine what sd1 and sda3 are. They are very small but do appear to be formatted with NTFS. I would be inclined to leave them alone.

---

