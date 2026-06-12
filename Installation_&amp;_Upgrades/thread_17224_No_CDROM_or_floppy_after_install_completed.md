---
title: "No CDROM or floppy after install completed"
date: 2005-02-27
forum: Installation &amp; Upgrades
---

### Post by ardvark on 2005-02-27
There  seems to be alot of problems showing up with the use of SATA drives. I originally loaded Unbuntu on an old 8gig drive and almost everything worked. 

But 8gig was too small, so I purchased a 200gig SATA drivemand removed the 8gig drive.  The first problem I had (and others) was the loss of the CDROM right after installation started. That was resolved with some "insmod" entries.  THe rest of the install went OK. But now after everything is completed I have no access to the CDROM or FDC and for that matter sound isn't working either.  These all worked on the 8gig setup.  Cdrom0 and fdc0 do not show up in the /dev directory.  The /etc/fstab file looks correct as far as I can tell.  I'm think I may be seeing a problem during boot, it looks like it's skipping the ide section because it thinks it's busy or already allocated (just a guess stuff's going by too fast to see)

Any ideas??

---

### Post by alastair on 2005-02-27
Logs ....

Have a look through :

/var/log/syslog

and see if you can see relevant (hd,ide etc.) entries that point to the problem.

---

### Post by ardvark on 2005-02-27
Looking at  /var/log/syslog  the only things that don't look right are these:

 I see ATA1 being assigened to my SATA drive

but     ATA2: no udma
          ATA2: dev0 not supported, ignoring

then later on

          ide0: I/O resource 0x1F0-0x1F7 not free   (believe this is SATA drive)
          ide0: ports already in use,  skipping probe

          ide1: I/O resource 0x170-0x177 not free   (believe this to be CDROM)
          ide1: ports already in use, skipping probe

I see no reference to the CDROM or floppy in this file at all and only 1 line refering to sound card.  BIOS shows SATA drive on IDE0 master, CDROM IDE1 master. 

Neither the CDROM or FD show up on System Configuration -> Device Manager.
All worked before using the SATA drive, and looking back thru the Bug reports it looks like SATA drives have been causing problems since at least Sept.

---

### Post by alastair on 2005-02-27
The LInux kernel is a moving target - lots of work getting done. SATA is no different. A kernel upgrade might be worth looking into (or trying hoary).

---

### Post by ardvark on 2005-02-28
Looks like I've resolved the CDROM problem at least. I had to change the BIOS setting for the SATA to Enhanced SATA. This appears to force the SATA drive to IDE master 3 and with the CDROM on master 2, so it must get recognised first.  If I had more time I'd see if this fixed the original CDROM load problem.

---

