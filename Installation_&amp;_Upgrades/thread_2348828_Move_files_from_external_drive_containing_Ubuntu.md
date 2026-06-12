---
title: "Move files from external drive containing Ubuntu"
date: 2017-01-07
forum: Installation &amp; Upgrades
---

### Post by storm-twister on 2017-01-07
I've connected a HDD via USB to my laptop, and on that external HDD, I have an installation of Ubuntu v14.04 and Windows 7. I only want to move some files and directories from my Documents folder and place them into my new installation of Ubuntu on the internal HDD of my laptop. I can see the Windows partitions and directories of the external HDD, but I cannot see the Ubuntu partition at all.

How can I achieve this?

---

### Post by TheFu on 2017-01-07
Connect the HDD and run **sudo parted -l**

Did you happen to encrypt any part of the Linux install?

---

### Post by storm-twister on 2017-01-07
Hello TheFu,
Thank you for replying on a Saturday. This is the output on Terminal:

```
Model: ATA ST1000LM014-1EJ1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs
 2      106MB   22.5GB  22.4GB  primary
 3      22.5GB  511GB   489GB   primary   ntfs            boot
 4      511GB   1000GB  489GB   extended
 5      511GB   994GB   483GB   logical   ext4
 6      994GB   1000GB  6207MB  logical   linux-swap(v1)


Model: Multiple Card Reader (scsi)
Disk /dev/sdb: 64.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 2      21.5GB  33.5GB  12.0GB  extended
 5      21.5GB  33.5GB  12.0GB  logical   linux-swap(v1)
 1      33.5GB  64.5GB  31.0GB  primary   ntfs


Model: KINGWIN ADP07 (scsi)
Disk /dev/sdc: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  26.8GB  26.8GB  primary   fat32        hidden, lba
 2      26.8GB  283GB   256GB   primary   ntfs         boot
 3      283GB   640GB   357GB   extended               lba
 5      283GB   640GB   357GB   logical   ntfs
```

---

### Post by storm-twister on 2017-01-07
The 1TB drive is the internal drive.

---

### Post by TheFu on 2017-01-07
According to the partition tables, there is only 1 Linux partition on any of the 3 storage devices connected. Everything else is using NTFS, which cannot be used by Linux for the OS or /home/ directories.

Do you have the correct disk?
Could it have been wiped?

---

### Post by storm-twister on 2017-01-07
Ah man! What a silly mistake! I connected my other drive and wallah, there are the files. It was confounding me why I could not see Ubuntu directories with Ubuntu period. Thank you for your help. I should label my drives.

---

### Post by TheFu on 2017-01-08
Yep.  I use letters.  That way when the purpose of the drive changes over the years, It doesn't ahve the wrong label from the beginning.  I use a "silver sharpy" on the edge - white on black is easier to read. ;)

Also, use "docks" here much more than enclosures.  Easier to swap disks that way.

---

### Post by storm-twister on 2017-01-08
Can I ask,  could you explain what it means by using docks?

---

### Post by TheFu on 2017-01-08
> **storm-twister said:**
> Can I ask,  could you explain what it means by using docks?

Something like this:
[https://www.amazon.com/Inateck-Dual-Bay-Function-Tool-Free-FD2002/dp/B00N1KXE9K/](https://www.amazon.com/Inateck-Dual-Bay-Function-Tool-Free-FD2002/dp/B00N1KXE9K/)

No enclosure. Trivial to swap different HDDs. I have 4 USB3 and 1 eSATA dock.  Most hold 2-HDDs.

---

### Post by storm-twister on 2017-01-09
Ok, thanks. I'll look into that. Best regards.

---

