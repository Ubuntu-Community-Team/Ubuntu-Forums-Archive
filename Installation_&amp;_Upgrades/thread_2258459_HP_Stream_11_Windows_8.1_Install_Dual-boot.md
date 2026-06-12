---
title: "HP Stream 11 Windows 8.1 Install Dual-boot"
date: 2014-12-27
forum: Installation &amp; Upgrades
---

### Post by capemayal on 2014-12-27
I have a new HP Stream 11 with Windows 8.1 pre-installed. UEFI Security enabled and Legacy Disabled.

I have Ubuntu 14.04 LTS on USB, and can boot into a "try" mode.

I have fast boot turned off.

I have a SD Card inserted as "D".

Computer management, with SD Card, shows 4 healthy partitions.  The card is 16gb, and reformatted from FAT32 to NTFS.

I want to install Ubuntu on D:.  The Stream's HDD is 32gb, with only 6 available.

I can start the installation either from the F9 Boot screen or by loading the try (Live?) mode, then clicking on install.

The installation starts; I sign onto my Wi-Fi network.  The installer indicates that I'm connected to the net, power is on, and I have at least 6gb available.  I select download all upgrades and install 3rd party plugins.

When I click "continue" the installation hangs and goes no further.

I have tried turning off secure boot.  I have enabled legacy mode. I've turned fast boot back on.

None of these seem to get me past the "continue".

Any suggestions?

Thanks in advance,
Al

---

### Post by Mark Phelps on 2014-12-28
> I want to install Ubuntu on D:. 

Can't do that.  Drive letters are a concept that Windows uses; Linux does not use them.  You would have to install Ubuntu to a Linux filesystem, meaning you would have to reformat the SD card to hold the partitions you need -- a single Ext4 partition and a small swap partition.

If you remove the existing partition from the card, the installer may be able to reformat it as part of the installation.

Also, 6GB is really tight -- I would go for 10GB to leave you some room.

---

### Post by grahammechanical on 2014-12-28
Be careful. If Windows 8 has been installed in EFI mode and not legacy mode, then we must also install Ubuntu in EFI mode and not legacy mode. You say that the Ubuntu live session run OK. When you run the installer do you see a screen with the following options?

Install Ubuntu alongside [other operating systems]
Erase disk and install Ubuntu
Encrypt the new Ubuntu installation for security
Use LVM with the new Ubuntu installation
Something Else

Not seeing that menu would indicate that the partitioner is having difficulty reading those drives. What to do about it is beyond me. Sorry. Why do you have partitions on the 16GB SSD that you want to install Ubuntu on? It could be that the installer calculates that there is not enough room on either the 16GB SSD or the 32GB HDD for a minimum install of Ubuntu of about 6GB.

When the early stages of the installer show a tick mark against a 6GB minimum disk space available, it has not actually measured the hard disks at this point. It is asking us to confirm that there is 6GB available by continuing with the Installation. If we know that there is not that minimum amount available then we must Cancel the installation. I think that you have found out what happens when we don't cancel when we should.

Regards.

---

### Post by capemayal on 2014-12-29
Thank you for your replies.

The HP Stream only has a 32gb "Hard drive", which only has 6gb available.

I thought I might be able to install Ubuntu to a SD card, in the card reader/writer.  I can write to the card.

I have formatted it to Ext4.  

However, I am unable to proceed past the add third-party programs when it stalls.

I do not "Add along side windows", etc.  

I have installed onto other laptops alongside windows and on newly formatted hard drives.

My thinking is that although the SD card is formatted as Ext4 that the HDD is NTFS and UEFI.

I would think the 16gb SD card would be sufficient to run Ubuntu with data saved to the cloud.

The laptop can see the SD card.


Thanks again.

---

### Post by gibbs-edward on 2015-02-23
Sadly it is not possible to boot from the SD card, the controller treats it differently from a real SSD, even though it appears to you to be one.

There are a couple options for you though.  

First you could clean up space on the 32 GB main drive.  Make a recovery USB stick, test it, and then delete the recovery partition.  Delete any programs or APPs that you don't really need, and move any documents, pictures, music, etc. to the SD card.  You should be able to get enough free space to install Ubuntu in a partition on the main drive (though I have not tried it so I'm not sure if it will dual-boot happily, just that you should be able to get it shoehorned in).

The second option is less invasive and more interesting - create a portable Ubuntu installation on a USB stick and boot from that.  Unlike a live version that evaporates as soon as you reboot, a full install to a stick allows you to save your changes, documents, etc.  And a USB stick IS bootable as you've already discovered.  A discussion of installing to a stick can be found here... [http://www.makeuseof.com/tag/keep-portable-ubuntu-installation-wherever-go/](http://www.makeuseof.com/tag/keep-portable-ubuntu-installation-wherever-go/).

Good luck.

---

