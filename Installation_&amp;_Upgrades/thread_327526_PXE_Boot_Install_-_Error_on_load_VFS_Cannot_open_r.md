---
title: "PXE Boot Install - Error on load: VFS: Cannot open root device &quot;&lt;NULL&gt;&quot;...."
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by scaryant on 2006-12-29
Hi,

I have an ageing Toshiba 4600 Satellite Pro Laptop (PIII 900Mhz, 384Mb RAM, 20 Gb HDD) that I'm trying to install Ubuntu on.

I have setup a Windows TFTP server and a Windows DHCP server which all seems to be working fine except as it loads the install I get the following error message(s);

> VFS: Cannot open root device "<NULL>" or unknown block(8,1)
Please append a correct "root=" boot option
Kernal panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)

I got the image files for the netboot from the [Ubuntu install help pages.]("http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/")

If it helps, my laptop hdd is currently split into two partitions.

Any assistance is much appreciated! :) Thanks!

PS I cannot use CD boot as the drive/bios will not recognise the burnt ISO (from ubuntu site), BIOS is too old for a USB boot as far as I know and the floppy drive is kaput!

---

### Post by scaryant on 2006-12-29
I have this fixed now! Duh. It appears I hadn't arranged the boot files/directories correctly in the TFTP boot image directory.

Thanks for stopping in though! When I've completed the install I'll post a how to...

Cheers

---

### Post by scaryant on 2006-12-31
[HOWTO: Install Ubuntu via Netboot/PXE using Windows]("http://www.ubuntuforums.org/showthread.php?t=327597")

Cheers

---

