---
title: "fresh install dumps to busybox please help !!!!!"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by mitch707 on 2008-05-25
I installed ubuntu hardy off the live cd (which worked perfectly) and after the install i rebooted and the little orange loading bar goes for a really long time and then i am dumped into busybox with this error: check root= bootarg cat proc/cmdline or missing modules, devices : cat /proc/modules ls /dev ALERT! /dev/disk/by-uuid/dfb20e59-84c3-4984-9357-c732b74f8d7e does not exist. dropping to shell

my specs are:
amd anthlon 64 1.2 ghz i think
1gb of ram
2x nvidia 7300 le cards
kn1 sli lite mobo
350gb maxtor HD

ive also booted into the live cd and tried to mount my hard drive but it says cannot find in mstab or fstab but when i do fdisk -l all the partitions show up but i cant mount them

---

### Post by Pumalite on 2008-05-25
Boot you Live CD and run:
sudo fdisk -l

---

### Post by mitch707 on 2008-05-26
okay i did and it shows the partitions /dev/sda1 /dev/sda2 /dev/sda5 and i cant mount them and the suse installer cant delete the partitions and the gparted live cd doesnt work so im really stuck

---

### Post by Pumalite on 2008-05-26
Check your drive with TestDisk:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by Ryude on 2008-05-26
Mine does the same thing.

---

### Post by outstandish on 2008-05-26
Me too (64 bit version on Shuttle SX38 P2 pro). Seemed to occur only sometimes and then the live CD wouldn't even boot. Got that going with the acpi=off switch added using the F6 key, but then the mouse was unusable...

---

### Post by Ryude on 2008-05-26
I got it to work by re-installing from live CD, this time however I did "Guide - Whole Drive" instead of partitioned.

Everything seems to work fine now.

Anyone recommend some packages after a fresh install of 7.10? I'm a noob at this ubuntu thing.

---

### Post by Pumalite on 2008-05-26
Try this:
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by outstandish on 2008-05-27
snip>Whole Drive<snip

There may be something in this; it installed fine on another machine where it was the only OS, though I did partition that drive. On my Shuttle it seemed to work fine, at first, when I had a separate boot primary partition. Then on booting up it started to  hang (most times) at busybox with the "ata 3.0 revalidation failed (errno=-5)" message. So I think it is a bit random.
Spent a lot of time eliminating faulty hardware (swapping drives, controllers and cables). I would try the acpi=off parameter on booting but I guess it will make the mouse unusable and in any case I have nuked the root partition with badblocks during my diagnostics.
:confused:

---

