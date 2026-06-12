---
title: "No root file system is defined partitioning issue"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by Raventara on 2010-12-02
So I keep getting this error from the 10.10 installer:

"No root file system is defined. Please correct this from the partitioning menu."

However the partitioning menu shows no disks or partitions at all.

The disk browser can however see and mount both partitions from my disk.

It is a terabyte SATA drive and the bios has been set to IDE.

It has 2 partitions with windows installed on the first partition.

Gparted can see both partitions but claims it cannot find the mount point of the second partition. (both are NTFS)

I have attached a screenshot.

Can anybody give me some advice on how to proceed from here so I can install Ubuntu.

---

### Post by libssd on 2010-12-02
I think the problem is that both partitions are NTFS. You could delete the non-Windows, then create a new partition using ext4 filesystem, and / as the mount point. Ubuntu will run fine in as little as a 16gb partition, although since you have so much space, you can afford to give it more. Free space can always be re-used at a later date.

---

### Post by oldfred on 2010-12-03
Is the 2nd NTFS empty? If so I would just delete it. The installer may not let you but you should be able to go into the liveCD mode and open gparted. You used to not be able to do any NTFS partitioning while in the installer, just shrink. The lock tells you that you cannot change it.

While in gparted I would just create the partitions for Ubuntu and then use manual install to select them & format them. I would keep the NTFS partition for shared data, but whether it needs repair or can be deleted and recreated I do not know.

If creating partitions in advance this is one choice.
Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up. And if dual booting with windows a shared NTFS partition is also recommended. 

Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by Raventara on 2010-12-03
Well, I guess I'll have to shrink the partition in Windows first and then use GParted to create the partitions as you've described. I'll check back in here when I'm done.

Thanks for the help guys...

---

### Post by libssd on 2010-12-03
Beautiful post, Oldfred. You covered everything in detail, and why.

---

