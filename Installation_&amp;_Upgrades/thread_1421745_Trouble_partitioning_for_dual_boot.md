---
title: "Trouble partitioning for dual boot"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by Chris Grk-O-Matic on 2010-03-04
I probably butchered this but can I get some advice on my partitioning scheme?

I did not know what to do about the 200meg bootloader partition, i.e. 'mount point'.

Can someone steer me in the right direction please?




Regards to all
Chris

---

### Post by mikewhatever on 2010-03-04
It depends on what you want it for. I guess you want it as a boot partition, so that the mount point should be just **/boot** .

---

### Post by adam22 on 2010-03-04
I don't have a boot partition, I've never even seen one. If you have a Windows disc, delete it and see what happens, if not, it might not be worth the risk.

I'm not sure what you have going on there. If you did a "default" partition setup with Ubuntu, for whatever, reason, it sticks everything in one extended partition. What I would do is make 3 primary partitions. A 1 GB SWAP, a 6 GB / (root) partition, and then a 8 GB /home partition. This way, if you want to install a new version, you will only have to install the / partition, leaving themes, documents, etc. in tact that are located in the /home partition.

As for that NTFS...I assume that's Windows? It's empty...did you mess up Windows or just not install it yet?

---

### Post by Chris Grk-O-Matic on 2010-03-05
So I'm going to start from scratch. I want to partition (using Gparted) for Windows and Debian and be able to share the files between them as well.
 
I did a lot of searching on this topic and it's been hard to differentiate between outdated methods and the new, better methods.
 
I came upon this [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) and it seems FS-Drive is the way to go. The author's partition scheme looks like this:
 
NTFS
Ubuntu /home - shared data (Ext3)
Ubuntu / (Ext3)
Swap
 
 
Assuming I should partition emulating the above mentioned scheme: 
I know how to create 4 partitions, but don't know which partition to put the boot flag, how to make a partition root, and how to make a partition home. Is it in the labeling that I'm supposed to designate / and /home?
 
Also, I have about 13gigs of personal data created in Windows. Is it better to size the NTFS partition to accomodate this or use the /home partition?

---

### Post by Sef on 2010-03-05
> NTFS
Ubuntu /home - shared data (Ext3)
Ubuntu / (Ext3)
Swap
 
 
Assuming I should partition emulating the above mentioned scheme: 
I know how to create 4 partitions, but don't know which partition to put  the boot flag, how to make a partition root, and how to make a  partition home. Is it in the labeling that I'm supposed to designate /  and /home?
 
Also, I have about 13gigs of personal data created in Windows. Is it  better to size the NTFS partition to accommodate this or use the /home  partition?

1) Boot Flag - Put it in Ubuntu

2) Make a partition root - When setting up the partition, you will have the option what to make it.  I believe that is mount.  There will be a list and you simply highlight, what you want the partition to be.  Root Partition = / ; Home Partition = /home ; Swap Partition = /swap

3) I would make the home/shared partition NTFS.   Ubuntu can read and write to NTFS, if NTFS configuration tool is downloaded from the Software Center.

---

### Post by Chris Grk-O-Matic on 2010-03-05
When formatting the partitions, it gives me the choice of Primary, Logical, or Extended. Which do I choose for the different partitions?

---

### Post by gordintoronto on 2010-03-05
If you are starting from scratch, the easiest thing is to remove all partitions, then install Windows giving it enough space for your data files. Then install Ubuntu, with a / partition (root) of at least 10GB (I picked 30 GB on my system, with a 640 GB drive), a swap partition as large as memory, then a /home partition with the remaining space. You do not have to set up the partitions ahead of time, it can only cause problems.

---

### Post by mikewhatever on 2010-03-05
> **Chris Grk-O-Matic said:**
> When formatting the partitions, it gives me the choice of Primary, Logical, or Extended. Which do I choose for the different partitions?

Windows needs to be on a primary partition, otherwise, it might not work. Ubuntu is not as picky, so it doesn't matter. In you particular case, you can make all four partitions primary or make Windows primary and the rest logical. Just a general note, you can't have more then four primary partitions on an hdd.

---

### Post by Chris Grk-O-Matic on 2010-03-06
I had success installing and dual booting XP and Debian. 

Just that, when it came to installing Debian, it didn't give me the choice of formatting my home/shared partition to NTFS. So I made it Ext3.

If I change the home/shared partition to NTFS now using gparted, will it screw things up?

---

### Post by oldfred on 2010-03-06
Yes.

Ubuntu's files have permissions and ownership that NTFS does not support. If you want to share files create a new NTFS partition and put some data in that.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by Chris Grk-O-Matic on 2010-03-10
Could it be suggested since that Ext3 partition would be rendered useless, to shrink it down, and then use the empty space to add the new NTFS partition for Windows/Linux sharing?
 
I tried to do that, but then I couldn't add another partition because I already created 4 primary partitions. 
 
Can anyone suggest a workaround for this?

---

### Post by Chris Grk-O-Matic on 2010-03-15
Can anyone chime in on this? It would be much appreciated.

---

### Post by srs5694 on 2010-03-15
> **Chris Grk-O-Matic said:**
> Could it be suggested since that Ext3 partition would be rendered useless, to shrink it down, and then use the empty space to add the new NTFS partition for Windows/Linux sharing?
 
I tried to do that, but then I couldn't add another partition because I already created 4 primary partitions.

The Master Boot Record (MBR) partitioning system has a limit of four primary partitions. One of these may be an extended partition that serves as a placeholder for an arbitrary number of logical partitions. If you're bumping up against that limit you have two options:


[list]
[*]Convert one or more partitions from primary to logical. It's not generally easy to convert existing partitions, though; I don't believe GParted supports direct primary-to-logical conversions at all, for instance. It sounds like you're still laying out your partitions, though, so you should be able to start over.
[*]Switch from the MBR partitioning scheme to one that doesn't have this limit. The only practical choice on x86 or x86-64 systems is the GUID Partition Table (GPT) scheme. This is a good choice for a Linux-only system or a system that dual boots with OS X, FreeBSD, or some other GPT-friendly OS; however, Windows won't boot from a GPT disk unless the computer has EFI support in its firmware, and such support is still rare. There are workarounds for this limitation, but they're ugly and potentially dangerous.
[/list]


Overall, your best bet is to delete all your partitions, create a primary partition for Windows (since it must boot from a primary partition), create an extended partition to cover the rest of the disk, and populate the extended partition with logical partitions for everything else. If I've misunderstood and you can't delete some or all of your partitions, you may need to delete just some of your existing partitions. As long as you keep it to three or fewer primaries, you're set.

---

### Post by oldfred on 2010-03-15
Post your partitions:

```
sudo fdisk -l
```

---

