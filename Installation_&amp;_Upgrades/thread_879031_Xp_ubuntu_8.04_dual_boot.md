---
title: "Xp ubuntu 8.04 dual boot"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by Nilanjan Majumdar on 2008-08-03
Hello every one

I am absolute novice to UBUNTU. My inspiration was my nephew playing with Gutsy Gibbon which prompted my try out UBUNTU. I was impressed with the concept of Ubuntu and the fact that it is immune to virus attack. I happen to be a radio ham and constantly experiment with new sound card based radio digital modes on HF and I have heard UBUNTU has loads of ham software. However I have so much Windows data and software that I must go for a dual boot system. I recently upgraded my PC to a Core2Quad processor, 2 GB of RAM and a 250 GB HDD. I have already downloaded and burnt the ISO image into an installation CD for 64 bit desktop PC. I have partitioned my 250 GB hard drive into the following partitions:

60 GB partition NTFS format (Drive C) where I have installed XP
installed Windows XP SP2. There is still 54 GB remaining in this drive.

140 GB partition NTFS format (Drive E) which I intend to use as my data drive.

50 GB partition unformatted.

Before I start UBUNTU installation in my PC I have the following questions:

1. Can I perform a guided installation in the unformatted 50 GB space? Do I have to format it NTFS with Windows disk manager before installing UBUNTU and then can Hardy Heron be guided installed in this 50 GB space?

2. If a guided installation of the above (1) is not possible then is a manual install possible in this partition. If so how to manually install UBUNTU in this 50 GB space.

3. If I have to install UBUNTU in drive C (60GB) where Windows is already installed then during guided installation what should be the ideal partition in this drive for Ubuntu to set up and leave adequate space for Windows XP.

I would be grateful if I could receive any help in this regard. I have also some confusion of what I should import from Windows during the installation.

Looking forward to any help.

Nilanjan Majumdar, VU2HFR
Kolkata
India

---

### Post by xen-uno on 2008-08-03
I'm no expert Ubuntu installer, but what I did is created 3 partitions with Windows in my 2nd hard drive (according to the BIOS). Of the 160 total size, I made a 90 GB NTFS partition for windows programs, an unformatted 2 GB for Ubuntu swap, and the unformatted balance for the Ubuntu system. During the install (off the alternate install disk), I pretty much accepted the defaults but checked the -noatime switch on all the drives. Setup has been fine with 7.10 and now 8.04.

edit: On the importing ... there really isn't anything you can until it's installed, and then it's more like "attaching to" rather than importing. Ubuntu should see all your NTFS drives (see Ubuntu's Places menu after install). You can take steps then to auto-mount those drives.

---

