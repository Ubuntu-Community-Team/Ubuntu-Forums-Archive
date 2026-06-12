---
title: "At installation my disk shows as completely unallocated but I have windows7 installed"
date: 2013-08-15
forum: Installation &amp; Upgrades
---

### Post by ndefontenay on 2013-08-15
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd033d792

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   986601471   493197312    7  HPFS/NTFS/exFAT
/dev/sda3       986601472  1953519615   483459072    7  HPFS/NTFS/exFAT
Gparted

/dev/sda contains GPT signatures, indicating that it has a GPT table.  
However, it does not have a valid fake msdos partition table, as it should.  
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  
Or perhaps you deleted the GPT table, and are now using an msdos partition table.  
Is this a GPT partition table?
So when I try to install ubuntu I get a whole TB of unallocated disk. However I can see the 2 partitions mounted on ubuntu when I run "try ubuntu" I've created the ntfs partition on /dev/sda3 in an effort to fix the GUID table without success.

Is there any way to fix this so I can install ubuntu on /dev/sda3?

---

### Post by oldfred on 2013-08-15
Was this a gpt drive and you installed Windows in BIOS mode. It converts drive to BIOS, but does not erase backup gpt partition table (one of advantages of gpt is  a backup table). So then Linux tools see MBR and backup gpt and get confused and stop working.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by ndefontenay on 2013-08-15
Fixparts fixed it :) I did it from the Ubuntu's DVD (try ubuntu) and went on to installing. It's currently going forward with the installation.
Thanks a lot for that super handy tool :)

---

