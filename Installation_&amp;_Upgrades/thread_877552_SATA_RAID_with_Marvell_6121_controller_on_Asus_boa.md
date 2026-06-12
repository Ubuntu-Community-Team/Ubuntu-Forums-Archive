---
title: "SATA RAID with Marvell 6121 controller on Asus board"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by Featherstone-Hough on 2008-08-01
Greetings.  I'm trying to install Hardy 8.04.1 on a new system with an Asus M3A32-MVP Deluxe motherboard, a Phenom 9850 cpu, and two WD 640 GB HD's which I want to be a RAID 1 array.  There is an optical drive on the board's only PATA connector, from which I'm running the install CD.  The board actually has two RAID controllers on it, a Marvell 6121 controller and an AMD SB600 controller.  After a great deal of trial, error, and net searching, I've discovered that both controllers can't be enabled at once, hence the PATA optical drive for the installation.

The problem:  The Ubuntu installer won't recognize a RAID array on *either* controller.  But let's consider the Marvell 6121 first.  With the 6121 enabled and SB600 disabled in BIOS, and the RAID 1 array defined in the Marvell RAID BIOS, the Ubuntu installation gets up to the point of detecting disks -- and throws up its hands, saying "No disk drive was detected" and offering to let me choose a driver from a list (or supply my own on a floppy).  

What to do here?  Am I missing something?  Is there a driver I can grab from somewhere?  (I've searched, to no avail.)  Everything looks right in the BIOS settings, and I'm pretty sure the disks themselves are fine.  

As a footnote:  If I switch to the SB600 SATA controller and attempt to make a RAID 1 array, I go through the right steps in the BIOS, etc., and this time the Ubuntu installer recognizes the disks -- as *two separate* disks which I'm given the choice to format individually, but no a RAID 1 array.  What gives?  In my searching online I found a procedure for manually setting up software RAID during the installation, but the whole point of getting a motherboard with RAID controllers was to have... hardware RAID!  Is this board just cursed or something?

I'd be hugely appreciative of any help or insight...  I'm kind of at my wit's end here and not sure what else to try.  Many thanks!

---

### Post by y@w on 2008-08-01
Sometimes on RAID controllers there's an option to make it emulate a PATA or IDE device.. is there an option on the RAID card or BIOS like that? If so, it'll make the kernel think it's just an IDE hard drive.

---

### Post by scarf on 2009-05-25
> **Featherstone-Hough said:**
> Greetings.  I'm trying to install Hardy 8.04.1 on a new system with an Asus M3A32-MVP Deluxe motherboard,

hey, i have the same board.

> **Featherstone-Hough said:**
> [...]After a great deal of trial, error, and net searching, I've discovered that both controllers can't be enabled at once, hence the PATA optical drive for the installation.

isn't that a bitch? i just found that out today.  the specs for the board do not indicate only one can be used at once.  it seems this problem has existed for at least 1.5 years now.  i hope they fix it soon...

> **Featherstone-Hough said:**
> 
The problem:  The Ubuntu installer won't recognize a RAID array on *either* controller.  But let's consider the Marvell 6121 first.  With the 6121 enabled and SB600 disabled in BIOS, and the RAID 1 array defined in the Marvell RAID BIOS, the Ubuntu installation gets up to the point of detecting disks -- and throws up its hands, saying "No disk drive was detected" and offering to let me choose a driver from a list (or supply my own on a floppy).  
[...]

so, i already have ubuntu 8.10 installed on a single drive that i have on the SB600 controller, and i want to setup a new RAID-1 using the Marvell 6121.  the SB600 will still work but only in IDE mode.

i have found [this bug report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/335615), and [this guide](http://wiki.debian.org/pata_marvell) which has helped me to get linux to at least see the two disks attached to the 6121.  however, it is detecting them as two separate disks instead of a single RAID-1 disk.

---

### Post by steinaro on 2009-08-01
The RAID driver disk can be created using the support CD that came with the motherboard. Refer to the motherboard User Guide page 5-49 for more details.
Once the driver disk is created it can be used to install operating systems.

Though, to be honest, I have not yet tried to install Ubuntu with it.

---

### Post by presence1960 on 2009-08-01
> **steinaro said:**
> The RAID driver disk can be created using the support CD that came with the motherboard. Refer to the motherboard User Guide page 5-49 for more details.
Once the driver disk is created it can be used to install operating systems.

Though, to be honest, I have not yet tried to install Ubuntu with it.

The Ubuntu Live CD has zero support for RAID. You need the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by realzippy on 2009-08-02
> **presence1960 said:**
> The Ubuntu Live CD has zero support for RAID. You need the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

......that is only a need if you want a softwareraid.
Featherstone is attempting to set up a FakeRAID.Try this page:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

...by the way,why not using a SoftwareRAID?

---

