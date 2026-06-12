---
title: "Installation CD to USB"
date: 2012-06-25
forum: Installation &amp; Upgrades
---

### Post by pmatos on 2012-06-25
Hi,

I have a burned CD with Ubuntu 12.04 image. However I want to install this on a pc without cd reader. My broadband is terrible so I am trying to circumvent downloading the iso again. Is there a way to use the LiveCD to get a USB installation image going? Maybe by recreating the iso from the cd and putting it on a usb? Would this work?

Paulo

---

### Post by VMC on 2012-06-25
from a terminal log into the cdrom drive and type the following:

```
mkisofs -R -J -o /home/ubuntu.iso .
```

point ubuntu.iso from the usb-creator gui.

Another way is to use the dd command(which is a bit dangerous if you make a mistake):

```
dd if=/dev/cdrom of=ubuntu.iso
```

go [_**here**_]("http://ubuntuforums.org/showthread.php?t=6509") for further examples.

---

### Post by efflandt on 2012-06-25
Boot the CD to a live system on a computer that had a CD/DVD player, where you have access to the install iso file.  From that use **Startup Disk Creator** to create a bootable install system on something with USB flash (memory stick or card reader) with regular FAT or FAT32 file system.  If you format it with Startup Disk Creator, just remember to format the "partition" (ending with a number) on the device, and not the entire device (without a number).

In a USB memory card reader that will even work with SD or microSD.  However, that will not work with some laptops where there memory card slot is NOT internally USB connected.  Most desktops with memory card slots are internally USB connected, as is my tablet PC which can boot an installed Linux system from large enough SDHC.

1 GB or more should work for bootable install iso on USB, but 8 GB minimum is recommended for full install to USB.

---

