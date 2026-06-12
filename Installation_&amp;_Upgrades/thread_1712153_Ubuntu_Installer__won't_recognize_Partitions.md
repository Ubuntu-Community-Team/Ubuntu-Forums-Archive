---
title: "Ubuntu Installer  won't recognize Partitions"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by AND1 on 2011-03-22
Hi there,
since a long time I'm having troubles to install Ubuntu on my notebook.
I used Ubuntu before, without problems but since the 10.04 version it won't recognize my partitions.
I formated my laptop and partitioned it, installed Windows 7 64bit, which I need for my work, and wanted now to install Ubuntu 10.04/10. 
I then used GParted to check my Harddisk and it is having troubles to recognize my partitions, too while Windows finds them. GParted is giving me an error message saying my partitions are oversized. I am still in the beginning of my Linux experiences and so I don't know what to do.
I have two 250GB harddisks (how Windows recognizes them), 
```
Disk0:
System Reserved 100MB
C:                                          69,90 GB  NTFS                  -> System (Windows7)
D:                                          125,00 GB FAT 32                                                      ext. Partition                          
                         33,88 GB                                 -> ext3 for Linux                                                    "                "
                                                    4,00 GB                                    -> free to create a swap partition     "        "    
Disk1:
E:                      50,01 GB FAT 32      ext. Partition
F:                      182,26 GB FAt 32               "             "
```

**Here is the fdisk -lu and the sfdisk -d:**
 

```
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0e5f0e5f
      Device     Boot            Start         End                     Blocks             Id         System
/dev/sda1      *                    2048              206847              102400         7          HPFS/NTFS
/dev/sda2                        206848    146800639        73296896        7          HPFS/NTFS
/dev/sda3                146801970    488392064   170795047+    f           W95 Ext'd (LBA)
/dev/sda4          408950640    480006134   35527747+   83       Linux
/dev/sda5                146802033    408950639    131074303+   b         W95 FAT32Disk 

```

```
/dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa08c3a0e
       Device    Boot          Start               End                          Blocks             Id      System
/dev/sdb2        *            16065         488392064       244188000      f        W95 Ext'd (LBA)
/dev/sdb5                        16128         104904449       52444161       b       W95 FAT32
/dev/sdb6               104904513     488392064      191743776    b     W95 FAT32# 

partition table of /dev/sdaunit: 
sectors
/dev/sda1 : start=     2048,          size=   204800,         Id= 7, bootable
/dev/sda2 : start=   206848,      size=146593792,   Id= 7
/dev/sda3 : start=146801970, size=341590095,   Id= f
/dev/sda4 : start=408950640, size= 71055495,    Id=83
/dev/sda5 : start=146802033, size=262148607,   Id= b# 

partition table of /dev/sdbunit: 
sectors
/dev/sdb1 : start=        0,                   size=             0,               Id= 0
/dev/sdb2 : start=    16065,        size=488376000,  Id= f, bootable
/dev/sdb3 : start=        0,                  size=             0,               Id= 0
/dev/sdb4 : start=        0,               size=             0,              Id= 0
/dev/sdb5 : start=    16128,        size=104888322,   Id= b
/dev/sdb6 : start=104904513,  size=383487552,  Id= b
```

---

### Post by Quackers on 2011-03-22
gparted can't see your partitions because you have an "illegal" partition table.
As you will see from the red entry, you have a primary partition (sda4)inside an extended partition (sda3). This is illegal in the mbr partitioning system. In fact, it should not be possible, however, we have seen it once or twice, lately.
It seems that the Windows installer can cause it sometimes, when partitions already exist before Windows is re-installed. I'm sure there are other possibilities too, sadly.

```
Device Boot Start End Blocks Id System
/dev/sda1 * 2048 206847 102400 7 HPFS/NTFS
/dev/sda2 206848 146800639 73296896 7 HPFS/NTFS
/dev/sda3 146801970 488392064 170795047+ f W95 Ext'd (LBA)
[COLOR="Red"]/dev/sda4 408950640 480006134 35527747+ 83 Linux[/COLOR]
/dev/sda5 146802033 408950639 131074303+ b W95 FAT32Disk 
```

I am not certain what should (or could) be done about that, but I know a man who may do :-)
I will ask him to take a look. I don't know if he is online at the moment, but I would recommend that you wait for further advice before doing any partitioning or installing.

---

### Post by Hakunka-Matata on 2011-03-22
Are you able to boot to the Live CD and choose "Try Ubuntu without installing"?

If so, boot into Ubuntu Live, and come back here to the forums

and oh, Welcome

---

### Post by coffeecat on 2011-03-22
> **Quackers said:**
> I don't know if he is online at the moment,

Yep, here I am. :)

@AND1, I agree with Quackers' diagnosis but I'm going to ask you to boot the live CD up again and run those terminal commands again. Something has happened to the formatting. That makes it difficult to read but, more importantly, bits of one line seem to have become appended to the end of a previous line. Examples:

> W95 FAT32Disk
W95 FAT32# 
partition table of /dev/sdaunit: 
Id= b# 

Since you'll probably need to edit the partition table with one of two utilities, we need to see exactly what those terminal commands are outputting, so as not to make any mistakes. I suspect you may have used a Windows text editor somewhere along the line. Unfortunately, Windows and Linux text editors use different conventions for line endings, and I think this is where the output has gone wrong. Don't use a Windows text editor but do this:

Boot up the Ubuntu live CD and choose "try Ubuntu". Open a terminal and run these three commands:

```
sudo fdisk -lu > Desktop/fdisk.txt
sudo sfdisk -d /dev/sda > Desktop/parts_sda.txt
sudo sfdisk -d /dev/sdb > Desktop/parts_sdb.txt
```

That will produce three text files on the live Desktop. Either post them from the live CD session, or if you have to use Windows to connect to the internet, copy them to a USB external drive from the Ubuntu session, and then attach them to your post using the 'Manage Attachments' button you can find below the message field. Above all, don't open them with a Windows text editor.

I've asked you to include details of your sdb (second) drive since you posted partial information for that in your first post. It may not be relevant, but let's see it anyway.

---

### Post by AND1 on 2011-03-22
Hey thanks for the fast reply and sorry for the format.
I am now online using the life CD. Here is the data:

---

### Post by coffeecat on 2011-03-22
> **AND1 said:**
> Hey thanks for the fast reply and sorry for the format.
I am now online using the life CD. Here is the data:

Thanks. I'll just post them in code tags so that others can see, and I'll post back again when I've had a think. 
[B]
fdisk -lu[/B]
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0e5f0e5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   146800639    73296896    7  HPFS/NTFS
/dev/sda3       146801970   488392064   170795047+   f  W95 Ext'd (LBA)
/dev/sda4       408950640   480006134    35527747+  83  Linux
/dev/sda5       146802033   408950639   131074303+   b  W95 FAT32

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa08c3a0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *       16065   488392064   244188000    f  W95 Ext'd (LBA)
/dev/sdb5           16128   104904449    52444161    b  W95 FAT32
/dev/sdb6       104904513   488392064   191743776    b  W95 FAT32
```

**sfdisk /dev/sda**

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=   204800, Id= 7, bootable
/dev/sda2 : start=   206848, size=146593792, Id= 7
/dev/sda3 : start=146801970, size=341590095, Id= f
/dev/sda4 : start=408950640, size= 71055495, Id=83
/dev/sda5 : start=146802033, size=262148607, Id= b
```

**sfdisk /dev/sdb**

```
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=        0, size=        0, Id= 0
/dev/sdb2 : start=    16065, size=488376000, Id= f, bootable
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start=    16128, size=104888322, Id= b
/dev/sdb6 : start=104904513, size=383487552, Id= b
```

---

### Post by coffeecat on 2011-03-22
OK. The problem is that your Linux partition, currently identified as sda4 should be a logical partition because it's inside the extended partition sda3. However, logical partitions are always numbered 5 and upwards, even if there is a gap between 1 and 4. A partition numbered sda4 is, by definition, either a primary partition or an extended partition (which is simply a special type of primary used solely as a container for logical partitions. Since your sda3 is an extended partition, and since you can only have one extended partition on a drive, a partition numbered sda4 must be a primary partition. Except yours can't be, because.... This is why Gparted doesn't see anything - it's a known issue that Gparted will show the whole drive as "unallocated" when there's a partition table illegality.

The answer is to edit the partition table, either with sfdisk or with a new utility written by forum member srs5694. See here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I have to go offline shortly for a few hours. It will be a good idea to involve srs5694 himself. Either Quackers or I will contact him so if you're prepared to be patient, that would be great.

In the meantime, a couple of questions. Do you know what the purpose of the FAT32 sda5 partition is? And, did you realise that you will need a swap partition as well as a Linux root partition? Also - there is a approximately 4GB unallocated gap in the extended partition that comes after your problem "sda4" partition. This might have been a swap partition that was taken out by whatever corrupted the partition table. Possibly the Windows installer as Quackers suggested. I've been doing some experiments with Windows installers working on HDs with Linux logical partitions. You don't want to know what can happen sometimes! :-s

---

### Post by AND1 on 2011-03-22
You're absolutely right, the 4GB FAT32 (sda5) has been the swap partition. It is astonishing what you guys can read out of this numbers!
And I can be patient, no problem. Have been trying to solve the problem on my own for quiet a while and I will start to save my data right now, just in case...;) 

Thanks again for you efforts!

---

### Post by Quackers on 2011-03-22
Thanks coffeecat :-)
AND1, I was unsure whether coffeecat has asked the author of fixparts for guidance, so I've asked him to have a look.
You've got plenty of reading to do, so a wait for him is probably not a problem :-)
I'm sure he'll be along when he can.

---

### Post by srs5694 on 2011-03-22
I'm the guy that Quackers and coffeecat contacted, and I agree with their analysis. You should either edit the partitions using sfdisk or use FixParts to fix the problem. FixParts is easier to use, but if you're comfortable editing the sfdisk output, it might be safer, since FixParts is still pretty new and relatively untested. Whatever you do, keep a copy of your current sfdisk output somewhere other than the hard disk you're modifying; if your efforts make things worse, you can use the sfdisk output to restore your partitions to the way they are now and start over again.

Good luck!

---

### Post by coffeecat on 2011-03-22
@AND1, now that srs5694 has posted I just wanted to say that I think you'll find fixparts quite straightforward to use. You can install it in the live session but remember to download the deb file appropriate for the architecture of your live CD - i386.deb for 32-bit or amd64.deb for 64-bit.

If you prefer to use sfdisk though, post back and I'll post a modified file based on your parts_sda.txt. This can then be written with sfdisk.

---

### Post by AND1 on 2011-03-23
Hey,
I tested it...perfect, GParted and the Ubuntu-Installer are now recognizing my partitions!
Thanks a lot! Now I can start to install Ubuntu again!
  Thanks again for the help, I learned much since yesterday!
  Greets!
 AND1

---

### Post by coffeecat on 2011-03-23
That's good news. Good luck!

---

### Post by Quackers on 2011-03-23
Excellent news! :-)
Did you use Fixparts?

---

### Post by leatherneckbiker on 2011-05-18
AND1 never came back and posted, but I wanted to add my story in the hopes it would help someone else.

Bottom line up front, OSX was the offender in my case.  It left "ghost" partitions with GPT signatures on both drives after spending a couple days attempting to get OS X to run natively on my laptop.

The platform:

Dell XPS 17 (L701X)
Core i7QM @ 1.73GHz
12 GB RAM
NVIDIA GeForce GT 455M w/3GB
Broadcom Bluetooth V.3
HL-DT-ST DVDRW/BDROM CT30N
Dual Samsung HM640JJ 640 GB HDD
HDMI Port
USB 2.1/3.0 ports
SD card reader
Intel G/B Ethernet
Intel Centrino 1000 Wireless N

The Problem:

After my experiments, I wiped the system to do a clean install.  Installed Windows 7 Home Professional, then added Ubuntu.  I didn't really pay any attention as I've done it many times but after install, realized that the installer never recognized my Windows installation.

The damage was done.  The 100MB partition that Win7 creates upon install was gone.

I reinstalled and loaded the live CD.  After some reading, I came across this thread and decided to try FixParts.  It recognized the errors and asked me to delete them. I'll need to rerun the installer to verify, but I'll be back in a few to check in.  Below are the results of the fdisk and sfdisk commands:

Before:

fdisk.txt
[INDENT]Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa5f99ec9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848  1250260991   625027072    7  HPFS/NTFS

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa376c0db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1250260991   625129472    6  FAT16[/INDENT]

parts_sda.txt
[INDENT]# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=   204800, Id= 7, bootable
/dev/sda2 : start=   206848, size=1250054144, Id= 7
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0[/INDENT]

parts_sdb.txt
[INDENT]# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=     2048, size=1250258944, Id= 6
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0[/INDENT]

---

### Post by leatherneckbiker on 2011-05-18
srs5694, coffeecat, and Quackers...

Thanks so much for your help and work supporting the community.  FixParts worked like a charm...

Rebooted and verified windows still worked, then booted to the liveCD. Install recognized Win7 just like it should have.

Again, thanks to all.

---

### Post by Quackers on 2011-05-19
Very nice :-)
Fixparts is a very useful tool  -  thanks srs5694 :-)

---

### Post by srs5694 on 2011-05-19
> **leatherneckbiker said:**
> Bottom line up front, OSX was the offender in my case.  It left "ghost" partitions with GPT signatures on both drives after spending a couple days attempting to get OS X to run natively on my laptop.
...
The Problem:

After my experiments, I wiped the system to do a clean install.  Installed Windows 7 Home Professional, then added Ubuntu.  I didn't really pay any attention as I've done it many times but after install, realized that the installer never recognized my Windows installation.

I'm glad you got it sorted out, but I thought I'd point out that you've really got three interacting issues that created the mess. From a strictly technical point of view, the only one that could be called an "offender" is libparted in the Ubuntu installer; however, as a practical matter the Windows partitioner deserves some blame, too. The three factors are:


[list]
[*]OS X uses the GUID Partition Table (GPT) by default, and for good reasons. GPT's design includes a "protective MBR," which is intended to prevent GPT-unaware utilities from overwriting a GPT disk. When you finished experimenting with OS X, your disk was therefore a GPT disk. This doesn't make OS X an "offender;" it just did with the disk what it had every right to do with the disk. Note also that what eventually caused the problems was not "'ghost' partitions with GPT signatures," as you wrote, but leftover GPT data that fell outside of the areas normally used by MBR -- GPT uses sectors on the disk that aren't normally touched by MBR data structures.
[*]When you installed Windows on the disk, it treated the disk as an MBR disk. It deleted the protective MBR, but it did not delete the GPT data outside of the MBR. From a strictly technical perspective, this is fine, since the GPT specs say that a disk with an MBR but no GPT protective partition is an MBR disk, not a GPT disk. Still, the bulk of the GPT data remained on the disk....
[*]Sadly, libparted has a bug that causes it to flake out when it sees a conventional (non-protective) MBR-only sector 0 along with GPT data. Most libparted-based tools treat the disk as empty, although some favor the GPT data, in clear violation of the GPT specs. This is the part of the picture where blame can unambiguously rest, since either behavior is a violation of the GPT specs and therefore constitutes a bug in libparted.
[/list]


So, if I were to apportion blame, I'd give 90% to libparted, 10% to the Windows installer, and 0% to OS X. From a standards point of view, Windows is actually blameless; however, I give it 10% because the Windows installer *does* understand GPT -- it can identify GPT disks and it can even use GPT disks if the computer uses UEFI firmware rather than BIOS. Thus, although simply overwriting the MBR and ignoring the GPT data is technically OK, it's lazy; to avoid the possibility of confusion, the Windows partitioner should wipe the GPT data, as libparted does when you tell it to create a fresh partition table on a GPT disk.

---

