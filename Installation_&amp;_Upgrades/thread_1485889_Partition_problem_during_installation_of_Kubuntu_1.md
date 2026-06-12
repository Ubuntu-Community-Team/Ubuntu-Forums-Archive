---
title: "Partition problem during installation of Kubuntu 10.4 (Win7 pre-installed)"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by Shirin10 on 2010-05-17
Hello,

New to Linux here,

I am desperately attempting to install Kunbuntu (10.4 LTS) for weeks on my new Netbook (MSI X340) on which Windows 7 Home Prem is already pre-installed.

I wish to keep Win7 and install Kubuntu in dual-boot.  I have created a "Live-CD" on a USB key using unetbootin-windows-436 as the netbook does not have a CD player.

After the first 3 installation steps (language, time and keyboard), the 4th partition step causes problems.

Problems
- the option "install side-by-side" does not appear
- The Kubuntu install software shows that there are already 4 partitions.
(see [http://www.hiboox.fr/go/images-100/dd-kubuntu-100514b,39a01dbcca2810ca07d7147c77cbc1e7.jpg.html](http://www.hiboox.fr/go/images-100/dd-kubuntu-100514b,39a01dbcca2810ca07d7147c77cbc1e7.jpg.html)) I have read that there cannot be more than 4 primary partitions.  I suppose this is the reason for which an additional partition for Linux cannot be created.
- under Win 7, only 3 partitions are shown ???!?
(see [http://www.hiboox.fr/go/images-100/dd-win-100514,74a52ba50b07f3da416286b3b8bd02e6.jpg.html](http://www.hiboox.fr/go/images-100/dd-win-100514,74a52ba50b07f3da416286b3b8bd02e6.jpg.html))


Partitions
- 1 MB, OS_Install
- 10 GB, recovery, NTFS
-  100 MB, system, NTFS
- 288 GB, disk C: (originally named  OS_install), NTFS (in which Win7 is pre-installed, as far as I understand).

I am completely confused.
I intended to copy and store one of the partition, in order to make room for the Linux partition, but I do not see how.

I would greatly appreciate a step-by-step help.

---

### Post by darkod on 2010-05-17
What does the 1MB partition have on it? If win7 can't see it or open it, ubuntu might be able to do it when booted in Try Ubuntu mode.

I guess nothing important in those 1MB. You could delete it and a new partition will be able to be created.

You would still need to make space for ubuntu, I guess you planned to shrink C:. Do that from win7 Disk Management (don't use the side-by-side option). The shrink will create unallocated space, leave it as such.
Then use the Use Largest Available Free space option in the ubuntu installer. It will be available when you have unallocated space on the hdd.

This is exactly why I hate the 100MB boot partition win7 creates. It is absolutely unnecessary and it's a waste of primary partition.

---

### Post by Shirin10 on 2010-05-17
Sincere thanks for your very prompt reply.


>What does the 1MB partition have on it?
I actually do not know.  Gparted says it is "OS_install".  I am a bit afraid to delete partitions as I do not know how to copy/save partitions (I only have one hard disk, no CD writer, disk copy softwares that I know cannot copy to USB keys or SD memory). 
I apologise to ask again: is it safe to delete this 1MB partition?

> You would still need to make space for ubuntu, I guess you planned to  shrink C:
Yes, I did. Again, a beginner's question: are 100 GB sufficient, knowing that all "sub-partitions" will be there?


> This is exactly why I hate the 100MB boot partition win7 creates.
I hate Win all together for all the trouble and money loss they caused me.  I am desperately attempting to depart from them, although it seems that some software are better run from Win. This is my attempt to migrate.

I sincerely appreciate your help AND any step-by-step guidance.  I am a complete beginner.
Regards,

---

### Post by srs5694 on 2010-05-17
I wouldn't be so quick to delete the 1MB partition, at least not until I'd identified what it actually is. I recommend trying the following commands from Linux (using an Ubuntu live CD, [PartedMagic,](http://partedmagic.com) [System Rescue CD,](http://www.sysresccd.org) or something similar):

```

sudo fdisk -lu
sudo blkid /dev/sda1

```

The "sudo" part may be unnecessary in some environments. Note that it's a lowercase "L", not a digit "1", after the dash in the fdisk command. Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. The first command identifies some low-level partitioning information, and the second peeks inside the mystery partition to try to identify any filesystem or other data it might contain.

Your /dev/sda2 is almost certainly a partition that holds an equivalent of Windows installation DVDs. Computer makers have been chewing up 10GB of their customers' disk space for this of late because they're too incredibly cheap to provide their customers with a $1 DVD with their $500 computer purchases. There's usually a utility in Windows that you can use to burn DVDs from the material in this partition. I recommend you do so -- twice, since recordable DVDs aren't as reliable as pressed DVDs. While you act as a human disc-swapping machine, you might as well write a letter to the manufacturer telling them what you think of this practice. I *think* that when you're done, it's then safe to remove this 10GB partition; however, I can't make any promises on this score. (FWIW, I created these discs and then deleted this partition on my latest computer purchase, so at the very least I'm following my own advice, even if it turns out to be bad advice.)

---

### Post by darkod on 2010-05-17
Unfortunately without even seeing your computer I can't say for sure if deleting the 1MB partition is safe. But it's too small to hold anything relevant.
You could try to actually open it in ubuntu live mode and see what sort of files are on it. Not just looking in Gparted. You should be able to find the partition in Places.

Also, you can try running the boot info script from live mode too and pasting the results here. Here are some instructions how to do that:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

As for how much space is sufficient for ubuntu, it mainly depends of what sort of personal/data files you plan to keep there. For example, if all your larger files reside in windows and you don't plan to move them, ubuntu needs less space.

Ubuntu is not as demanding for space as windows. The default install takes only about 3GB - 3.5GB. Software that you add also doesn't add much. The type of files that might add a lot are like photos/videos/music, etc. According to that, 100GB is not only enough, but even too much. :)
However, if planning to keep videos and loads of photos in there, give it as much as you can spare.

---

### Post by Shirin10 on 2010-05-17
> **srs5694 said:**
> I wouldn't be so quick to delete the 1MB partition, at least not until I'd identified what it actually is. I recommend trying the following commands from Linux (using an Ubuntu live CD, [PartedMagic,]("http://partedmagic.com") [System Rescue CD,]("http://www.sysresccd.org") or something similar):

```

sudo fdisk -lu
sudo blkid /dev/sda1

```The "sudo" part may be unnecessary in some environments. Note that it's a lowercase "L", not a digit "1", after the dash in the fdisk command. Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. The first command identifies some low-level partitioning information, and the second peeks inside the mystery partition to try to identify any filesystem or other data it might contain.



Thanks.  Here it is.

[noparse]```
[/noparse] 
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7311862a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            2048    20973567    10485760   27  Unknown
/dev/sda3   *    20973568    21178367      102400   27  Unknown
/dev/sda4        21178368   625137663   301979648   42  SFS

Disk /dev/sdb: 2121 MB, 2121269248 bytes
255 heads, 63 sectors/track, 257 cylinders, total 4143104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x012d43b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     4143103     2071520+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(256, 254, 63) logical=(257, 228, 35)
[noparse]
```[/noparse] 


[noparse]```
[/noparse] 
/dev/sda1: LABEL="OS_Install" UUID="28286FBB286F8722" TYPE="ntfs" 
[noparse]
```[/noparse] 


...
What this means is completely unknown to me.
Looking forward to the next step.

---


@darkod: ok, thanks.  It is noted.

---

### Post by srs5694 on 2010-05-17
First, a minor point: By including "[noparse][noparse][/noparse]" and "[noparse][/noparse][/noparse]" strings around the "[noparse]```
[/noparse]" and "[noparse]
```[/noparse]" strings in your reply, you did away with the benefits. Your output should have looked more like this:

```

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd813d813

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1799    14450436    b  W95 FAT32
/dev/sdb2            1825        6002    33559785   bf  Solaris
/dev/sdb3            6003       10011    32202292+  a5  FreeBSD
/dev/sdb4   *        1800        1824      200812+  83  Linux

```

Note how the columns line up, as they do in the original. Note how they *don't* line up in what you posted, because the Web forum software obstinately tries to reformat everything as if it were paragraphs of natural language rather than the columnar data it actually is. This makes it very hard to extract meaning from the output, even if that meaning would jump out at a knowledgeable person in proper columnar form.

Anyhow, your /dev/sda1 is of type 0x42, which is an odd type. Checking [here,](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html) that's a "Windows 2000 dynamic extended partition marker:"

[quote=http://www.win.tue.nl/~aeb/partitions/partition_types-1.html]
If a partition table entry of type 0x42 is present in the legacy partition table, then W2K ignores the legacy partition table and uses a proprietary partition table and a proprietary partitioning scheme (LDM or DDM). As the Microsoft KnowledgeBase writes: *Pure dynamic disks (those not containing any hard-linked partitions) have only a single partition table entry (type **42**) to define the entire disk. Dynamic disks store their volume configuration in a database located in a 1-MB private region at the end of each dynamic disk.*
[/quote]

I now note that the Windows screen shot to which you linked in your first post specifies that the Windows C: volume is "Dynamique." I'm afraid I know very little about Windows dynamic partitions, so I'm reluctant to advise you to do anything specific except to research the issue more carefully before you do anything at all.

---

### Post by Shirin10 on 2010-05-19
Many thanks for your reply.


I am afraid that this case is "SOLVED".
Even before I could save/copy any partition/system/Win7, the system crashed and the blue screen appeared.  The restore point did not function.  After some fighting with the customer support of the netbook distributor Littlebrain, sorry Littlebit SA, I have decided that this case has come to an end:

I WILL NEVER USE WINDOWS AGAIN, EVEN IN DUAL BOOT.

I am finally free.

FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE, FREE!!!!!!

Kubuntu 10.4 has been installed smoothly.  I still have a sound problem though.  There is no sound...

---

### Post by linsaaaan on 2011-05-10
hello, 
i have the same problem, and it is a long time that i am trying to install Ubuntu, please help 
----------
these are my partitions
dev/sda1               1 MB             unknown
dev/sda2   ntfs       100 MB          unknown
dev/sda3   ntfs       178538 MB     unknown
dev/sda4   ntfs       421554 MB     unknown
----------

this is the result of "fdisk -lu"
/noparse
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1ccde6d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2048      206847      102400   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3          206848   153602047    76697600   42  SFS
/dev/sda4       153602048   976771119   411584536   42  SFS

Disk /dev/sdb: 8036 MB, 8036286464 bytes
248 heads, 62 sectors/track, 1020 cylinders, total 15695872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00029ac4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62    15683519     7841729    b  W95 FAT32

/noparse
-------------------------------------------------

and this is the result of "blkid dev/sda1"

ubuntu@ubuntu:~$ sudo blkid /dev/sda1
/dev/sda1: LABEL="System Reserved" UUID="08C6545BC6544B58" TYPE="ntfs" 

--------------------------------------------------

and this is the result of "blkid dev/sda2"

ubuntu@ubuntu:~$ sudo blkid /dev/sda2
/dev/sda2: UUID="947C7ED57C7EB21A" TYPE="ntfs"

---

