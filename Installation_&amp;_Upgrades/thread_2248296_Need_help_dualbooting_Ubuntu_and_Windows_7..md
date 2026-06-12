---
title: "Need help dualbooting Ubuntu and Windows 7."
date: 2014-10-13
forum: Installation &amp; Upgrades
---

### Post by Hunter_Haywood on 2014-10-13
Currently I have Windows 7 installed on my PC. I'm trying to dual-boot Ubuntu on it. This is what happened:

Backed up all my files.
Downloaded PenDrive's Ubuntu USB installer
Booted off of the USB
Selected to install Ubuntu alongside Windows, but then it was only showing my hard drive while I wanted to boot it from my SSD, which has Windows on it.
Went to the partitioning menu, and froze up.

I'm not new with computers, but when I saw that menu I froze up. I had no idea what to do. I turned off my PC, ripped that USB out and booted back onto Windows. I'm willing to go again but I'll need some help with this menu. Anyone care to help?

---

### Post by Bucky Ball on 2014-10-13
*Thread moved to **Installation & Upgrades**.*

So you mean when you got to the 'Install Alongside' partitioning section of the install you chose 'Something Else' to partition manually and then the machine froze?

---

### Post by yancek on 2014-10-13
Are you saying it only shows your internal hard drive and not the SSD with windows?  I'd suggest that you read a tutorial or two on installing Ubuntu.  The link below is pretty detailed and specific to Ubuntu 14.04 and has a lot of useful information in addition to the how to install.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by oldfred on 2014-10-13
When you say SSD, is this one your installed or is system an UltraBook with small SSD as cache for Windows using Intel SRT? That uses RAID and may lock up installer.

Can you boot into live mode?

Post this from terminal:
sudo parted -l

---

