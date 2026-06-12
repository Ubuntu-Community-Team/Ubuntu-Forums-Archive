---
title: "Format Dell XPS Disk from USB"
date: 2013-10-09
forum: Installation &amp; Upgrades
---

### Post by sochin on 2013-10-09
I have a XPS box with Vista.

Also have a 13.04 bootable install USB that has successfully
installed on 2 similar machines.  This machine will boot to 
Vista and run, but the 13.04 install hangs. 

Running the BIOS hard disk check does find some problems.
So I assume that a hard disk problem is preventing the boot
or install from the 13.04 USB. 

So... I'm looking for a way to create a disk or usb that has
just the tools needed to boot this box and format the disk
so that a subsequent 13.04 install will work.

Thanks.

---

### Post by fantab on 2013-10-09
Can you "Try Ubuntu without Installing" on your XPS box?
If yes, then you can use GParted to format your HDD. But before you do that I'd recommend you to run HDd 'defragmentation' from Vistas. Run it a couple of times. 

How many Partitions do you have? The legacy 'msdos' partition table can only have 4 Primary Partitions, that is the limit. If you force a 'fifth' then Windows will convert your HDD from 'Basic' to 'Dynamic', and Dynamic disks don't work with Linux. 

It would help if you can post a screenshot of your Partitions from Vista.

---

### Post by sochin on 2013-10-09
After some more digging, I was able to 'solve' the problem with
the boot-repair-disk ([http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)).

I burned boot repair onto a CD, then by tweaking the boot parameters
(F6 in Boot Repair) was able to boot from the CD. 

Was then able to use gparted to wipe the disk and install 13.04.

Thanks for the help!

---

