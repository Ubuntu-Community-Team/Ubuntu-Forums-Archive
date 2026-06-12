---
title: "Failed to create file system - can't install"
date: 2009-09-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Terry32 on 2009-09-19
I was wondering if anyone had any ideas, I have tried to install Karmic Alpha 5 and Alpha 6 without success. Below are some screenshots showing the problem, note I have AMD SATA Controller not nvidia like the screenshot shows.

Configuration:
AMD Phenom X4 940BE 3.0GHz
Asus M4A79 Deluxe Motherboard w/ AMD 790FX/SB750 chipset
4 Gigs of DDR2 800 Ram
Onboard AMD SATA controller set to AHCI (it has options for IDE/AHCI/RAID)
First Hard Disk - WD Velociraptor 80GB SATA II Hard Disk w/ Ubuntu 9.04 installed and working.
Second Hard Disk - WD Velociraptor 80GB SATA II Hard Disk w/ Blank (want to install 9.10 Alpha 6)

This is the way it looks when I get to the partitioning part of the install:
[IMG]http://img233.imageshack.us/img233/6570/screenshotinstall1.png[/IMG]


I change it to "Erase and use the entire disk", and pick the second hard disk (sdb because sda has my 9.04 install)
[IMG]http://img233.imageshack.us/img233/5746/screenshotinstall3.png[/IMG]


After the install starts it errors almost immediately like this:
[IMG]http://img233.imageshack.us/img233/7987/screenshotinstall4.png[/IMG]

I have tried using EXT3 and still no luck, 9.04 installs fine on this configuration and one thing I noticed was 9.04 installer doesn't show the option "Serial ATA RAID nvidia_bdbaffei () - 160.0 GB Linux device-mapper (stripped)" in the available hard disk drop down for the "Erase and use the entire disk" option.

Thanks in advance for any help, I did google and search this forum and could not find anyone with this issue.

-Terry

---

### Post by VMC on 2009-09-19
There have been reports of any of the alpha version of having buggy install program.

I don't know how experienced you are, but have you tried to set up your disk beforehand and then choose custom install?

Something like gparted will work. It's also gui. You can read this [**_tutorial_**]("https://help.ubuntu.com/community/InstallingANewHardDrive") for any further help.

---

### Post by Terry32 on 2009-09-20
Thanks for the suggestion, I used gparted and blew away the partitions on the hard disk and then created one main ~75GB partition with EXT4 filesystem and ~5GB swap partition, I then booted the 9.10 cd and ran the installer and did custom and set the main partition to / and left it as is and didn't select format. I got the following error.

[IMG]http://img44.imageshack.us/img44/1280/83593430.png[/IMG]

I tried it again and checked the format option also this time and it game me the same error as my first post. I think it is detecting my sata controller incorrectly because I don't have nvidia, mine is AMD AHCI SATA.

Maybe I should try and remove a disk and see if it will install with a single disk, that way it won't be trying to create a striped set.


-Terry

---

