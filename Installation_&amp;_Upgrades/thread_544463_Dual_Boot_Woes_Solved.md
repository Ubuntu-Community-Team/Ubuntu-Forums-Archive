---
title: "Dual Boot Woes Solved"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by measekite on 2007-09-06
This may help others.  I had dual boot (Grub) problems when installing on the following equipment.  Keep in mind that while experience in Windows Tech Support I am totally new to Linux.

**My Equipment:**

ASUS MB.  Two Maxtor Hard Disks - 1 SATA and the other IDE (PATA).

[B] What I did the first time

[/B]I booted from the Live CD and did a manual install.  I choose to have 60GB of the SATA drive partitioned for Linux leaving the remaining 60GB for NTFS Windows.

At the end of the install GRUB was placed in (hd0,1).  When I booted from my SATA drive menu.lst showed Ubuntu at (hd1,1).  Both Windows and Ubuntu would not boot.  I then typed e at the menu and changed Ubuntu to (hd0,1) and Ubuntu booted fine.  

However Windows would not boot.  Using the same proceedure I changed Windows from (hd1,1) to hd0,0).  There were two additional "map" lines but I did not change them.  Windows failed to boot.

I did a previous Ubuntu install on a one drive machine with no problems.  The Windows portion lacked the two map lines.  If I knew how to edit Grub I would have attempted to resolve the issue but that is for the future.  Linux has many issues and the learning curve is high even though it is more efficient and secure than Windows.  I did a reinstall many times and got the same results.

**The Solution That Worked.**

I removed power to my IDE (PATA) drive.  Booted with the Live CD and did the install the same way.  Now Ubuntu booted and the Grub menu showed the following:

Ubunto - (hd0,1) meaning (boot drive, partition 2)

Windows (hd0,0) meaning (boot drive, partition 1)

After testing I replaced the power to the IDE drive and all is well.

**What I Think Happened**

With both drives connected and booting from the CD Drive the BIOS reported that the IDE drive was 0 and the SATA drive was 1.  The install program put GRUB on the SATA drive (where the Linux partition was installed) and wrote the information as (hd1,1) since that is what the BIOS reported.

When you went to boot from the hard disk things became reversed. The BIOS always reports the IDE drive as 0 and the SATA drive as 1.  You can see this in Windows Disk Manager where the IDE drive is DISK0 and the C: drive - SATA is Disk1.

However Linux changes things.  It always calls the boot drive as 0 so the IDE drive became 1.  So that is why Ubuntu now boots properly.

The only thing I can think of why Windows now works is that in addition to having (hd0,0) the two line that read MAP (hd0,0) (hd1,1) and the reverse on the next line were no longer there.

---

### Post by toolfreakuna on 2007-09-06
I had a very similar problem, and by editing my menu.lst and ALSO taking out the map lines under the windows header, mine works like a charm now. So yes, this is what is needed to get it working even with multiple SATA or PATA drives working in conjunction.

---

### Post by measekite on 2007-09-06
Are you saying that if the system has 2 SATA drives the same thing would happen?  Or is it the double map lines that affects Windows if the drives are both SATA?

Where can I find out what all of the lines in menu.lst mean and represent?  How can you edit it and save it?

---

