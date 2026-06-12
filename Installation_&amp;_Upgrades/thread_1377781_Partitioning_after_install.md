---
title: "Partitioning after install"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by shuu on 2010-01-10
The noob again, heh. Well, I was so eager to try out Ubuntu I disregarded the consequences of installing it and particularly the benefit of installing it on a sized partition. I've got two physical drives, one reserved for Windows and everything that is "Windows only" .. while I have been using the other, up until now, to store programs, games, films, the works.. basically things that I'd like to keep if I were to reformat Windows or change OS. Now, I installed Ubuntu onto that other physical drive without making a seperate partition, and bear with my I am no computer genious (at least not yet). This doesn't have any critical consequences, as Windows is still my primary OS, and the files on the secondary drive is perfectly accessible from here. However, when running Ubuntu, I have access to the Ubuntu installation only, ie the 40GB I reserved, when installing, for Ubuntu and "Ubuntu only" stuff. Of course, I can also access the primary HDD, ie the Windows partition. What I can't access is the 460GB of space and files on the secondary HDD, the Ubuntu partition. 

In short, I need to make (at least) two partitions out of the secondary physical drive, one that is 40GB for the Ubuntu installation, and one that is 460GB for everything else. That way, as far as I know, I'd be able to access the partition of 460GB as well as the one of 40GB, right? Instead of the 460GB being completely invisible. Thing is, you can't just say "hey, move Ubuntu into a partition of 40GB and make a partition out of the rest" and it will just work. I'm curious if it is possible to make partitions at all without deleting what's within the original partition.

It's not a dire need, as I could "just" move the 100GB of files already on the D: drive over to the C: drive temporarily, wipe it and make partitions out of it, and then proceed to install Ubuntu once again into the correct partition and move the files back over to the remaining partition.

Suggestions?

---

### Post by michy99 on 2010-01-10
Before anything else, please clear up one thing. Did you install Ubuntu by booting from the CD, or did you install it while you were running Windows? Also, can you open a terminal (Applications->Accessories->Terminal) and enter this command. Note that it is a lower-case L at the end and not a one.```
sudo fdisk -l
```Post the output from that command.

---

### Post by phillw on 2010-01-10
Hi there !!!

You say that you installed ubuntu onto the 'other' hard drive without making a partition ?

Please explain how. Did you use Wubi, or did you tell Ubuntu to use the entire disk ?

Please clarify .. C: = 1 physicall hard drive and   D: = a second physical hard disk ?
which you are calling 'other' ?

If so, for ubuntu - it will see them as
c: = /dev/sda
d: = /dev/sdb

When you're in Ubuntu, could you post back the response to :
```
df -H
```
and
```
sudo fdisk -l
```

Thanks,
Phill.

---

### Post by oldfred on 2010-01-10
You can use gparted to resize partitions if there is enough space. It can be a slow process since it has to move data and verify it. There always is some risk of loss of data in any process  like that but it is usually user error (oops I did not mean to delete that:)). 

I ran windows on one drive and Ubuntu on the other for 3 years. I did create a shared partition (then FAT but now NTFS) for photos, thunderbird  & firefox profiles and some other data. That way I was able to have the same data in both systems. I now have a /data partition that is ext3 for Ubuntu data only.

You also will want a swap partition slightly larger than your memory if you hibernate or at least 2GB. You should also plan on a /home directory for Ubuntu data and hidden settings so if you want to upgrade you can do a clean install without losing your settings.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by shuu on 2010-01-10
I'll run those applications first thing tomorrow morning guys, right now I'm on Windows and I'm going to catch some sleep after this post.

I'll clear up a few things though.

C: is a physical drive, 500GB, with Windows Vista 32-bit installed.
Referenced as primary HDD or Windows partition.

D: is a physical drive, 500GB, with Ubuntu 9.10 64-bit installed (via WUBI)
Referenced as secondary HDD, Ubuntu partition or "the other physical HDD"

When I ran Wubi I defined 40GB space for the installation, and I installed that on D:.

Before I installed Ubuntu, there were already 100GB of files on D:.

When I run Ubuntu, I see the Windows drive, 500GB, my DVD-ROM and another drive (named something identifying which I can't recall right now) on which there are Ubuntu files, that claims to be sized 40GB. The remaining 460GB of space, whereof 100GB is files, on D: drive does not appear to be accessible (at least not through the 'Computer' file view Places>Computer and that's all I know about).

I want to access those 460GB on the D: drive, and not only the 40GB reserved for Ubuntu. I assume the only way to do that, is by making it into two partitions. One for Ubuntu and one for the files.

---

### Post by michy99 on 2010-01-10
The drive which has Ubuntu on it is under Computer->host. Or else Computer->File System->host.

---

### Post by shuu on 2010-01-11
Okay, here are the print-outs:

```
shuu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf3c6fc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf3c6fc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512    7  HPFS/NTFS


shuu@ubuntu:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/loop0              31G   3.4G    26G  12% /
udev                   2.1G   267k   2.1G   1% /dev
none                   2.1G   1.2M   2.1G   1% /dev/shm
none                   2.1G    91k   2.1G   1% /var/run
none                   2.1G      0   2.1G   0% /var/lock
none                   2.1G      0   2.1G   0% /lib/init/rw
/dev/sdb1              501G   142G   359G  29% /host
none                    31G   3.4G    26G  12% /var/lib/ureadahead/debugfs

```

It appears to me both physical HDDs are visible and accurate. sda1 is C: and sdb1 is D: .. however, under Places>Computer Iùve got 500GB Hard Disk Windows, CD/DVD Drive, Generic - Multi-card and Filesystem. In file system there is merely 24GB of free space, which tell me those 360GB of free space outside the 40GB part that Ubuntu is installed onto (a part, not a partition) is not apparent to the File Browser.

---

### Post by shuu on 2010-01-11
(Pardon the double post)

Aight, I found my full HDD now, through the *host* folder. I've never really had a Linux system myself for personal use, so I've never actually studied how things are sorted within, and I sort of assumed it was a lot similar to Windows. Anyway, I've got access to all files now, so there's no urgent need to do any partitioning. However, I'll probably be cleaning up everything and doing a clean reinstall in a while, and I'll make sure I make appropriate partitions that time 'round.

I'll just clarify though, when I will make partitions, I'll need three partitions for Ubuntu, right?

For example: 40GB partition on which I install Ubuntu, 455GB partition for files accessible by all OSes (ie NTFS file system) and a 5GB swap partition (I've got 4GB RAM).

As for the other physical drive, I'll be making a 100GB partition for Windows and 400GB for files accessible by all OSes.

So in Ubuntu terms:

sda1 - 100GB - NTFS, Windows installation
sda2 - 400GB - NTFS, files
sdb1 - 040GB - ext#, Ubuntu installation
sdb2 - 455GB - NTFS, files
sdb3 - 005GB - swap

Curious about how the file system for the Ubuntu partition is set, as right now my impression is that it's in ext2, while it should be in ext3 or ext4?

Also wondering about how I set up the swap partition, there was some info about logics and that it needed to be slightly larger than my RAM and it has to be the end of the physical drive (hence sdb3 and not sdb1 for instance).

---

### Post by darkod on 2010-01-11
If you are doing clean reinstall later I would recommend to think about full ubuntu install. On its own partition with its own filesystem.
What you have now is only wubi, sort of virtual ubuntu. Looking from inside wubi, it looks like full ubuntu, but from outside you can easily see it's just virtual on ntfs partitions. Your fdisk result confirms this, you can see you have both drives with ntfs partitions on it.
At the moment wubi is working on ntfs partition creating virtual vision of ubuntu. Full ubuntu on its own ext4 partition will run much faster and better, not to mention that right now if your windows breaks down, you probably won't be able to boot wubi too because it's inside it.
With proper dual boot you can usually boot the other OS if one breaks down.

---

### Post by oldfred on 2010-01-11
I agree with darko. Wubi is fine if you are new to ubuntu and want to try it out without having to repartition and it is faster than running just from the CD. But it is still on a windows system, if windows breaks it can be difficult to recover data from the wubi root file. 

Once you decide you want to use ubuntu at least some of time on a regular basis it is better to have a true dual boot with ubuntu in a separate partition.

---

### Post by shuu on 2010-01-11
Yes, I intend to do a full Ubuntu install after I clean things up so I can partition sdb correctly. Still haven't had this confirmed though:

> 
Is this an appropriate way of partitioning?

sda1 - 100GB - NTFS, Windows installation
sda2 - 400GB - NTFS, files
sdb1 - 040GB - ext#, Ubuntu installation
sdb2 - 455GB - NTFS, files
sdb3 - 005GB - swap

Also wondering about how I set up the swap partition, there was some info about logics and that it needed to be slightly larger than my RAM and it has to be the end of the physical drive (hence sdb3 and not sdb1 for instance).

I've got two 500GB HDDs, 4GB RAM.

---

### Post by SecretCode on 2010-01-11
> **shuu said:**
> Still haven't had this confirmed though:

Is this an appropriate way of partitioning?

sda1 - 100GB - NTFS, Windows installation
sda2 - 400GB - NTFS, files
sdb1 - 040GB - ext#, Ubuntu installation
sdb2 - 455GB - NTFS, files
sdb3 - 005GB - swap

Also wondering about how I set up the swap partition, there was some info about logics and that it needed to be slightly larger than my RAM and it has to be the end of the physical drive (hence sdb3 and not sdb1 for instance).

It looks fine to me. I would just suggest putting everything after the first partition into "logical" partitions, which in linux numbering would mean:

sda1 - 100GB - NTFS, Windows installation
sda5 - 400GB - NTFS, files
sdb1 - 040GB - ext4, Ubuntu installation
sdb5 - 455GB - NTFS, files
sdb6 - 005GB - swap

Putting swap at the end of the drive is conventional but I don't think it's important.

ext4 is good for the ubuntu installation, but ext3 would also be fine.

---

### Post by shuu on 2010-01-11
> **SecretCode said:**
> It looks fine to me. I would just suggest putting everything after the first partition into "logical" partitions, which in linux numbering would mean:

sda1 - 100GB - NTFS, Windows installation
sda5 - 400GB - NTFS, files
sdb1 - 040GB - ext4, Ubuntu installation
sdb5 - 455GB - NTFS, files
sdb6 - 005GB - swap

Putting swap at the end of the drive is conventional but I don't think it's important.

ext4 is good for the ubuntu installation, but ext3 would also be fine.

How do I do these logical partitions, and why is it better? I'm pretty much a complete beginner when it comes to hardware level, and the base structures of OSes, etc. I only now, after installing Ubuntu, realised the benefit of partitioning a HDD. I've always used one partition per HDD.

---

### Post by oldfred on 2010-01-11
Lots of info on partitioning. You only need root (/) and swap. With 4GB of memory swap will rarely be used. Swap is overflow for running lots of large programs at once or for hibernating. With 4GB it becomes difficult to run enough programs to use much swap. Your 5GB for swap is plenty. Many recommend a separate /home but you then have to partition in advance and use manual install to choose what partitions to use where. If you have a separate /home root can be 10-20GB and home all the rest that you want to allocate.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

