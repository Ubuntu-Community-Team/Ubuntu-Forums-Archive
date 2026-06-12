---
title: "Re-install after failed install deleted all partitions"
date: 2013-08-25
forum: Installation &amp; Upgrades
---

### Post by stephen8 on 2013-08-25
Hi,

I have an Acer Aspire V3-771 Windows 8 Core i3 Laptop, and today I finally got around installing Ubuntu 13.04.  I downloaded the installer image and burned it onto a DVD, created a 20GB NTFS partition on my laptop's 500GB hard drive and then rebooted from the DVD.  I followed the install wizard, which advised me that I would need a swap partition, which I created (1 GB) and continued with the install.

I selected my language, timezone settings etc, and all appeared to be going fine.  However, when I returned to my laptop about an hour later, I was faced with a command line interface, with what looked like a series of error messages, with no disk or DVD activity.  At this point, I decided to restart my laptop, and to attempt the installation again.

The installer detected the previous Ubuntu 13.04 installation on the 20GB partition, but also displayed a message to the stating that there were errors with the installation.  One of the options available was to uninstall the existing instance and re-install again, which was exactly what I wanted to do.  After I chose this option, the partition management screen loaded as before, however ALL of the existing partitions had been removed!

I decided to shutdown at this point, as I did not want to proceed with the installation for fear of overwriting the data on the hard drive.  I have removed the hard drive from my laptop, placed it in 2.5" enclosure and connected it to my old Windows XP laptop via USB, in the hope of finding some software to restore the deleted partitions.  Out of interest, I opened Windows XP Disk Manager to review the state of the partitions, but it looks like the old partitions have been replaced with a single "GTP Protective Partition".
 
I have attempted to recover the partitions or failing that the raw files, however both Pandora Recovery and Partition Recovery (by EaseUS) cannot read anything from the hard drive.
 
There are quite a few documents and photos from the last few weeks that I have not backed up, so I am pretty desperate to either restore the partitions or recover the files on the disk.  I (in hindsight naively) did not back up before I started the install, as I did not expect any partition other than the new 20GB one to be affected during the install process.
 
It looks like Windows based tools are not able to make sense of the new partition, is there anyway the old partitions can be recovered either by the Ubuntu installer, or some other recovery software?
 
If you need any further info, just ask.
 
Thanks,
 
Stephen.

---

### Post by TheFu on 2013-08-25
I fear you are screwed. During install, you only had NTFS partitions, so depending on your choices, you may have told the installer to overwrite everything. Backups before doing dangerous things are important.  Computers don't always do what we intend, they do what we tell them.

You might try a gparted ISO boot to see what that shows. You might get lucky.

If the data on the drive is critical, you can try testdisk and photorec or take it into an expert data recovery shop and for $3000, they will get some of the data back.  If it were me, I'd get a new HDD, mirror the screwed-HDD to the new HDD using ddrescue first, then try photorec and other linux data recovery tools on the newly mirrored HDD. I wouldn't touch the original except to read until I've given up.

I hope I'm wrong, but I want to set the expectations.

---

### Post by stephen8 on 2013-08-25
Thanks for your reply.  I have placed another 2.5" SATA hard drive into the Acer laptop and I am currnetly running a clean install of Ubuntu.  I'm planning to connect my original hard drive via USB and attempt to recover the original partitions using testdisk.  If I can't recover the partitions, then I'm planning to delete the newly created partition, which I'm hoping will allow Pandora Recovery to scan the drive...

---

### Post by TheFu on 2013-08-26
> **stephen8 said:**
> Thanks for your reply.  I have placed another 2.5" SATA hard drive into the Acer laptop and I am currnetly running a clean install of Ubuntu.  I'm planning to connect my original hard drive via USB and attempt to recover the original partitions using testdisk.  If I can't recover the partitions, then I'm planning to delete the newly created partition, which I'm hoping will allow Pandora Recovery to scan the drive...

Not likely that a non-Linux tool will recover anything, but you don't have anything more to lose.

---

