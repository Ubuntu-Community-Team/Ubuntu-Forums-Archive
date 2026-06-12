---
title: "Hard Drive Cloning Problem..."
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by stego_s_aurus on 2007-11-23
Hello all,
  I seem to have painted myself into a corner, and am hoping to find a clean way out of this dillemma...

Today I made a clone of my systems Hard Drive using dd, and at the end of the clone I found that the New drive is ONE CYLINDER SMALLER than the Old Drive, despite the fact that both drives advertise themselves as 80GB drives (The old one had 9730 cyls, the new one is 9729 cyls).

There are a total of three partitions on this drive:
/dev/sda1 is Linux swap
/dev/sda2 is the Root partition, mounted on /
/dev/sda3 is the user files partition, mounted on /home

Of course its the user files partition /dev/sda3 that is incorrectly sized on the new disk.

I can read and write to and from the partition with no problem whatsoever, and I know that as long as something doesn't try writing data to the end of the disk then I'm OK for now, but of course I do realize that I'm treading on thin ice and thus I want to correct this before it bites me. I know that to correct the problem, all I need to do is to resize the partition using a utility like gparted.

However, I am running into a snafu:

I can Use fdisk, go into (x)pert mode, (c)hange the size to the correct cylinder count (9729), and then (w)rite the data out to the disk, however it comes back and says "**WARNING: Re-reading the partition table failed with error 16: Device or resource busy.**" (Thats the kind of error I'd expect out of a Windows box: not a Linux box...). Obviously the data is not being written to disk as the partition is marked "Busy" somehow...

I've gone ahead and attempted to use both gparted and qparted to see the partitions: gparted simply says: "Error: Can't have a partition outside the disk!" and shows the entire disk as being unused, and qparted shows the device as being "Busy". This is even after I boot off of the Ubuntu CD-Roms to try and correct this problem!!

Is there any way to correct this partition-size problem without having to delete the entire bloody partition and redo it? theres alot of user data in there and I'm not looking forward to another several hours redoing the backup, especially since I'm running on a schedule and my allotted time is already up: Right now the new drive is running, but as I said I'm hoping that nothing tries to write to the end of the partition between now and the time I fix it.

Here's what I did to clone the drive, and where I noticed the problem:

- Powered down the machine
- installed replacement drive in second hdd slot and connected to mobo
- powered up machine, booted up using ubuntu cdrom
- double-checked with gparted to make sure my source and destinations were good (source= /dev/sda , destination = /dev/sdb )
- on terminal, I ran "sudo dd if=/dev/sda of=/dev/sdb"
- It ran for a few hours, then came back with an error informing me that it couldnt write the last 12000 blocks.

A Note: Hindsight says that I should have resized the original partition BEFORE doing the backup, but the problem is that I Have no backup in case something went wrong, and thus I didn't want to chance completely munging up my only copy of the partition: rather, I'd rather work with a munged working partition and fixing it somehow...

- I rebooted onto the CD, and tried the fdisk command I mentioned above to fix it, no dice. Qparted, gparted donesnt want to touch it as I explained above. cfdisk just says something along the lines of "Fatal Error: partition extends beyond end-of-disk!" and dies.

And heres where I'm stuck. The wacky thing is that the system reads, writes to the partition no problem whatsoever.

Is there any way to FORCE a write of the partition table, or somehow "unbusy" it or mark it as "idle"?

ugh. Help on this would Definitely be appreciated. The next time I can attempt to do a backup like this onto a larger drive would be over the Xmas holiday.

---

### Post by Pumalite on 2007-11-23
Check your drive:
Rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by stego_s_aurus on 2007-12-11
Helo there!
  I tried sysreccd and the tools on there are giving me the same errors. It appears I need some additional help with this.

> **Pumalite said:**
> Check your drive:
Rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

