---
title: "Ubuntu 21.10 Installation Failed to Find SSD Partition"
date: 2021-10-17
forum: Installation &amp; Upgrades
---

### Post by airbot on 2021-10-17
I have a MSI GS66 laptop with Nvidia RTX3060. It has dual boot Windows 10 and Ubuntu 21.04.  I would like to reinstall the Ubuntu partition to 21.10.  I downloaded Ubuntu 21.10 installation iso file and created a bootable usb flash by using Rufus tool. Then I logged into Windows 10 and had the Ubuntu 21.04 installation partition deleted. I rebooted the laptop to start the installation. However in the installation wizard it didn't show any installation type. If I clicked Install Now to install Ubuntu, it showed the following errors: "No root file system.  No root file system is defined.  Please correct this from the partitioning menu."  Fast boot was disabled. Something must be broken in Ubuntu 21.10 installation process as I had no such issue when I installed Ubuntu 21.04 on the same laptop.  I left 600 GB SSD for Ubuntu.  The installation wizard failed to find such partition.

---

### Post by tea for one on 2021-10-17
Ubuntu 20.10 is now unsupported (end of life).

Did you mean Ubuntu 21.10?

---

### Post by yancek on 2021-10-17
Use the Something Else option and in the Installation Type window you need to select the partition on which you had your previous install of Ubuntu.  In the lower left part of that window you will see Change, click on that and you will get the Edit partition window which will give you several options.  One of these  is Mount point. Click the down arrow and you will see several options.  The first one should be the symbol for root "/: so click that and proceed.  Failing to do this is the reason you see the "no root filesystem is defined" error.  Scroll about half way down the page at the link below to see a graphical image of this.

[https://www.tecmint.com/install-ubuntu-alongside-with-windows-dual-boot/](https://www.tecmint.com/install-ubuntu-alongside-with-windows-dual-boot/)

---

### Post by airbot on 2021-10-17
Yes.  Sorry for the typo.  It is Ubuntu 21.10.

---

### Post by tea for one on 2021-10-17
> **airbot said:**
> Then I logged into Windows 10 and had the Ubuntu 21.04 installation partition deleted.
Having deleted the [COLOR="#0000FF"]target[/COLOR] partition, then the installer would not be able to install into a non-existent partition.
You have to create a partition and then select it so that the installer can proceed.
yancek's link displays [COLOR="#0000FF"]Create Ubuntu Root Partition[/COLOR]

I think that your difficulty arose because you deleted the original Ubuntu partition when you could have over-written it with a fresh installation.

Make sure that you have booted in the correct mode (probably UEFI if you already have Windows 10)
Info here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by sarmad2 on 2021-12-20
A late reply, but might be useful to someone: The issue is that the Ubuntu installer is not seeing your NVMe at all (not just the partition). Change the Intel VMD option in the Bios (can't remember if it needs to be enabled or disabled, but anyway just flip the switch to the other option) and Ubuntu installer will start seeing your NVMe hard drive.

---

### Post by MAFoElffen on 2021-12-21
Just a hint:

Please run the Ubuntu Forum's 'system -info" script in my signature line from the Installer LiveCD environment to show people what state your system is in currently, so they are not assuming or guessing on what it 'may be' Better to go off the current 'facts'... 

That will confirm what: Is seen, is configured and there on your system... as well as what your system actually is. There is a lot of unknown factors that do matter in your problem, and I don't think anyone has asked 'the questions' into dig into those yet.

*On the last recommend/previous post, hold off on that, as it might make your storage unreadable by flipping that.

---

