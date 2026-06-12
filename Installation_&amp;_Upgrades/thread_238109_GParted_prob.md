---
title: "GParted prob"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by carverj on 2006-08-17
HI everyone
Gparted was working fine last time but now it shows both my hard drives as unallocated, whereas a few days ago it would show all partitions.
It is the same when I try to use the Breezy install CD. Oh, and by the way my fstab file hasn't been altered since GParted was working allright.
Could someone please try to help as I am soooo busy and don't have the time to reinstall my current dual boot setup from scratch.
Ta in advance

_________________
My original post regarding this attmpted partition resize
[http://www.ubuntuforums.org/showthread.php?t=233448](http://www.ubuntuforums.org/showthread.php?t=233448)

---

### Post by mlind on 2006-08-17
Does qtparted or parted show the same information? Is your system working otherwise normally except gparted problems?

---

### Post by carverj on 2006-08-17
Yes, It seems fine otherwise.... I could even see the different mounts when browsing whilst running the live cd (which I didn't think you could do)
which leads me to query whether there is a problem with the hard drive or even the MBR !?
How may I check this?

---

### Post by mlind on 2006-08-17
I reckon the problem is with gparted (or parted) instead of corrupted partition table. For me, parted dies with "floating point exception" (which is a known bug). 

While using livecd, you can check filesystems using e2fsck:
```

sudo e2fsck -f /dev/xxx

```
Where /dev/xxx is the filesystem, like /dev/hda1

I dunno how to verify partition table, except using cfdisk/fdisk..
btw. Did you try out qtparted?

---

### Post by carverj on 2006-08-22
Ok, so gave qtparted a try and it found the 2 drives but when I to click on them instead of showing me partitions it gives me the following error message
```
Critical error during ped_disk_new!
```
Could some one point me in the right direction to find the problem with my disk?

Running e2fsch only gave me the following error:
```
ubuntu@ubuntu:~$ sudo e2fsck -f /dev/hda1
e2fsck 1.38 (30-Jun-2005)
Couldn't find ext2 superblock, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/hda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```
Would this be because XP is on the first partition (and therefore is of the wrong filetype to check) or am I in need of a new pair of hard drives?
:roll:

---

### Post by mlind on 2006-08-22
> **carverj said:**
> 
Running e2fsch only gave me the following error:
```
ubuntu@ubuntu:~$ sudo e2fsck -f /dev/hda1
e2fsck 1.38 (30-Jun-2005)
Couldn't find ext2 superblock, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/hda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```
Would this be because XP is on the first partition (and therefore is of the wrong filetype to check) or am I in need of a new pair of hard drives?
:roll:

e2fsck is for ext2/ext3 like its manual page says.. Don't use it with other filesystems.

---

### Post by carverj on 2006-08-29
No worries, managed to wipe the Ubuntu partitions totally with the help of
the PCLinux OS Live CD. Am trying to use an XP CD to fdisk or is it FDISK
/MBR or whatever (so I can boot into the XP partition at the start of the
disk in order to make it larger with Partition Magic).
It seems the Administrator password is not accepted. I assumed the
administrator password in XP would be my password !?
Does anyone know how I can bypass this obstacle?
Cheers all

---

### Post by mlind on 2006-08-29
You can boot into xp's recovery console using xp's cd (then execute fixboot or fixmbr). You can also download win98 bootdisk image from bootdisk.com, boot using it and execute fdisk /mbr.

---

### Post by carverj on 2006-08-29
>  You can boot into xp's recovery console using xp's cd (then execute fixboot or fixmbr). QUOTE]
Yeah, have tried but it asks for Administration password and my password is not working. I didn't think to look into the Administration password as I assumed my account would be sufficient for administration. lol learn the hard way huh?


[QUOTE]You can also download win98 bootdisk image from bootdisk.com, boot using it and execute fdisk /mbr.

Could try this but won't I have the same problem as above or is there a way for me to fix the MBR without entering the windows Administration password?
Thanks for the reply b;y the way

---

### Post by mlind on 2006-08-29
> **carverj said:**
> 
Could try this but won't I have the same problem as above or is there a way for me to fix the MBR without entering the windows Administration password?
Thanks for the reply b;y the way

recovery console boots up from the cd to command-line interface and doesn't require login.
win98 bootdisk doesn't require login either, it boots to "dos". (bootdisk contains the fdisk utility)

---

### Post by carverj on 2006-08-29
NO probs. managed to beat the password problem to find a bigger problem. The partitioner told me that I had only the original 10G avaiable and checking properties in my computer confirmed that my resize (with the PCLinux part tool) to 16 GB hadn't worked. Also crashing everytime despite me nipping in to restore system settings successfully. Is there any hope for this operation or do I need to (finally) bite the bullet and write a new NTFS partition over the top?
Cheers ears

---

### Post by mlind on 2006-08-30
> **carverj said:**
> NO probs. managed to beat the password problem to find a bigger problem. The partitioner told me that I had only the original 10G avaiable and checking properties in my computer confirmed that my resize (with the PCLinux part tool) to 16 GB hadn't worked. Also crashing everytime despite me nipping in to restore system settings successfully. Is there any hope for this operation or do I need to (finally) bite the bullet and write a new NTFS partition over the top?
Cheers ears

Have you tried parted that's on Ubuntu "Alternate" install cd?
It has always worked for me. On windows, I've use Partition Magic in the past, but it's not free product..

---

### Post by carverj on 2006-09-02
oh, ok. maybe I did It wrong with Parted somehow !?
It's strange, I succeeded with Part (PCLinux cd) but didn't succeed if you know what I mean. It hasn't recognized it as one new larger (working) partition. So by increasing the size of the ntfs partition, I have only corrupted the system somehow!! I guess the only solution for me is to choose the ntfs size wisely to begin with & perhaps take a ghost snapshot of my drives !? thoughts?
Thanks

---

### Post by mlind on 2006-09-03
I'm not very qualified to give you anything else except suggestions, but I'd backup the data while it's still there even though partition table may be messed up. Don't mount that NTFS partition, and don't let windows to write to it. It's possible to manually recovery partition table, but easier job would be to get all the data safe and re-create the partition.

There's ugly looking bug that's filed against gparted/parted about NTFS resizing [https://launchpad.net/distros/ubuntu/+source/gparted/+bug/48229](https://launchpad.net/distros/ubuntu/+source/gparted/+bug/48229)


/edit
forgot the link that might actually help
[http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html#troubleshoot](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html#troubleshoot)

---

### Post by cotcot on 2006-09-03
> Ok, so gave qtparted a try and it found the 2 drives but when I to click on them instead of showing me partitions it gives me the following error message

I experienced that gparted or qtparted from ubuntu (or other distros)do not work always. I always use the Gparted LiveCD, which works fine.

---

### Post by Luvis8 on 2006-09-03
Hi There,
I discovered a very simple way to partition the hard drive using WIndows XP.

Step 1: Right click on My Computer
Step 2: Left click on Manage
Step 3: Left click on Disk Management

From there you can repartition and format the drive as you like.
It will format in either FAT32 or NTSF, but don't worry, there is a Wizard program to guide you through the whole thing.

When you install Ubuntu you can simply tell it to install on the drive (i.e. partition) of your choice and tell it to format it.
If I remember correctly, you have to select "manual partitioning" during the installation and you have to select a root drive and a swap drive.
I have used this method to successfully install other Linux Distro's on my computer (Freespire and Xandros).

However I should let you know that I have been experiencing a problem with the Ubuntu install program suddenly "Vanishing" soon after it has installed only 9 percent, but I don't think it is related to the Windows Partitioning. 

I hope this helps.
Please let me know if this works for you.

---

### Post by carverj on 2006-09-06
> I always use the Gparted LiveCD, which works fine.
Cheers, will remember that for next time

> I'm not very qualified to give you anything else except suggestions, but I'd backup the data while it's still there even though partition table may be messed up. Don't mount that NTFS partition, and don't let windows to write to it. It's possible to manually recovery partition table, but easier job would be to get all the data safe and re-create the partition.

[http://mlf.linux.rulez.org/mlf/ezaz/...l#troubleshoot](http://mlf.linux.rulez.org/mlf/ezaz/...l#troubleshoot)


Followed this link/advice and managed to resize the partition further with fdisk. set the hex flag from 1 to 7. still Windows crashing and wondering why it doesn't like me.... um, so you think I should try backing up the whole partition and repartition? I suppose it wouldn't hurt to try...
the problem with that is I won't be able to backup from gui. 
Is there a way I can fully backup this partition from the command line?

---

