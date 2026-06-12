---
title: "I need some help installing Ubuntu on a CF card"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by tackle on 2010-03-01
I have built a small computer with low power draw (<20watt) which I want to use as:

- File server, both locally and possible to access from outside the network
- Backup server, automatically back up my two desktop computers
- Torrent downloader

I've chosen to go with Ubuntu desktop 9.10 for this. Would Ubuntu server be more ideal for this? I wont be using the computer in day-to-day basis, just let it do its work.

Anyways; my computer is this:
Motherboard: Intel D945GSEJT
1 gig ram
4 gig Sandisk Extreme IV (45 MB/s) Compact Flash card, in a CF > IDE adapter.

I've created a bootable installation USB-drive. I fire up the computer and I can boot into Ubuntu fine with it, everything seems to work.
However, when I try to run the installation onto the Compact Flash card I run into trouble when it tried to format the file system:

It gives me an error dialog box saying "Could not create file system", "Failed creating a ext4-filesystem on partition nr.1 on SCSI1(0,0,0)(sda).". (Might not be word for word, I'm running swedish installation).

So of course I've started messing around with the CF's partitions and whatnot inside of GParted. I've managed to format the card to ext2. However if I run the installation again I'm forced to choose between:
- Erase and use entire disk. If I pick this I'm back at step one, same problem as above.
- Speciy partitions manually.
Of course I pick choice no. 2, and here I can see the device /dev/sda, with /dev/sda1 (type: ext2, size 4104 MB).
I'm forced to choose a root file system so I double click /dev/sda1 and choose use as ext2 file system, and I pick "/" as the Mount point.
Trying to go forward from here gives a dialog box saying "ERROR!!!" - "File system has an incompatible feature enabled. Compatible features are has_journal, dir_index, filetype, sparse_super and large_file. Use tune2fs or debugfs to remove features.

I go into the partitions settings once again and this time check the "format" checkbox. This time it allows me to continue. I accept that I wont be using any swap space by hitting continue.

This time during the installation I only get a dialog box saying "Do you want to resume partitioning?" - "The attempt to mount a file system with type ext2 in SCSI1(0,0,0) partition #1 (sda) at / failed. You may resume partitioning from the partitioning menu."
Go Back or Continue.

This is as far as I can get. I have no idea how to install Ubuntu Desktop on my Compact Flash card. It does indeed show up as a IDE device, and Ubuntu sees it as a SCSI device I assume (from the naming).

Can anyone give me any hints on what to try? Surely someone must've gone through the same steps as me but with success?

Should I somehow ever get this working, I wonder if anyone has any tips on how to setup the system so it doesn't write a lot of unnecessary data onto the CF card, since I want to keep the lifetime at a max if possible.

---

### Post by tackle on 2010-03-02
Should I ask this question in another part of the forum, or another forum?

The activity in this one is insane!

---

