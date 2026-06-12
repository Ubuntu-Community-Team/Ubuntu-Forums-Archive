---
title: "Ubuntu will not install from USB"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by djshortsleeve on 2011-03-12
I have yet to hear from someone who has installed from USB.

Its as if it gets flustered thinking it is being told to install onto the USB.  How can I direct it to install onto hard drive?

---

### Post by Rubi1200 on 2011-03-12
Please provide us with more information if you expect us to help.

what version of Ubuntu, how did you put it on the USB stick, what are the computer specs.?

---

### Post by Hedgehog1 on 2011-03-12
Am I missing something?  Didn't we do this a few days ago?

> **djshortsleeve said:**
> ubuntu@ubuntu:~$ sudo fdisk -l
 
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
 
[COLOR=red]**Disk /dev/sda doesn't contain a valid partition table**[/COLOR]
 
Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders
Units = cylinders of 1892 * 512 = 968704 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18
 
Device Boot Start End Blocks Id System
/dev/sdb1 * 5 4138 3909696 c W95 FAT32 (LBA)
 
What does this mean?
 
djshortsleeve,
 
Your situation is that your first 640 gig hard drive has no partitions laid out at all. It is completly blank.
 
Please reinstall, choose the manual install method and make 3 parititons:
/dev/sda1 20 gigs: ext4 '/'
/dev/sda2 5 gigs: Swap
/dev/sda3 'the rest of the disk space' ext4 '/home'
or (/dev/sda3 **130 gigs** if 'the rest of the disk space' fails)
 
 
***The Hedge***
 
:KS

---

### Post by garvinrick4 on 2011-03-12
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by djshortsleeve on 2011-03-12
I attempted to partition the disk but to no avail.

I have now moved on to using a CD.  This appears to go further, but stops where I am asked my time zone.  A warning appears that the drive contains a GPT partition table and I am asked YES or NO. 

Both selections do nothing.

---

### Post by Rubi1200 on 2011-03-12
If you are on the LiveCD, go to Applications > Accessories > Terminal and post the output of the following command:

```
sudo fdisk -lu
```

---

### Post by oldfred on 2011-03-12
You cannot mix MBR (msdos) and gpt partitioning schemes. (although Macs do in a way to make windows work in gpt). If you have left over gpt info and want MBR you have to remove the gpt info.

When formating a new drive the first choice is gpt or MBR. If it will always be a Linux drive then gpt is better but only slightly with BIOS. Most users currently have MBR which is the old standard for the last 20 years. And windows with BIOS will not boot from a gpt drive. Windows will read data from gpt.

Remove old parts of gpt
[http://ubuntuforums.org/showpost.php?p=10022223&postcount=34](http://ubuntuforums.org/showpost.php?p=10022223&postcount=34)

Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

---

### Post by djshortsleeve on 2011-03-12
Installation works properly with CD, but I need to properly allocate drive space.

---

### Post by djshortsleeve on 2011-03-12
Now I get an error telling me there is a GPT partition table.  This was a brand new drive which I have formatted like this:

[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/2/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/2/)

---

### Post by wilee-nilee on 2011-03-12
> **djshortsleeve said:**
> Now I get an error telling me there is a GPT partition table.  This was a brand new drive which I have formatted like this:

[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/2/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/2/)

Since your still getting a gpt error look closer at post 7.

---

### Post by srs5694 on 2011-03-12
djshortsleeve, we're pretty much guessing here because you haven't provided any real data about the current state of your disks. Please boot using [PartedMagic](http://partedmagic.com/) or [System Rescue CD](http://www.sysresccd.org/) and type the following two commands into a Terminal window:

```

sudo fdisk -lu
sudo gdisk -l /dev/sda

```

Note that those are lowercase letter "L"s in "-lu" and "-l", not digit "1"s. If you've got more than one physical hard disk, repeat the second command for each disk (/dev/sdb, etc.). If gdisk asks whether to use MBR or GPT data, tell it to use GPT data. Note that gdisk isn't installed in the Ubuntu live CD by default, which is why I asked you to use System Rescue CD or PartedMagic. Alternatively, you could download and install gdisk from [its Sourceforge download page.](https://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.0/gdisk-binaries/) However you do it, post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. These commands will provide us with the information we need to determine what's going on and advise you without as much guessing.

---

### Post by djshortsleeve on 2011-03-13
> **wilee-nilee said:**
> Since your still getting a gpt error look closer at post 7.

I have installed successfully using the partitioning listed above.

Thanks for your help.

---

