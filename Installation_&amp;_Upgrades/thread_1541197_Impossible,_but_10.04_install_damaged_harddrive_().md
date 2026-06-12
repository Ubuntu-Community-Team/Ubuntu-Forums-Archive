---
title: "Impossible, but 10.04 install damaged harddrive (???)"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by rnsc on 2010-07-28
TWICE:

Working hardware, could go into setup, boot Linux CD, known good hard disk.

Installed 10.04 desktop.  Installation successful.  On reboot, the BIOS processes hang.  It recognizes that it has an IDE hard disk, and ATAPI CD-ROM, then it lists the hard disk vendor, model, and notes that it is SMART compatible.  Then it hangs.

This includes if I "Hit delete to enter setup", so that it is not trying to boot!

The hard drive is on the Primary IDE, the CD/DVD on the secondary.  Both are configured as a "single" drive.  

If I unplug the CD/DVD drive, same thing (Hangs).

If I unplug the hard drive, then the BIOS continues, lists the CD/DVD vendor and model, and enters setup or boots.

It *appears* that the 10.04 installation did something to damage the hard drive.  I know of no mechanism by which this could happen.

The first time I figured that the hard drive failed at a coincidental time.  But now it has happened, exactly the same, to a SECOND hard drive!

Are there any processes that might update the hard drive firmware or configuration behind my back?  Both are Western Digital 120GB.

Any ideas?  Anybody ever seen anything like this?

Thanks.

---

### Post by laimigrante on 2010-07-28
i dont think any os could damage the hard disk, with the live cd of ubuntu or maybe mint you could see is there any problem in any sector of the hard disk.
 in ubuntu go to system, administration,  disk utility, click on ur hard disk and chose smart data, in there u will see if something is wrong with ur hard disk and wich sectors.
if something is wrong maybe Hiren's BootCD would help.
 [http://www.hirensbootcd.net/](http://www.hirensbootcd.net/)

---

### Post by rnsc on 2010-07-29
The system will not get to accessing the CD-ROM or hard disk.  It will not boot with the hard disk plugged in.  It will not get through the BIOS process.  I cannot boot the live CD with the hard disk plugged in.  The presence of the hard disk causes the system to not work.

This same disk was happily running Ubuntu 0810 just before I turned it off to install 1004, and had been for about six months.  It was turned off and on perhaps every day or 2 or 3, always worked perfectly.  

The second disk had been off for six months, having been running up until then running ... 0810 at that time.  When I replaced the first disk, the machine got through the BIOS fine, booted knoppix.  I zero'ed the disk (my normal process), then booted the install CD.  The install worked fine.  When the install rebooted, the disk failed to allow the BIOS to progress, just like the first disk.

If I unplug the CD/DVD drive, same thing.

If I unplug the hard disk, the BIOS progresses fine with the CD/DVD plugged in.  

We either have two hard disks that happenned to fail in exactly the same way, at exactly the same point in the Ubuntu install process (Working right up to an including the shutdown after install, but failing 5 or 10 seconds during the reboot,  OR   Ubuntu did something to the configuration of the drive during shutdown or during install that takes effect on the next power-up that makes it non-functional.

The probability of the former is astronomically small.  I vote for the later.  I don't have too many more hard drives to brick, and I really don't want to do so.

Does Ubuntu (Install) do any hdparm commands to change the drive?  I can't poke around because I can't install it - it bricks the drives!

---

### Post by efflandt on 2010-07-29
You have not given any details of your hardware.  One thing that is new in 10.04 related to partitioning is that by default, it aligns to MB boundaries instead of cylinder boundaries, and that is not compatible with some motherboards or BIOS (like my HP a530n desktop with Asus mobo from 2004).

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems)

If that is the case, you may need to use **partman/alignment=cylinder** when booting the install CD (or create your partitions first with older Ubuntu version).  And it would also be a good idea to include it in this line of /etc/default/grub:  GRUB_CMDLINE_LINUX="partman/alignment=cylinder"

Fortunately I sorted that out while testing 10.04 from a USB hd, before I installed 10.04 on the internal drive of that old desktop.

---

### Post by laimigrante on 2010-07-30
i install ubuntu 10.04 in a old compaq presario desktop and works fine, i will read more about that just to be sure before i install ubuntu in other computers.

---

### Post by clarkkillick on 2010-09-13
rnsc,

regarding your "either / or" above: I have thought of a third possibility.  It may be something to do with the contents of the disk since the install.  Maybe your BIOS or mainboard doesn't like something about the new contents.  Things you could try:

(1) Try the non-working disks on another machine to see if they are recognised.

(2) If (1) works, use the second machine to wipe the disks.  Then see if the original machine recognises them again.

If you get any more info on this please post a follow-up, as it is rather worrying.  I've never seen anything like this before.

---

### Post by kerry_s on 2010-09-13
try changing you ide cables. for example the 1 from your cd.

---

