---
title: "Installation question"
date: 2014-09-05
forum: Installation &amp; Upgrades
---

### Post by conrad4 on 2014-09-05
I installed Linux Ubuntu 12.04 on my old Win XP machine. I used the DVD created from the downloaded ISO file. I had the installation program wipe the C: drive and install Ubuntu all by itself. Everything ran just fine for several months until the motherboard failed.  I removed both internal HDD's. I would like to install Ubuntu 14.04.01 from a new DVD which I created from the downloaded ISO file onto my Win 7 machine. I want to use one of the removed HDD's from the Win XP machine and mount it into an External HDD enclosure connected to the Win 7 machine. The HDD is a 120 gig serial ATA drive partitioned into two equal NTFS partitions. Ubuntu could have the whole HDD. Is it possible to leave Win 7 by itself on the C: HDD and Ubuntu on the external HDD ?  They would not have to interact. When I boot up the machine I would like to choose which operating system I would want to run.  Is this scenario possible ?  If so, could someone kindly outline what I must do to prepare the external HDD for Ubuntu and will this install process create the means to choose which operating system I wish to use when I boot up the computer.  I'm comfortable using the Ubuntu desktop and using the applications, Firefox and Thunderbird Mail but am not too comfortable using typed commands to make things work.  All help will be appreciated. Thank you.

---

### Post by yancek on 2014-09-05
Yes, you can do that.  I am posting a link below for installing Ubuntu 14.04.  It is a very detailed tutorial and has a separate section on partitioning and another on dual-boot installation.  If you are going to install Ubuntu on an external drive, the default install location for the Grub bootloader will be on the the first/internal drive mbr.  Problem with that is that it will overwrite the windows code there.  It should create an entry for windows however and you will be able to select either windows/ubuntu.  If you do this, you will need to have the external attached at all times to boot either as only a small part of the boot code is in the mbr and the rest is on the system partition, in your case on the external drive where you install Ubuntu .  You could install Grub to the mbr of the external and then on boot select either drive from the BIOS.   That would leave windows to boot the internal Ubuntu/Grub to boot the external.  Windows cannot boot any Linux.  You could install third party software on windows to do that, EasyBCD.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by grahammechanical on 2014-09-05
The installer will install the Grub boot loader into sda by default. Now sda should be the internal disk with Windows 7 on it. So, the Windows 7 Boot loader will be gone but Grub will look for its configuration files in Ubuntu on the external disk. Then if the external disk is unplugged you will not be able to load Windows 7. This is what I think.

So, I suggest that you make sure that the installer puts the Grub boot loader on the external disk. It should be sdb. There will be a panel with a drop down list of drives and partitions.

Then if the external drive has boot priority you will get a Grub boot menu with the options to load either Ubuntu or Windows 7 when the external is connected. And if the external drive is not connected the boot priority should switch to the internal drive and load Windows 7.

That's the cunning plan, anyway.

Regards.

---

### Post by conrad4 on 2014-09-06
Thank you for the reply.  I have your link now for the install guide.  Much, much reading to do before I proceed. The Rosewill RX-358 V2 SATA to USB & eSATA External Enclosure I am considering will let me connect directly to the motherboard, I hope !
Conrad

---

### Post by conrad4 on 2014-09-06
Thank you for the reply.  I will carefully plan my install procedure before I attempt the install.
Conrad

---

