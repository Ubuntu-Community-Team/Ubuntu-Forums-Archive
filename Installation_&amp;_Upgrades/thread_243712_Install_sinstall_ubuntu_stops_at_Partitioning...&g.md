---
title: "Install sinstall ubuntu stops at Partitioning...&gt;"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by Scoobsky on 2006-08-25
Hi all,

Just got my new Toshiba Tablet PC M7 (out of the box today!).
It came with standard doze for Tablet PC Edition

trying to install ubuntu 6.0.6.

I get to the stage of resizing the Disc Drive sda1 so I select an appropriate size but then clicking Forward just does nothing at all... all I get in a egg time and that is it.

I booted with the live CD so Im wondering if I need to do anything to run the Install icon as root instead so that it is allowed to repartition the disc.

Any ideas greatly appreciated. 

Thanks in advance
M.

---

### Post by orb9220 on 2006-08-25
If you have os on thier already you may want to defrag it from windows side.

That was my problem when the disk is to fragmented gpart chokes.
After running defrag a few times then it worked like a champ.

Sorry couldn't be more help.

---

### Post by randell6564 on 2006-08-25
Hi!

Have a look at this [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

I have another link that I would like to show you on another drive, so I will be back!  Leave you with this.,There is not much Linux support regarding S-ATA devices.

---

### Post by randell6564 on 2006-08-25
Hi!

Here is something that Everyone using S-ATA raid devices should read:

[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

---

### Post by jldugger on 2006-09-24
I don't know if you've ever solved the repartitioning problem, but I encountered the same exact problem. Its a bit strange, but if you search the forum for resizing ntfs, there's a guide or two out there. They all recommend using the manual partitioning rather than the somewhat obvious and simple "resize and use freed space" option. Anyways, just reboot the liveCD (if you cancel out of the installer I think the partitions you want to resize get locked or something because its halfway done), and choose manual repartition. Then just use the interface to parted to resize the desired partition to have enough free space, and make both a swap and a root partition. Hopefully this is fixed on edgy?

---

