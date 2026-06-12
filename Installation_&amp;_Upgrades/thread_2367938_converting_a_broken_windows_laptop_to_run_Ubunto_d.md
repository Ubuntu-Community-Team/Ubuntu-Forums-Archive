---
title: "converting a broken windows laptop to run Ubunto desktop from boot or network"
date: 2017-08-04
forum: Installation &amp; Upgrades
---

### Post by haroldontherocks on 2017-08-04
[COLOR=black][FONT=Helvetica]Hello, About a year ago, I turned an older windows desktop into a32-bit Linux SERVER, without the Ubunto GUI, using a CD/DVD boot disc image Imade. This past week, I downloaded the latest Ubuntu 32-bit DESKTOP iso. Iburned this onto a USB drive and a DVD drive. I put the usb drive into the oldGateway windows laptop, and it boots up with Linux desktop, something new tome, as I was expecting it to go straight into the Languages prompt of theUbuntu install. Anyways, I see on the Ubunto desktop has a "setup"icon. I click to Install Ubunto, and after the wizard connects to the Wifi, itproceeds to install and around step 2 or 3 of the install, it DISABLES thecontinue button, saying something like, "you need 8.5 Gb of space toinstall Ubunto. This drive has 2gb. 2gb is the size of my USB stick.** I can onlyclick cancel or back. I'm STUCK**. I get the same thing with the DVD boot disc,and it says, this disc has 0.0 space. I read changing a setting in the BIOSmight fix this, but I couldn't find any such IDE advanced setting to change. Iam viewing the **Ubunto Network Installer but it’s over my head**. **How do I get thedisc or usb drive to install onto the windows laptop hard drive? Any tips onusing the network installer?** The Gateway laptop I want to convert to Ubuntocannot boot up with its Windows and I don’t know why. My goal is to salvage theLaptop with Linux.:D[/FONT][/COLOR]

---

### Post by oldfred on 2017-08-04
Is drive still seen in BIOS?
Was drive ever part of RAID? The server install may work, but the desktop installer may not work if drive still has RAID meta-data.

Post this to see if drive shown, change to sdb if flash drive seen as sda:
       sudo parted /dev/sda unit s print

---

### Post by BenginM on 2017-08-05
How much space does the partition on the HD/SSD .. ! I would try the to boot the mini.iso 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

and do a minimal installation like so , 

[https://www.youtube.com/watch?v=U42Ln3k7VK0](https://www.youtube.com/watch?v=U42Ln3k7VK0)

but you need to make sure you're connected through wired ethernet cable , as this is netboot network installation. and when you get to the software selection screen , pick the desktop environment you want , ubuntu-desktop will give you Unity DE , Xubuntu-desktop , Xfce , and so on.

---

### Post by johndough2 on 2017-08-05
Hi

Is the HDD actually fully partitioned, leaving no space for a new install?

Try something light onto your stick like a live Gparted, more to prove the boot process and view the HDD.
gparted.org/livecd.php

---

