---
title: "Install on SSD ( cant see partitions )"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by __guppy on 2011-10-01
So I upgrade my hardware and got a shiny SSD aswell, from past experience it's always better to install windows before linux and after 6-7 attempts I managed to install win7.

Now that I got my toy OS up and running I want my work OS installed - but;

Ubuntu installer only detects the OS'es on the old hard drive (win7+11.04) and it thinks my SSD is completely blank, with no partitions :s

Any clue what I am doing wrong here? ( other than installing windows, haha )

I toggled AHCI mode on/off a few times when installing windows but I'm fairly sure it's still on... not really sure if that would make any difference.

SSD: Crucial m4 128gig. MOBO:  Asus P8Z68-v pro

[Solution] 

The fixpart tool fixed it and everything was smooth sailing here after

---

### Post by Hakunka-Matata on 2011-10-01
Hi, please post the results of ```
sudo fdisk -l && sudo sfdisk -luS
```

---

### Post by __guppy on 2011-10-01
```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5324b930

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       15566   124930048    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
(sdb partition info not shown to save post space)

Partition table entries are not in disk order
```
```
ubuntu@ubuntu:~$ sudo sfdisk -luS

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 15566 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048    206847     204800   7  HPFS/NTFS
/dev/sda2        206848 250066943  249860096   7  HPFS/NTFS
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty

Disk /dev/sdb: 60801 cylinders, 255 heads, 63 sectors/track
(sdb partition info not shown to save post space)

```

Also sda2 mounts just fine from the live CD:

partial mount output:

/dev/sda2 on /media/F66E96186E95D1AB type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

---

### Post by Hakunka-Matata on 2011-10-01
Your SSD has a GUID partition table, as stated in the output from fdisk and sfdisk. [COLOR=Red] That is a problem for the Ubuntu installer[/COLOR], I cannot tell you how to get around this speed bump, but it is not a big problem.  I'll look for the answer (have seen it many times, but I do not have (U)EFI BIOS and never have had to deal with the issue, so I don't remember)

[COLOR=Red]**EDIT: not true**[/COLOR]

---

### Post by Hakunka-Matata on 2011-10-01
[http://www.rodsbooks.com/gdisk/booting.html](http://www.rodsbooks.com/gdisk/booting.html)

that may explain it.

btw "GUID Partition Table [logically equal to] GPT

---

### Post by __guppy on 2011-10-01
Yes, It would seem that Ubuntu have severe issues installing on UEFI / GPT systems ( erasing the EFI partition and what not ) - how ever I cant even get that far as the Ubuntu installer claims the entire disc to be empty :|

It gets even weirder; I decided to try freeing up space for a ubuntu partition with the windows partition tool - this claims that the disc is using MBR partitioning :confused:


Edit:

Even with 30gig space freed up  the installer claims the entire disc to be free.

When I tried taking a screen shot of it and tried to save it I could see the list of all my partitions including the now 92 gig large win7 partition on the SSD -.- I've not had this much trouble installing linux since Redhat 4.2

---

### Post by Hakunka-Matata on 2011-10-01
another short thread on the topic> [http://ubuntuforums.org/showthread.php?t=1763198&highlight=on+gpt+disk](http://ubuntuforums.org/showthread.php?t=1763198&highlight=on+gpt+disk)

---

### Post by Quackers on 2011-10-01
It may be that your drive just has the GPT headers. The site that Hakunka-Matata linked you to should have details on what to do, if that's the case.

---

### Post by oldfred on 2011-10-01
+1 on Quackers 

You do not show efi partition and windows usually has another boot partition with gpt. 

Ubuntu will install to gpt drive, but Window will only install to gpt if you have UEFI not BIOS. Most new computers with UEFI have a BIOS mode for compatibly with older drives.

Part of site linked above.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Backup partition table first, change to sda or sdb:
sudo sfdisk -d /dev/sdc > parts_sdc.txt

---

### Post by __guppy on 2011-10-01
> **oldfred said:**
> +1 on Quackers 

You do not show efi partition and windows usually has another boot partition with gpt. 

Ubuntu will install to gpt drive, but Window will only install to gpt if you have UEFI not BIOS. Most new computers with UEFI have a BIOS mode for compatibly with older drives.

Part of site linked above.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Backup partition table first, change to sda or sdb:
sudo sfdisk -d /dev/sdc > parts_sdc.txt

That may be it - during my many attempts to install win7 it created first one partition layout ( with 3 partitions ) and then during the first boot told me that the partition layout was unsupported, subsequently it did a layout with 2 partitions

---

