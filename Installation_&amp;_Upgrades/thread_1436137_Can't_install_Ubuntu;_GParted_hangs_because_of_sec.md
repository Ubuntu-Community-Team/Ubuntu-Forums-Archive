---
title: "Can't install Ubuntu; GParted hangs because of sector size error"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by EarthMind on 2010-03-22
Gparted won't let me install Ubuntu 9.10 64 bit. Every time it hangs at 47% and throws a sector size error, something like: doesn't support sector size 2048 and the code is HIGHLY EXPERIMENTAL.

My 1TB hard drive exists out of the following partitions:

100MB Windows 7 Reserved
900GB+ Windows 7
30GB EXT4
1MB unallocated space

Is there a workaround for this? I've tried installing Linux Mint and Ubuntu but both gave me the same error.

---

### Post by phillw on 2010-03-22
Hi,

you may want someone to verify this, as I am running from memory and the man page to refresh it (As long as there is no data on the partition, any changes can be undone)

For sake of ease, I'm going to call your ext4 partition /dev/sda3

Ensure you use the correct 'bit' for sda3 !!

From a 'LiveCD' - Do NOT try this with the drive mounted !!

If block-size 2048 is not supported (and it appears not), then reformat it to block-size of 1024.

```
mkfs.ext4 -b 1024 -L /dev/sda3
```

If you're not at the # prompt, then use sudo

```
sudo mkfs.ext4 -b 1024 -L /dev/sda3
```

Regards,

Phill.

---

### Post by EarthMind on 2010-03-22
The problem is that I have only 1 hard drive and it's automatically mounted when using the LiveCD. The Ext4 partition is empty but this partition doesn't seem to be the problem because I formatted it to Ext4 (was initially unallocated) after I got the sector size error with the hope of avoiding the error at next launch.

---

### Post by Skaperen on 2010-03-22
Enter a command line terminal and unmount it, if it was mounted ...```
umount /dev/sda1
```
The "df" command can show you where it is, if it showed up in some other way.  Then reformat per previous instructions given.

You may also want to check to see if the starting sector number is a multiple of 4.  If not, you may have caching or performance issues.  You might want to treat it as having a blocksize of 4096 in that case (e.g. sector number being a multiple of 8).  The parted command can do partitioning in exact sectors by using "s" appended to sector numbers for start and end locations (the end will be a multiple of whatever minus 1).

FYI, I now use the practice of allocating partitions at multiples of 1 MB (e.g. 2048 sectors for sector size of 512) to make sure the partitions are aligned to as much as possible (drive blocks, drive cache, OS cache, RAID striping, RAID cache, etc).  Does anyone really care if most of a MB is wasted on each end of the disk in this day and age where that would be less than 0.0002% of the space?

---

### Post by EarthMind on 2010-03-22
I managed to "fix" it by doing the following:

- Disconnect my MP3 player which was recharging
- add the 1MB unallocated space to the Win 7 reserved partition
- Execute a check & repair on the windown partitions (which actually didn't fix anything)

I suspect my MP3 player being the cause.

Anyway, thanks for the help.

---

### Post by srs5694 on 2010-03-22
The error has nothing to do with 4096-byte blocks, as Skaperen's reply suggests. The error message specifically states that the disk has *2048-byte* blocks, and AFAIK that error only pops up when the disk reports that it has that size of block to the OS, which isn't the case with the new Advanced Format disks that require careful alignment as Skaperen suggests.

My own first question is: What sort of disk is this? The only disks I'm aware of that have true 2048-byte sectors are magneto-optical (MO) disks, and you're unlikely to be using one of those as a Linux boot disk. I believe some hardware RAID controllers enable adjusting the logical block size, and it's conceivable you're using one of those that's been configured for a 2048-byte sector size for some reason. It's also possible you're using some obscure sort of disk I've not heard of before now. (I have heard of one type of external USB disk that uses 1024-byte sectors, FWIW.)

To verify your sector use, use "fdisk -l". Here's part of its output on an MO disk:

```

$ sudo fdisk -l /dev/sdd

Note: sector size is 2048 (not 512)

Disk /dev/sdd: 635 MB, 635600896 bytes
255 heads, 63 sectors/track, 19 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x00000000

```

Note the comment about the sector size ("sector size is 2048 (not 512)") and the subsequent use of "2048" in the unit computation. Both verify that the disk is communicating to the OS in 2048-byte sectors. Try running this command (modifying the device filename, of course) on your disk from a Linux emergency boot disc.

Unfortunately, although fdisk is happy with disks that use 2048-byte sectors, and the kernel and other system utilities can use such disks just fine, libparted (the basis for GNU Parted, GParted, and several other disk utilities) flakes out badly on such disks. This is a libparted bug, and I know of no way around it. The only in-Linux solution is to use fdisk or some other non-libparted tool to partition your disk, then use mkfs or other text-mode tools to create partitions on the disk.

I have no idea if the Ubuntu installer is so tied to libparted that it will object after you've set up your disk manually. If it is, you'll need to switch to another distribution, replace the hard disk, or install temporarily to another disk and then transfer your installation manually.

---

### Post by srs5694 on 2010-03-22
EarthMind, you posted your last reply about the MP3 player after I began composing my response. I'm glad you got it fixed. Since you never mentioned an attached MP3 player in your original post, I assumed (incorrectly) that the only disk was your install disk. It's now obvious to me that your MP3 player is the device with the 2048-byte sectors, and that the Ubuntu installer's libparted ties were making it flake out when that device was installed. FWIW, you should still be able to access your MP3 player in Linux, but you'll have to detach it whenever you want to use a libparted-based utility for disk maintenance.

---

### Post by EarthMind on 2010-03-22
Thank you for your reply,srs5694. Although having fixed my problem already, it's really informative :)

---

