---
title: "Errno 5 - Error during installation"
date: 2018-09-22
forum: Installation &amp; Upgrades
---

### Post by vishalmukadam on 2018-09-22
Howdy,

I am trying to install Ubuntu-18.04.1-desktop-amd64 from USB flash drive to my Dell 5567 laptop which has 4 GB RAM, but it keeps failing to copy the files, 
I have made a live bootable USB via PowerISO, it shows me this error "**Errno 5**", please check the screenshot below:
[IMG]https://cldup.com/o-4Qq8yXMM.PNG[/IMG]

I have tried to find a solution from the past similar thread; some people have said to use Ext3, and I tried but again failed.

Someone has also suggested uninstalling "Ubiquity by typing commands on terminal"(a slideshow which shows during installation), tried that option as well again the installation failed the same error.

Please help me to get this fixed.

Thanks!
Best Wishes!

---

### Post by oldfred on 2018-09-24
More often a bad copy to flash drive or defective flash drive.
Some have also had to use a different USB port or a different install tool to create flash drive.

You should use ext4 for / and FAT32 for installer partitions.

UEFI or BIOS install?
What brand/model system?
Post this from live installer in live mode:
sudo parted -l

Similar issue, was flash drive.
[https://ubuntuforums.org/showthread.php?t=2401744](https://ubuntuforums.org/showthread.php?t=2401744)

---

### Post by vishalmukadam on 2018-10-21
@oldfred,

Thanks for your response, the problem got solved I was using memory card to install the ubuntu, the problem got solved when I burned the DVD using PowerISO and it got fixed.

The issue was with Memory Card, and sorry for the delayed response from my side. :)

Cheers!

---

