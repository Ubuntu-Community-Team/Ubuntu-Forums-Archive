---
title: "Cannot change partition table?"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by Csutcliff on 2012-12-19
Hi, I recently decided to put ubuntu on my eee 1000 rather than windows 7. The problem I'm facing is that whatever changes I make to the partition table (be it via fdisk, sfdisk, gparted, ubuntu installer) are lost as soon as I exit the application, reverting to the old partition table. nothing seems to stick.

None of the applications report any errors in what they are doing, but next time you load them you are right back where you started. I've even tried using parted magic to the same effect.

Help!

---

### Post by darkod on 2012-12-19
Depending on the program, are you sure you are applying the changes? For example in Gparted you have to hit the green button to apply, otherwise it doesn't do anything.

Another thing is that if some partition is mounted and unable to be changed while the OS is running, you might need to reboot to see the change. But it doesn't sound like this is your issue because after a reboot the partition table would be changed.

What changes are you trying to do? Can you post the output of:
sudo parted -l

and explain what do you want to change?

---

### Post by Csutcliff on 2012-12-19
> **darkod said:**
> Depending on the program, are you sure you are applying the changes? For example in Gparted you have to hit the green button to apply, otherwise it doesn't do anything.

Another thing is that if some partition is mounted and unable to be changed while the OS is running, you might need to reboot to see the change. But it doesn't sound like this is your issue because after a reboot the partition table would be changed.

What changes are you trying to do? Can you post the output of:
sudo parted -l

and explain what do you want to change?

Yes definitly applying changes. The partition isnt mounted anywhere.

Since posting ive managed to wipe the drive with secure erase (the only thing that actually took) but still have the same problem (albeit now with no partition table).

Creating a partition table appears to work fine however it never actually makes it to the disk.

Originally what I wanted to change was to delete the ntfs partition and create some for ubuntu, now Im trying to create a partition table and partitions for ubuntu.

Output from parted -l (removed the section for my usb stick):

> root@PartedMagic:~# parted -l
Error: /dev/sda: unrecognised disk label
Model: ATA STT_FPM64GLSE (scsi)                                           
Disk /dev/sda: 63.0GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

---

### Post by darkod on 2012-12-19
Right now it says partition table unknown. Try writing a new msdos table with parted.
```
sudo parted /dev/sda
mklabel msdos
quit
```

After that check again with parted -l whether it will say partition table msdos. If it does, try creating few partitions either with parted or Gparted.

---

### Post by Csutcliff on 2012-12-19
> **darkod said:**
> Right now it says partition table unknown. Try writing a new msdos table with parted.
```
sudo parted /dev/sda
mklabel msdos
quit
```

After that check again with parted -l whether it will say partition table msdos. If it does, try creating few partitions either with parted or Gparted.

Same result, no partition table. Parted doesn't report any errors.

I've done badblocks read/write tests and the read test is fine but the write test fails every block from 64 onwards,

It seems as if the disk is read only although it reports that it isnt in hdparm.

Any ideas?

---

### Post by darkod on 2012-12-19
Not really. But it's becoming to sound like a hardware issue. All partitioning software doesn't work. It doesn't look like software issue.

---

