---
title: "want to overwrite existing linux distro"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by aviceda on 2007-05-14
I was intending to add Ub 7.04 to a dual-boot XP and overwrite a Fedora 6 installation but noticed that the partitioning tool when installing doesn't 'see' the linux partitions. Any advice?
Tom

---

### Post by earobinson on 2007-05-14
Screenshot?

---

### Post by tkainz on 2007-05-15
I'm actually in the same boat so if you don't mind, I'll throw my information in also - :

I currently have a Laptop with an 80 Meg HD which is currently partitioned as follows (per GParted)
/dev/hda1 - Filesystem: NTFS, Mountpoint: /media/disk-1, Size: 33.47 GiB, Flags: boot
/dev/hda3 - Filesystem: reiserfs, Mountpoint: /media/disk, Size: 29.29 GiB, Flags: (null)
/dev/hda4 - Filesystem: fat32, Mountpoint: /media/COMMON, Size 9.77 GiB, Flags: lba
/dev/hda2 - Filesystem: extended, Mountpoint: (null), Size 2.00 GiB, Flags: lba
Under hda2 - /dev/hda5 - Filesystem: fat32, Mountpoint: /media/DISE_BACKUP, Size: 2.00 GiB, flags: (null)

All partitions appear to be locked (by evidence of a lock icon after the partition name)

hda1 is the current Windows XP version
hda2/hda5 is the partition containing the XP backup which was installed at the time of purchase
hda3 is a current install of "freeespire" which I would like to overwrite with Ubuntu
hda4 was a 'common' partition which I created to allow access to files form XP and Freespire

When I run the Unbuntu install the options I am given are;

1. "Guided - resize IDE1 master, partition #4 (hda4) and use free space"
2. "Guided - use entire disk"
3. "Manual"

While I really do not hold any afinity to Windows and would love nothing more than to choose option 2 - "Use entire disk", I need to finish first making sure I can find comperable linux programming to do all that I have to do.  Ideally, I would like to install the current version of Unbuntu in the same partition I have currently set up for Freespire (overwrite Freespire) - this would be in hda3 and then once I have everything set up as needed and have installed all the necessary programs I can then trash the Windows partition and free myself from the clutches of the Windows deamon forever.

If I choose the "Manual" option I am presented with a "Prepare partitions" dialog. And here is where I'm stuck.  I don't want to go into unfamiliar territory and end up trashing the Windows partition (just yet).

In the "Prepare partitions" dialog box, hda's 1,3,4 and 5 are all listed and hda3 has a check box which (presumably) allows the partion to also be formatted.  Underneath the list of partitions are the option buttons: Edit Partition, Delete Partition, Undo changes to partition.

Where do I go from here so I can have a dual Windows / Unbuntu boot option at startup.

I really would appreciate any help you could offer.

Thanks in advance.

---

