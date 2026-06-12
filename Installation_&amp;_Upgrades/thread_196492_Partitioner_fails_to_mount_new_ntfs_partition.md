---
title: "Partitioner fails to mount new ntfs partition"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by Oblong_Cheese on 2006-06-14
Hi all.

After the partitioner nuked my NTFS partition while trying to resize it (got my data back with GetDataBack NTFS -- so it's OK, and my fault for not backing up in the first place), I tried a second attempt at installing Ubuntu 6.06.

My partitions I setup as follows:

IDE1 - WD1600JB (160Gb)
IDE2 - WD1200JB (120Gb)

hda1 -> existing XP drive (10Gb) -> /windows
hda2 -> new partition, formatted to NTFS (~65Gb) -> /games
hda3 -> new partition, formatted to ext3 (~65Gb) -> /
hda4 -> new partition, formatted to swap (1Gb) -> /swap

hdb1 -> existing NTFS partition (~110Gb) -> /multimedia
hdb2 -> new partition, formatted to FAT32 -> /shared

This is all fine and dandy until I come to creating and formatting the partitions. Every one is created and formatted fine, except the newly created NTFS partition, which gives an error like the following:

"The attempt to mount a file system with type ntfs at IDE1 has failed"

This is annoying but not really a problem; although the installer gives me the option to go back, I cannot circumvent this issue, so I must progress by letting the installer format this partition as ext3.

I will simply format it again from Windows to use as my games drive in Windows, and will have to edit fstab so Ubuntu doesn't die on me. ;-)

Anyway, I was wondering if anyone knew why this problem is caused and a way of fixing it properly, instead of working around it?

Thank-you.

---

### Post by rcarring on 2006-06-14
What type of partitions have you setup?

Are their all primary on hard disk 1? Is there an extended partition containing logical drives?

Also if hdb1 is primary it will be seen following hda1 in the partition schema.

---

### Post by Oblong_Cheese on 2006-06-14
Yes, all partitions were set to be primary partitions -- though this should not be a limitation, as there are four logical partitions per drive allowed.

So are you saying that if hdb1 is set as a primary partition, it will 'follow' hda1 in some way? I don't fully understand what you mean by this.

---

### Post by rcarring on 2006-06-14
Under XP the order of drives is dictated as follows:

List primary on first hard disk
List primary on second hard disk if there are no more primaries on first hard disk, else list primary
Repeat until all partitions that are primary are listed
List first logical partition on first hard disk
List successive logical partitions on first hard disk
List first logical partition on second hard disk
List successive partitions on second hard disk

This is the case with my setup, although I have a usb external drive as my second hard disk.

Now, I am assuming that Linux would use the same listing schema I have shown above, if it doesn't then no doubt someone will correct me.

---

### Post by Oblong_Cheese on 2006-06-14
Alright... that may be so, but how has it caused the problem I described above? I am still not following your line of thought, sorry.

It shouldn't matter what order the partitions are enumerated in, the failure point was during the mounting process.

Unless I'm totally wrong. :-)

---

