---
title: "FAT32 partition wants to be known as NTFS"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by archis on 2006-02-21
A question regarding file systems: I've partitioned an external drive with qtparted to prepare it for a fresh install of Ubuntu -- a large FAT32 partition for Windows file sharing, and root, home and swap partitions for Ubuntu respectively.

When I check the partitions and filesystem of this drive with cfdisk or fdisk -l, the FAT32 partition shows up correctly:

```
Disk /dev/sda: 80.0 GB, 80060424192 bytes
4 heads, 32 sectors/track, 1221625 cylinders
Units = cylinders of 128 * 512 = 65536 bytes

   Device   Boot     Start         End      Blocks   Id  System
/dev/sda1                1      946045    60546864    c  W95 FAT32 (LBA)
/dev/sda2    *      946046     1023865     4980480   83  Linux
/dev/sda3          1023866     1221625    12656624+   5  Extended
/dev/sda5          1023866     1206970    11718704   83  Linux
/dev/sda6          1206971     1221625      937904   82  Linux swap / Solaris
```
But when I try to mount this FAT32 partition, I get an error written into my syslog and the drive doesn't mount:

[FONT="Lucida Sans Unicode"][COLOR="DarkOliveGreen"][INDENT]localhost kernel [4297536.354000] FAT: bogus number of reserved sectors
localhost kernel [4297536.354000] VFS: Can't find a valid FAT filesystem on dev sda1.[/INDENT][/COLOR][/FONT]

If I specify the partition as read-only ntfs, though, it mounts. I have put the following entry into my fstab, and the drive mounts with it:

[FONT="Lucida Console"][COLOR="DarkOliveGreen"]/dev/sda1       /media/tantalus ntfs    ro,user,auto,nls=utf8,fmask=0333,dmask=0222      0       0[/COLOR][/FONT]

What's more, the partition also shows up as ntfs in Windows. 

So there's a mismatch between what I did with qtparted, what fdisk tells me and how the partition is actually being handled under both Linux and Windows. 

It looks as if the partitioning with qtparted was not successful for this partition.  I wonder whether the size of the FAT partition has something to do with this? As you can see from the fdisk output, it's about 60GB. The built-in Windows partitioning tool only formats FAT32 partitions up to 32GB but qtparted doesn't have this restriction.

Apart from the changed functionality, should I be concerned about the file system integrity on this partition? What are the consequences of Linux (and Windows) treating a FAT32-formatted filesystem as ntfs?

---

### Post by Coelocanth on 2006-02-21
If memory serves, the FAT32 file system won't work on anything bigger than 32 GB. Even though qtparted supposedly formatted it to a 60 GB partition, that's probably where your error lies. I think the only thing you can do to fix it is to reformat that partition into 2 partitions of 32 GB or less each.

Don't take this as set in stone however. I'm too old for my memory to be completely reliable... ;)

---

### Post by archis on 2006-02-21
I'm a bit confused about what works and what doesn't. For example, I thought that many or most large external drives (80, 120, 200GB etc.) you can buy off the shelf these days are actually pre-formatted with FAT. I sort of assumed that's what the drive's 'natural state' was before I started to work on it with qtparted..?

---

### Post by Ocxic on 2006-02-21
the drive you get from the store or fresh, and have never been formatted. this allow you to format the most easiest way, without haveing to deal with a partitons thats already there.

---

### Post by Coelocanth on 2006-02-21
[QUOTE=archis]I'm a bit confused about what works and what doesn't. For example, I thought that many or most large external drives (80, 120, 200GB etc.) you can buy off the shelf these days are actually pre-formatted with FAT. I sort of assumed that's what the drive's 'natural state' was before I started to work on it with qtparted..?[/QUOTE]

No, as Ocxic said, I don't think they're formatted (other than the low-level format), so you need to format them before installation of an OS.

As for the 32 GB limit on a FAT32 partition, like I said, I could be wrong, but I could swear I've read that somewhere. Apologies if I've further muddied the waters for you or provided erroneous info.

*edit* I'll do some research and get back to you.

*re-edit* Okay, here's what I found: I was sort of right and mostly wrong. This quote should clear things up:

> A FAT32 volume must have a minimum of 65,527 clusters. Windows XP Professional can format FAT32 volumes up to 32 GB, but it can mount larger FAT32 volumes created by other operating systems.

So, your FAT32 partition, according to this quote, should be read correctly by Windows at least (I believe that applies to XP Home as well). Judging from that, it would seem it's not a size problem. Anyway, I've confused things enough, so I'll shut up now. Again, apologies for making things murkier.

---

### Post by archis on 2006-02-22
Thanks for your efforts, coelocanth -- I hope you won't exit the discussion as I hope to clarify two issues: 

1) Are there any known issues with QTparted formatting very large (>32GB) FAT partitions?

2) Are there any adverse consequences (potential file corruption etc) to a FAT32 partition being mounted as NTFS?

But first I want to clarify what I meant with FAT formatting on large storage devices: Storage devices of large manufacturers carry the FAT32 filesystem out of the box because it is, Windows nonwithstanding, the most common file system to most operating systems. [Here is a link]("http://www.experts-exchange.com/Storage/Q_20762156.html") to a comment from a Maxtor representative explaining their policy to format their storage devices with FAT32. The comment, in response to a file corruption issue, is way down in the comments thread, so I've copied it here for your convenience:
  
[INDENT][COLOR="DarkRed"]We are aware of the XP "not formatted" issues. This type of phenomenon is not isolated to Maxtor drives. The problem with hard drives losing their format with XP is not related to hard drive functionality but rather how XP recognizes file systems. This issue is most common with external drives carrying the FAT 32 file system. Most of our external drives made for PCs carry the FAT 32 file system out of the box. This is because the FAT 32 file system is the most common file system to most operating systems. However, this file system is not a very stable file system in Windows XP or 2000, particularily with the large drives sizes in the marketplace today. We recommend (and we have documented in our installation manuals) that the file system be changed immediately to NTFS for any machine running XP or Windows 2000. That will solve most of the file corruption issues on our external drives.

This issue happens less often on internal drives. But again, we would recommend the NTFS file system for large drive sizes, or if you want the drive to be set up in FAT 32, that you use the Disk Management utility within XP to set up the drive. When you use Disk Management to set up the drive, it will not allow you to set up the partition size any larger than 32 gigs in FAT 32. This is a constraint within XP. Generally speaking, any format on a drive is software written to the drive and it does not reflect the proper functioning of the drive if the format is corrupted at the software level.[/COLOR][/INDENT]



FAT32 support was added to Debian's Linux kernels [from 2.0.34 onwards]("http://www.linux.ie/articles/tutorials/dualboot.php"). I assume this means full read-write support, limited by FAT32's own volume size limitations. I've looked around a bit for info on FAT32 volume sizes and here's what I've come up with so far:

Regarding Windows XP support for large FAT32 partitions, [Daniel Petri writes:](http://www.petri.co.il/install_windows_xp_on_large_fat32_partitions.htm)

[INDENT][COLOR="DarkRed"]As you probably know already, Windows 2000, XP and Windows Server 2003 have built-in support for FAT32-formatted partitions (Windows NT 4.0 did not). Although these operating systems can read, write and boot from FAT32 partitions, Windows XP and Windows Server 2003 have a maximum size limit of 32GB for creating such partitions.

The above paragraph means that you CAN use any FAT32 partition you want, no matter it's size, however you CANNOT create FAT32 partitions larger than 32GB in size.

Also, Windows 2000, XP and Windows Server 2003 do NOT have a native utility that can be used to convert FAT16 partitions to FAT32.

There is a way to trick Windows 2000, XP or Windows Server 2003 into using FAT32 partitions bigger then 32GB. Here is how you do it:

   1.     Get a Win98 boot disk.
   2.     Boot from boot disk and run Fdisk.
   3.     Partition the drive to what size you want up to 120GB.
   4.     Reboot the computer off of the Win98 boot disk.
   5.     Format the drive.
   6.     Boot the computer off of the Windows 2000, XP or Windows Server 2003 CD.
   7.     Proceed to install Windows.
   8.     When Setup asks you what partition to install to choose the disk you just formatted it will give you several option dealing with NTFS. Don't make any changes and choose the last option, which is to install the OS to the current drive without making any changes. Setup will proceed to install normally and you will have Windows 2000, XP or Windows Server 2003 installed to a fully functional FAT32 Partition greater then 32GB. 

As stated above, remember that Windows 2000, XP and Windows Server 2003 can use larger than 32GB partitions, but Microsoft intentionally limited the Fdisk portion in Windows in order to push people to use NTFS instead (which in my opinion is a smart move).[/COLOR][/INDENT]

Daniel Petri's reader Tom Thornhill wrote a command line tool with which you can actually format FAT32 partitions larger than 32GB using the Windows XP tools ('Disk Management', compmgmt.msc). [Please see here for more details.](http://www.ridgecrop.demon.co.uk/fat32format.htm)

Thornhill also writes

[INDENT][COLOR="DarkRed"]that the 32GB limit is a limit of the formatter in Windows XP. FAT32 itself should be OK to 2TB, limited by a 32 bit sector count in the boot sector.[/COLOR][/INDENT]

[A Microsoft KB article states]("http://support.microsoft.com/default.aspx?scid=KB;EN-US;Q314463&")

[INDENT][COLOR="DarkRed"]The maximum disk size is approximately 8 terabytes when you take into account the following variables: The maximum possible number of clusters on a FAT32 volume is 268,435,445, and there is a maximum of 32 KB per cluster, along with the space required for the file allocation table (FAT).[/COLOR][/INDENT]

Wikipedia's [FAT entry goes with 2TB as well]("http://en.wikipedia.org/wiki/File_Allocation_Table").

------------

I conclude: FAT32 partitions can probably be up to 2TB or perhaps 8TB large. Windows supports read-write access to large FATs but doesn't provide the tools to create or manage them.

---

### Post by blakegrover on 2006-03-18
I am also having this problem.  Whenever I try to mount a fat32 drive it gives me the same error:

```
[4295033.218000] FAT: bogus number of reserved sectors
[4295033.218000] VFS: Can't find a valid FAT filesystem on dev sda7.
r
```

This is on a 80 Gigabyte hard drive.  The first partition is NTFS and its around 65 GB, then I have my ext3 partitions where I have boot and my root.  After that I have 3.5 Fat32 partition and I have my swap space after that.  I have formatted the fat32 partition in windows and I get the error mounting the drive in linux.  I formatted the partition again in qtparted as fat32 and still nothing.. Any help would be appreciated.

---

### Post by DoktorSeven on 2006-03-18
Just as a clarification to the original poster, what fdisk reports on the right is the partition ID (c = fat32) can differ from what the partition is actually formatted as.  One can create a fat32 filesystem on a partition labeled 83 (Linux), for instance.  In other words, creating a filesystem of a certain type is separate from creating the partition and its associated ID.

In your case, apparently qtparted created the partition as fat32, but Windows formatted it as NTFS.  Change the ID to 7 (HPFS/NTFS) using a partition editor (fdisk/qtparted/etc) and you should be okay.

And for the last poster -- sure you formatted the partition as FAT32 instead of NTFS in Windows?  Again, partition ID can differ from the actual filesystem... (try mounting as ntfs)

---

### Post by Irony on 2006-03-18
This is how to change a partition ID with fdisk, here I change the ID from 7 (ntfs) to 83 (linux) on hda4;

[PHP]irony@ubuntu:~$ sudo fdisk /dev/hda

The number of cylinders for this disk is set to 24792.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): t
Partition number (1-6): 4
Hex code (type L to list codes): 83
Changed system type of partition 4 to 83 (Linux)

Command (m for help): p

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7438    59745703+   7  HPFS/NTFS
/dev/hda2            7439       14618    57673350    5  Extended
/dev/hda3           14619       19840    41945715    7  HPFS/NTFS
/dev/hda4           19841       24792    39776940   83  Linux
/dev/hda5            7439       14323    55303731   83  Linux
/dev/hda6           14324       14618     2369556   82  Linux swap / Solaris

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource  busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
irony@ubuntu:~$[/PHP]

---

### Post by blakegrover on 2006-03-18
Sorry about posting I feel kind of stupid now.  I was trying to mount my swap space sd7, my fat32 partition is sda6 and it works fine.  Thanks again for helping me open my eyes

---

