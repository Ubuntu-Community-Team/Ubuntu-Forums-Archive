---
title: "Install to USB stick."
date: 2023-04-22
forum: Installation &amp; Upgrades
---

### Post by truij on 2023-04-22
Hi,
I'm wanting to install Ubuntu to a USB stick because my SSD already has Windows (and I don't want to ruin it) and only has 80 GB free space and my spinning disk is too slow. So I'm wanting to install it to USB. 
But when I try to install, it doesn't register the USB as a install option. 
Why? And how can I fix it?

---

### Post by yancek on 2023-04-22
Which release of Ubuntu are you trying to install?  Which release of windows do you have?  If you have a desktop, it might be better to disconnect the windows drive so it isn't accidentally overwritten.  How old is your hardware?  Is windows a UEFI install or a Legacy/MBr install?  Or do you know what those terms mean?  How are you trying to install?  Have you written it the Ubuntu iso file to a flash drive with software dedicated to that purpose?  Your post seems to indicate your USB boots but doesn't see the other flash drive, is that correct?  If you can boot the Ubuntu usb, select the Try option and when you see the Desktop, open a terminal and input the following to list drive/partition info:

```
sudo fdisk -l
```

Post that output here, have both USB drives attached.  A USB/flash drive is going to be much slower than a standard drive.

What does 'register' mean?  Did you select the manual install method (Something Else)?  In the Installation Type windows, you should see detected drives/partitions, is that what you are referring to?  Is the USB you wish to install to formatted with a filesystem?  If so, what is it?

---

### Post by oldfred on 2023-04-22
Ubuntu does not make it easy to install to any second or external drive.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Several work arounds in bug report. Easiest may be:
Remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator) & 

I used to do and still have full installs on USB drives. But USB flash drives are slow.
My install to SSD is 10 min, install to USB3 flash drive is an hour.
I bought a larger M.2 NVMe drive to replace my M.2 SSD. Moved SSD to USB3 adapter.
I now will not install to flash drives as external SSD is almost as fast as internal SSD.

Also since external drives are slow better not to use Ubuntu but a light weight flavor.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
I use Kubuntu which is a mid-weight flavor

---

### Post by grahammechanical on 2023-04-22
You will need two USB ports. One for the USB memory stick with the Ubuntu ISO image burned to it. The second USB memory stick is where you want to install Ubuntu to. If the installer puts the boot files on the Windows disc then Ubuntu will take control of booting Windows. Remove the Ubuntu USB stick and the Grub boot menu will not appear as it will look for boot files on the Ubuntu USB stick that is not present.

This might help.

[https://www.fosslinux.com/68855/install-ubuntu-on-external-hard-drive.htm](https://www.fosslinux.com/68855/install-ubuntu-on-external-hard-drive.htm)

Regards

---

### Post by ubfan1 on 2023-04-23
The just released Ubuntu 23.04 has apparently fixed the refusal to install bootloaders to a second device (bug [https://bugs.launchpad.net/ubuntu/+s...y/+bug/1396379]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379")).  If you don't set up the partitioning on your target in advance (e.g. ESP and root), the manual part of the installer will always create a 1GB ESP, even if you create a partition you want to use for that.  I use a 300MB ESP and the rest / on a 30GB USB. Select that device, the booloader location is that device, bootloader files get copied to the target USB, and the host system's grub is unchanged. This fix has been a looooong time coming.

---

### Post by tea for one on 2023-04-24
> **ubfan1 said:**
> The just released Ubuntu 23.04 has apparently fixed the refusal to install bootloaders to a second device (bug [https://bugs.launchpad.net/ubuntu/+s...y/+bug/1396379]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379")).  If you don't set up the partitioning on your target in advance (e.g. ESP and root), the manual part of the installer will always create a 1GB ESP, even if you create a partition you want to use for that.  I use a 300MB ESP and the rest / on a 30GB USB. Select that device, the booloader location is that device, bootloader files get copied to the target USB, and the host system's grub is unchanged. This fix has been a looooong time coming.
Yes, good information from ubfan1 - thank you, it encouraged me to conduct a few tests.

I would like to add a few comments (UEFI mode only):-
The bootloader is installed on the second device and the target device will boot - so far, so good.

The host grub is _not_ always unchanged - there are many factors in play i.e. no. of disks, vendors' UEFI structure, other OS systems visible etc.
I have a test system, dual boot (Xubuntu 23.04 and Windows 11) and only the Windows Boot manager was untouched.
Luckily, I can boot into Xubuntu via EFI shell to re-install and update Grub from a running session.

If you have two disks and installed Ubuntu 23.04 to a third external disk, I experienced that UEFI boot order had changed after removing the third (target) disk.

Ubuntu family flavours with 23.04 may not use the new Flutter installer.
The clue seems to be in the text used:-
"Manual partitioning" in Ubuntu 23.04
"Something else" in Xubuntu 23.04
I couldn't get the Xubuntu 23.04 installer to behave as the Ubuntu installer.

Nevertheless, the Ubuntu 23.04 Flutter installer is an improvement over previous versions.

---

### Post by sudodus on 2023-04-24
An easy way to install Ubuntu or an Ubuntu family flavour is to extract and clone from a compressed image file of Ubuntu Server and then install the desktop environment you prefer: the meta-package ubuntu-desktop, kubuntu-desktop, lubuntu-desktop ... xubuntu-desktop.

The method will grab the whole drive and works with an internal drive, external drive and even with a drive in a virtual machine. This method does not tamper with any other drive (only affects the target drive).

See more details about this method at [this link](https://ubuntuforums.org/showthread.php?t=2474692).

---

