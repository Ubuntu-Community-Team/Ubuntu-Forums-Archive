---
title: "Missing Operating System - Flubbed GRUB"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Kerry Lange on 2006-10-29
Hi there:

A newbie here.

I tried back in June to get the live demo to work but failed.  So, I finally tried to just install the system but with even less luck than with my live demo.

Here's my system:

160 GB drive 1 on ATA RAID - NTFS
160 GB drive 2 on ATA RAID - NTFS
320 GB WD drive for data files - NTFS
320 GB Seagate drive for Ubuntu

The two drives in the RAID are connected to a PCI card.  The two 320 GB drives are SATA connected to the MB.

I have a bios where I can specify the drive I'm wanting to boot.  Normally, I specify the RAID drive (the two 160 GB drives) for booting Win XP.

For installing Ubuntu, I specify the Seagate drive for the installation (and as the drive to boot from the BIOS), then boot to the installation CD.

Installations 1 - 4
-------------------
I partitioned the Seagate drive into a system partition and a swap partition.  Each time booting, I got "missing operating system."

During these four installations, I tried the repair mode and tried reinstalling the GRUB loader to one of the Ubuntu partitions I'd created.  Either I got an error message telling me the system couldn't install the GRUB loader or I was simply taken back to the menu where I could select between the various options available for the partition I was working on.

After the fourth try, I decided to simply boot Win XP again so I set the bios to use the RAID drives.  Instead of the usual XP boot choices, I got a screen filled with "GRUB" printed over and over.

So, I fixed the MBR but found "ntldr" was also missing.  I copied "ntldr" from the XP install disk and all was well again.

Installation 5 & 6
------------------
Thinking my problems might have something to do with having a partition on the Ubuntu drive (Seagate), I then created three partitions--one for booting, another for swap, and a third for the rest of the files.

Of course, nothing worked.  On trying to boot XP again, I ended up with "GRUB" printing to the screen again.  So, I fixed the MBR (but "ntldr" was still there for some reason this time) and booted XP again.  And that's where I am.

Can someone tell me how I can get Ubuntu to boot from my Seagate drive, rather than messing up the RAID drive?

Kerry

---

### Post by Amon_Re on 2006-10-29
I have a simular issue with my system (multiple disks, sata & pata), the problem is that grub installs into the wrong disk, your raid disk is being seen through grub as drive 0, and when you select your other disk, that disk is changed to disk 0 instead, while it might actually be disk 1, or disk 2...

You need to do a grub-install /dev/<disk><partitionnumber> to get grub on the  proper disk, and then use testdisk to restore the bootloader on your ntfs drive.

---

### Post by Kerry Lange on 2006-10-29
Okay, how do I do the Grub install (via the Repair Mode?), what's testdisk, and how do I access testdisk?

---

### Post by Kerry Lange on 2006-10-30
Okay, I disconnected the RAID drives and the other 320 gig drive I have.  I then installed Ubuntu without any problems.  I rebooted without re-connecting the other drives and Ubuntu ran fine.

However, when I reconnected the drives, I get the following error while trying to boot to the Seagate drive:

/bin/sh: can't access tty; job control turned off

I get shell I guess I'm supposed to use to fix the problem.  Unfortunately, I haven't got a clue how to fix the problem.

Anyone know what I can do to fix this?  Is there a boot file I can edit to get the system to run with the other reconnected drives?

---

