---
title: "Huge Partition after install?"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by mfcallahan on 2010-01-05
I recently installed ubuntu from CD (Windows 7 previously factory installed, 500GB HD) and used the auto option for partitioning.  Everything works fine and Im able to dual boot, though I noticed that the installation partiton is now huge (up from about 50GB with windows 7 only to 168 GB!).  I also noticed the GRUB boot loader that there are multiple options: Ubuntu normal, ubuntu recovery mode, two different memory tests, Windows 7 and (very suprisingly) Windows Vista.  Are all of these swelling the partition to its current huge size?  Also, is the Windows Vista option normal when not installed previously?  When selecting that option, it launches into a windows installation dialog...  Im wondering if its possible to trim some fat, and shrink the partition down to something smaller.  Is it possible that the Windows Vista is not installed and the partition was created in anticipation of that?

Matt

---

### Post by tachuela on 2010-01-05
Post a picture of Gparted or:
"sudo fdisk -lu"

---

### Post by mfcallahan on 2010-01-05
RE: sudo fdisk -lu

---------
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc63193df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    21860351    10929152   27  Unknown
/dev/sda2   *    21860352    22065151      102400    7  HPFS/NTFS
/dev/sda3        22065152   608294867   293114858    7  HPFS/NTFS
/dev/sda4       608301225   976768064   184233420    5  Extended
/dev/sda5       608301288   961731224   176714968+  83  Linux
/dev/sda6       961731288   976768064     7518388+  82  Linux swap / Solaris
-----------


From my assumption, the largest partition is my normal file system, the next largest being Windows & Ubuntu installations, one for backup, and one for hibernate settings (which I've read can be quite large.  Like I mentioned befofe, Windows Vista should not be installed on this machine, though it shows up in the boot loader.  I suspect that this is why my installation partition is so large.


Thanks again,

Matt

---

### Post by mfcallahan on 2010-01-06
a

---

### Post by SecretCode on 2010-01-06
> **mfcallahan said:**
> I recently installed ubuntu from CD (Windows 7 previously factory installed, 500GB HD) and used the auto option for partitioning.  Everything works fine and Im able to dual boot, though I noticed that the installation partiton is now huge (up from about 50GB with windows 7 only to 168 GB!).  I also noticed the GRUB boot loader that there are multiple options: Ubuntu normal, ubuntu recovery mode, two different memory tests, Windows 7 and (very suprisingly) Windows Vista.  Are all of these swelling the partition to its current huge size?  Also, is the Windows Vista option normal when not installed previously?  When selecting that option, it launches into a windows installation dialog...  Im wondering if its possible to trim some fat, and shrink the partition down to something smaller.  Is it possible that the Windows Vista is not installed and the partition was created in anticipation of that?

Matt

Windows Vista was probably "detected" by the Grub2 bootloader in Ubuntu - maybe the factory install actually did have a Vista alternative, or maybe the recovery partition has a vista component on it.

I don't understand what you mean by the installation partition growing. Each operating system is installed on its own partition. There's no way I know of that an Ubuntu installation would cause an NTFS partition to grow in size ... only to be shrunk in order to make space.

Also, hibernation in Windows is normally handled by a file within the same partition; Linux uses the swap area which is normally a separate partition. Yours is about 3.5GB which is normal.

sda1 ~5GB is probably the system recovery partition.
sda2 which is only 50MB is odd - this must be a boot partition created by windows (also part of the factory install?) - this might be what Grub thinks is Vista. I wouldn't worry about it.
sda3 ~140GB has to be your Windows 7 partition. There'll be no Ubuntu code at all in this partition.

(The different Ubuntu options and the memtest options are all run from the ubuntu partition sda5.)

Are you **sure **one of the partitions was ever just 50GB?

---

### Post by kansasnoob on 2010-01-06
Post the output of:

```
sudo parted /dev/sda print
```

Much more human readable ;)

Most of your grub2 questions are answered here:

[http://ohioloco.ubuntuforums.org/showthread.php?t=1195275](http://ohioloco.ubuntuforums.org/showthread.php?t=1195275)

---

### Post by mfcallahan on 2010-01-06
RE: sudo parted /dev/sda print

Model: ATA SAMSUNG HM500JI (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  11.2GB  11.2GB  primary   ntfs
 2      11.2GB  11.3GB  105MB   primary   ntfs            boot
 3      11.3GB  311GB   300GB   primary   ntfs
 4      311GB   500GB   189GB   extended
 5      311GB   492GB   181GB   logical   ext4
 6      492GB   500GB   7699MB  logical   linux-swap(v1)

---

### Post by mfcallahan on 2010-01-06
also, forgot to include in previous post:  sda1 is Vista, and sda2 is Windows 7, according to the options on the boot loader.

---

### Post by darkod on 2010-01-06
> **mfcallahan said:**
> RE: sudo parted /dev/sda print

Model: ATA SAMSUNG HM500JI (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  11.2GB  11.2GB  primary   ntfs
 2      11.2GB  11.3GB  105MB   primary   ntfs            boot
 3      11.3GB  311GB   300GB   primary   ntfs
 4      311GB   500GB   189GB   extended
 5      311GB   492GB   181GB   logical   ext4
 6      492GB   500GB   7699MB  logical   linux-swap(v1)

It looks quite normal.
sda1 is your recovery partition. Probably that's the install process you see starting if you select it in grub menu. Vista and 7 have similar boot records and win7 recovery partition can be reported wrongly as vista boot.
sda2 is the 100MB win7 boot partition, and sda3 is the win7 system partition.
Then in the extended partition, sda5 is your ubuntu root and sda6 swap.

About the sizes of the partitions, we don't know what your disk looked like so we can't judge. You have to take into account that some partition was shrinked (probably sda3) to make space for ubuntu (sda4 with sda5 and sda6 inside).
Which of the partitions look with "wrong" size to you?

---

### Post by SecretCode on 2010-01-07
OK, I see the linux partition is the one that is 168GiB, the number you gave. Was there a 50GB linux partition before? And this has "grown". 

On a 500GB drive I would partition it differently - 20-40GB tops for each OS partition, and the rest in data partitions. But if it's working the way it is, no need to rush into anything!

---

### Post by mfcallahan on 2010-01-07
Thanks for the help, I think I will leave as for now, eveything seems to be working OK.  300BG left on the HD is enough left to work with for me.  Would Gparted be the way to go if I want to resize anything in the future?

---

### Post by mfcallahan on 2010-01-07
** 300 gb

---

### Post by SecretCode on 2010-01-07
Yes, gparted is the way to go.

Just remember to take seriously the warning that any partition editing carries a risk of losing data. Make backups first.

---

### Post by tachuela on 2010-01-07
Use Gparted Live CD, ( it works with unmounted partitions; which is better):
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

