---
title: "SOLUTION: installation failure (due to SATA drive?)"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by emanaton on 2006-08-20
Greetings,

I've now invested several hours attempting to install 6.06 on my wifes machine:

Dell Dimension 4100
Maxtor 6Y080M0 Drive, Serial ATA on port SATA-0
Drive contains XP (NTFS) partition to keep, XP (NTFS) partition to delete and replace with linux, and a "shared" partition (also currently NTFS) to remain in tact.

The installation hangs shortly after attempting to mount the file system with error along the lines of:

kubuntu can't access tty; job control turned off

An hour or so of troubleshooting brought me to realize that the issue has to due with hard drive detection. In particular, executing qtparted provided a friendly message that the system appears to have no hard drive.

After another hour of ](*,) , I started futzing with BIOS settings. It turns out that a SATA Operation set to "Combination" instead of "Normal" is the culprit here. Changing it to "Normal" caused proper drive recognition. Color my happy, right?

Well, qtparted now launches, but it crashes as soon as I click on the drive listed. In what I thought would be a vain attempt to get around this, I booted into windows and deleted the superfluous NTFS partition, freeing the space for the linux install, leaving the primary XP partition and the data partition in tact. While qtparted still crashes, choosing "Use largest continuous free space" does move one to the "Ready to install" page (whereas before it crashed on an attempt to launch qtparted). I proceeded through the rest of the installation without incident. I think the happy-color will stick this time.

Ta ta for now,

Sean P. O MacCath-Moran
[www.emanaton.com](www.emanaton.com)

---

### Post by joemacnz on 2006-09-12
I am having a very similar problem at the moment except that I can't find any SATA references in the BIOS. The MOBO is an ASUS A8V-MX and the book says something about needing Windows2000 SP4 or better.I can see the HD on the Bios but not on Ubuntu(or BartPE).Can anyone help?

---

