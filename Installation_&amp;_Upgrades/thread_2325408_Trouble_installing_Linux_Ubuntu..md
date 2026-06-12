---
title: "Trouble installing Linux Ubuntu."
date: 2016-05-22
forum: Installation &amp; Upgrades
---

### Post by Joseph_Arvanitis on 2016-05-22
I am trying to dual boot Windows 10 with the latest version of Linux Ubuntu but while trying to install it I had some complications. Prior to starting the installing process I had created a 48GB partition on my HDD but I didn't format it so now its empty. Midway through the installation wizard, due to an error message, I found out that I need to create a swap partition, sized two times bigger than the RAM of my system. After creating it using 16GB out of the 48GB, somehow the UEFI boot became involved. I know my Windows 10 uses UEFI boot, and I am confident that the USB stick I am using is booted in UEFI mode as well. From what I've seen so far, I am supposed to create a UEFI boot partition, a main partition and a swap partition. I am extremely confused right now.

What I need most right now is step by step instructions as to how to dual boot Linux Ubuntu with Windows 10 (both in UEFI mode). I currently have an empty, non-formated partition of 48GB intact (I deleted the swap partition). What should I do now?

---

### Post by RobGoss on 2016-05-22
Hello and welcome to the forum, I think you might want to read this help guide so you have a better understanding how to dual boot Windows and Ubuntu, [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)


I think the most important thing to remember here is what ever boot order you have Windows 10 in you'll need to install Ubuntu in as well, Example UEFI or Legacy, in oder to choose what operating system you would like to run. As far as the Swap partition is concern I only have a 2-GB for my Ubuntu 16.04 and it seems to be more then enough with out any problems

---

### Post by kansasnoob on 2016-05-22
The link posted by RobGoss is outdated and deals with older msdos/mbr/bios mode installs. Better to look here:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Windows and Ubuntu will share the same uefi/boot partition. If you have 8GB RAM I'd only create an 8GB Swap partition so the machine can hopefully hibernate properly. Before we could give any really detailed info we'd need to see what your current partitioning looks like since you were part way thru an install and aborted. An easy way to do that would be to use the Ubuntu live media, choose to Try w/o installing, and from the live DE post a screenshot of Gparted.

---

### Post by Joseph_Arvanitis on 2016-05-22
Well I actually completed the installation before I saw your reply, so currently there are 2 UEFI boot partitions, a 16GB swap partition, a 775GB windows partition and a 32GB linux partition along with a bunch of other backup partitions. Windows (which I am on currently) shows a total of 9 partitions but Linux showed 2-3 more. Now I am more conserned about how my HDD is going to handle this, considering its relatively low-end and not the newest ever.

---

### Post by oldfred on 2016-05-22
The UEFI spec allows two ESP - efi system partitions, but many vendor's implementation of UEFI, does not work with more than one ESP per device.
Do both systems boot ok? If so then ok, but may be better to only have one.

Or is only one FAT32 partition show boot flag (which is only gparted's way of making it an ESP)? And one system boots.

With UEFI, and gpt you do have more partitions. Several are required, some unformatted which may show as errors in gparted but are ok.

       But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by ajgreeny on 2016-05-22
>  I found out that I need to create a swap partition, sized two times bigger than the RAM of my system. After creating it using 16GB out of the 48GB, somehow the UEFI boot became involved.
That advice is now very much outdated and most users make a swap of 2 - 4GB only, irrespective of the amount of RAM they have.

I assume you have 8GB of ram from what you've said and with that you will be unlikely to use swap at any time, other than perhaps running any virtual machines in, for example, VirtualBox, should you use that.  The only situation where RAM must be at least equal to or larger than the RAM amount is if you wish to hibernate, which not many use these days.

If both OSs boot fine I would be inclined to leave things as they are; if you have difficulties with one or other OS maybe you should consider reinstalling Ubuntu, making sure that you follow the instructions in that link from kansasnoob, but maybe this time using only 2 - 4GB swap.

---

