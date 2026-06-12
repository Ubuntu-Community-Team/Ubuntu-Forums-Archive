---
title: "Operating system not found during installation"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by vhastings on 2008-10-29
I am trying to install Ubuntu Server Edition 8.4 on a new whitebox system that has two 160gig SATA hard drives that I intend to use in a RAID array.  The system also has a SATA CD/DVD drive on Port 0; the two drives are on ports 4 and 5.

When I start the computer, the system attempts to "Boot From AHCI CD-ROM", then reports "Operating System not found."

I have selected the CD/DVD drive as the first bootable device in the BIOS.  The CD/DVD drive and both hard drives are shown in the BIOS.

I checksummed the ISO file; it's perfect.

The hard drives were already configured as an array using the Intel RAID utility.  I deleted the volume to see if that might have been the problem.  It wasn't.

I'm a noob to both Ubuntu and RAID, so I'm throwing myself on the mercy, and expertise, of the community.  Thanks in advance.

---

### Post by Pumalite on 2008-10-29
Download a Knoppix Live CD and see if it boots:
[http://www.knoppix.net/get.php](http://www.knoppix.net/get.php)
Let me know

---

### Post by vhastings on 2008-10-30
Found the problem -- the ISO image was burned onto the disk, rather than the files and folders.  New CD burning software fixed it.  D'oh!

---

