---
title: "[SOLVED] Hard disk woes"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by lisati on 2008-10-03
I'm just about off to bed after spending several hours mucking around, and suggestions would be appreciated.

Synopsis of problem:
I tried installing xubuntu 8.04 on my desktop, no big deal, done it with ubuntu feisty, shouldn't be a problem. I deleted the existing partitions with Ubuntu with gparted, ran the installer from the Live CD, told it to use largest free space.

Somewhere in the tinkering, some of my system's partition tables got scrambled: gparted "thinks" that my hard disk is empty, even though the XP partition is bootable, and the recovery partition is also bootable.
fdisk -l yields no info on /dev/sda (the relevant disk drive)

Searching the forums and with Google has yielded no useful ideas so far.

Suggestions would be welcome.... (I'll probably be coming back to check in about 12 hours)

EDIT: IT's getting late, hope the above is coherent enough to suggest answers, I can always make a backup of the partitions and try running the recovery partition to restore factory defaults, but don't particularly fancy it since I only did it the other day to clean out after-effects of malware

---

### Post by kosmiciatakuja on 2008-10-03
This is just a guess but if you have an empty disk, just create the partitions there (with parted, fdisk or whatever), then create filesystems (with parted or mkfs), then install the OS (xubuntu, right? that's what I'm using and it rocks!). It _should_ work...

As for windows still booting, as far as I understand this, is that removing partitions only erases the partition table, the data and partition headers are still there. So if windows boot manager knows where to start reading the boot code, chances are it will still boot. Who knows what's inside the code, eh?

But after you install xubuntu, the data should be overwritten, so _then_ you should not be able to boot windows. 

That's what I think at least, I may be wrong...

---

### Post by lisati on 2008-10-03
Thanks. I had another look. After doing a "fixmbr C:" from the Windows Recovery Console (the C: was necessary otherwise fixmbr would have knobbled the recovery partition), and checking with a Feisty Live CD, I noticed an error message I hadn't seen before when running fdisk (possibly caused by running it without the C: in a previous attempt to fix things)
> [COLOR="Red"]Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)[/COLOR]

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         832     6289888+   c  W95 FAT32 (LBA)
/dev/sda2   *         833        9524    65711520    7  HPFS/NTFS
/dev/sda3            9525       10337     6146280    5  Extended


A quick search of the forums suggested a solution [here]("http://ubuntuforums.org/showthread.php?t=889843")
> ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 10337.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         832     6289888+   c  W95 FAT32 (LBA)
/dev/sda2   *         833        9524    65711520    7  HPFS/NTFS
/dev/sda3            9525       10337     6146280    5  Extended



Now to see if windows will boot (running of Live CD at the moment)

---

### Post by lisati on 2008-10-03
I'm marking this one as solved, and due to a lot of bumbling caused by inexperience and a big head (on my part)

EDIT: it seems that some of my initial woes were in part caused by the particular machine taking a dislike to XP service pack 3. I installed the available updates for XP, and was back to the point of having windows not starting (actually restarting while the XP splash screen was showing). Solved by logging in with "safe mode" and removing servie pack 3.

---

### Post by lisati on 2009-02-01
> **lisati said:**
> I'm just about off to bed after spending several hours mucking around, and suggestions would be appreciated.

Synopsis of problem:
I tried installing xubuntu 8.04 on my desktop, no big deal, done it with ubuntu feisty, shouldn't be a problem. I deleted the existing partitions with Ubuntu with gparted, ran the installer from the Live CD, told it to use largest free space.

Somewhere in the tinkering, some of my system's partition tables got scrambled: gparted "thinks" that my hard disk is empty, even though the XP partition is bootable, and the recovery partition is also bootable.
fdisk -l yields no info on /dev/sda (the relevant disk drive)

Searching the forums and with Google has yielded no useful ideas so far.

Suggestions would be welcome.... (I'll probably be coming back to check in about 12 hours)

EDIT: IT's getting late, hope the above is coherent enough to suggest answers, I can always make a backup of the partitions and try running the recovery partition to restore factory defaults, but don't particularly fancy it since I only did it the other day to clean out after-effects of malware

Apparently some of the woes I'd been experiencing turned out to be related to installing XP SP3 on Compaq machines with AMD64 cpus.There's a patch available at Compaq's website.

---

