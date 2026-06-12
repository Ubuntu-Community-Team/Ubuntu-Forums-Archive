---
title: "The attempt to mount a file system with type ext4 in SCSI1 (0,0,0), partition #1 (sda"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by madoba on 2010-10-15
Unable to install Ubuntu 9.10 on a new internal harddrive. The hardrive contains no operating system. This hardrive is the only drive present in the system.
 
Whenever the installation trys to mount the ext4 partition the following error appears:
The attempt to **mount** a file system with type **ext4** in SCSI1 (0,0,0), partition #1 (sda) at /**failed** 

Iv'e tried over and over to get past this error to no avail.

---

### Post by madoba on 2010-10-15
Ok one thing I did not mention is that the night before, I loaded ubuntu live cd went to disk utility program and ran a short test on the new internal hardrive. It was suppose to take about 10 minutes but the next morning 8 hours later it was still running. It never finished and I canceled it. Samething everytime I tried to run the short test.
 
The ubuntu disk utility says my drive is good but it can't ever complete the quick test. I refused to believe something was wrong with the disk as it was new.
 
What tests can be run on a harddrive to determine that the new disk you bought is good? Anyone have any other ideas about how I can rule in or out that the disk may be defective?

---

### Post by Skaperen on 2010-10-15
How large is this new hard drive?

Was the option to format the drive's partition selected where that might be chosen?

Is your installation media a CD/DVD optical disk, or a USB flash drive?

If this hard drive is new and has no data on it, you should be able to do the following command to be sure it is clear:

sudo dd if=/dev/zero of=/dev/sda oflag=direct bs=1048576 count=1

To do the above command, boot from optical media (if using USB flash drive, the device name may be different) and select the trial/live Ubuntu. When it comes up with the graphical desktop, press the keyboard triad cntrl+alt+F1.  This gives you a text console.  Type the above command.  To get back to the graphical desktop, press Alt+F7 or Alt+F8 or Alt+F9 (the first should work but in rare cases the others are needed).  Shutdown, reboot, and install, again.

If the problem still happens, there may be other issues that will require exploratory diagnostics.

---

### Post by Skaperen on 2010-10-15
If you plot a curve of failure rates against age of hard drive, there is a sharp peak right after birth.  If a drive is going to fail soon, it very often fails within the first 24 hours of use.  This is why smarter manufacturers do 24 to 48 hour "burn in" tests.

One possible failure mode is a loose or poorly inserted cable.  Either the data or power cable could do this, causing the drive to eventually get into a locked/frozen state, or an incomplete I/O operation.  Power off, unplug AC power, open case, stay grounded to case, remove drive cables on both ends, and re-attach cables with definite attention to making firm and secure insertions.

Other failure modes that can exist include a power supply on the verge of failure (voltage instability), damage to mainboard, incorrectly detected blocksize settings, incorrectly detected drive size.

---

### Post by madoba on 2010-10-15
> **Skaperen said:**
> How large is this new hard drive?
 
Was the option to format the drive's partition selected where that might be chosen?
 
Is your installation media a CD/DVD optical disk, or a USB flash drive?
 
If this hard drive is new and has no data on it, you should be able to do the following command to be sure it is clear:
 
sudo dd if=/dev/zero of=/dev/sda oflag=direct bs=1048576 count=1
 
To do the above command, boot from optical media (if using USB flash drive, the device name may be different) and select the trial/live Ubuntu. When it comes up with the graphical desktop, press the keyboard triad cntrl+alt+F1. This gives you a text console. Type the above command. To get back to the graphical desktop, press Alt+F7 or Alt+F8 or Alt+F9 (the first should work but in rare cases the others are needed). Shutdown, reboot, and install, again.
 
If the problem still happens, there may be other issues that will require exploratory diagnostics.
 
20gb
2491 cylnders
7200 rpm
 
I've never seen option to format. I've assumed the partition does the same thing.
 
I'll try that command tonight when I get home.
 
Being that the drive is brand new will that command prep the device for installation? Is there anything prior that needs to be done for a brand new disk with no operating system, to work for an Ubuntu install?

---

### Post by madoba on 2010-10-15
> **Skaperen said:**
> If you plot a curve of failure rates against age of hard drive, there is a sharp peak right after birth. If a drive is going to fail soon, it very often fails within the first 24 hours of use. This is why smarter manufacturers do 24 to 48 hour "burn in" tests.
 
One possible failure mode is a loose or poorly inserted cable. Either the data or power cable could do this, causing the drive to eventually get into a locked/frozen state, or an incomplete I/O operation. Power off, unplug AC power, open case, stay grounded to case, remove drive cables on both ends, and re-attach cables with definite attention to making firm and secure insertions.
 
Other failure modes that can exist include a power supply on the verge of failure (voltage instability), damage to mainboard, incorrectly detected blocksize settings, incorrectly detected drive size.
 
It's definitely an older computer system (A compaq pressario s5100xn) , probably about 5 to 6 years old. It was abandoned in my parents attic.  It hads its problems but it was replaced because it was one of those slow running window systems.
 
but I replaced and bought new memory and harddrive for a $100 dollars to attempt to run this thing solely on Ubuntu.

---

### Post by Skaperen on 2010-10-15
My guess is something additional is wrong, either some part not functioning correctly, or some part not supported any longer.  At this point I'd have to have it in front of me to get an idea what could be wrong.

I'd try selecting ext2 instead of ext4 and see what happens.  We lived on ext2 for many years when computers this size were plenty.

---

