---
title: "HOWTO install Ubuntu 9.04 on RAID0 (ICH10R)"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by Anton T. on 2009-12-10
Hello! It's my first HOWTO. I'll be glad to see some responses!

So... My system:
Intel i7 940
ASUS P6T SE ICH10R
HDD 2 x 750Gb
DDR3 12Gb

That motherboard supports semi-hardware raid... (fakeraid you know..) 
In BIOS >> Storage config >> SATA - RAID >> F10
Then Ctrl+i after rebooting for opening RAID manager. 
Then I've chose 1. Create new device...
I've made first device: Volume name - DATA, RAID0, size - 1370Gb  and all by default. 
Second device: Volume name - SWAP, RAID0, size - 20Gb  and all by default. 
Then I've pressed Ok and Yes in every next window.
Hardware is ready to install OS!

**Use Alternate CD or DVD only!!!!** (I've tried both. Works well!)

Insert your alternate CD or DVD in your drive.
Press Install... set up all settings as you wish untill you'll see window with question:
Activate RAID...? Press YES.
Then use auto-partitioning for all your space.
You'll see 2 raid drives. First 1.4 TB, second - 20GB.
Open the first one. Set:
Primary - Beginning - Use as Ext4 - Mount point "/" - Boot flag "on"
Second drive:
Logical - Use as swap - boot "off"
And then save all changes and continue installation.
After finishing... VOILA! All works fine!

My speed increased almost in twice! 200-300Mb per second! OMG its real on HDD with 7200... fake-software RAID0 rulezzzzzzz!!!

Oh yeah... Before this way I tried some manuals from ubuntuforums but I didnt get success. Hope I'll help someone!

---

### Post by mkfs on 2010-07-13
Thanks, that was pretty useful, and got me up up and running in a hurry.

I had some problems installing that I will make a note of here, for posterity.

I had two RAID drives configured, one of which was /home. Both / and /usr were on non-RAID drives.

The installer failed ("Failed to create a file system") to format the partition on both of the RAID drives, so I had to switch to another VTY (ALT-F2) and create them directly (mkfs.xfs -f /dev/mapper/DRIVE_NAMEp1). This may have been caused by an aborted FreeBSD install (I originally planned to use FreeBSD, until I discovered empirically that it doesn't play well with SATA3 ... but that's a story for another day).

I selected 'do not format' for these two partitions. The installer was able to continue, then puked on "remove operating system files" ("Failed to remove conflicting files") -- trying to delete stuff from /home, because it hadn't had to format it, only there was nothing in the /home directory. A very silly and very stupid error, made all the more stupid because it prevents the installer from continuing. Still pondering in what universe it makes sense to prevent an install because an empty drive does not contain files that are to be deleted.

Switching the /home partition to 'do not use' fixed this. I'll do the ole tarcp [tar cpf - . | (cd /mnt/home && tar xvpBf -)] to move the contents of /home onto the RAID partition once the install finishes.

---

