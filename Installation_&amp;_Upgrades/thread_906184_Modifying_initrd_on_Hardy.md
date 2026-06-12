---
title: "Modifying initrd on Hardy"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by karthikb23 on 2008-08-31
Hi,
After making ubuntu bootable on my USB, i checked about the casper script bug in hardy. To fix it I extracted the initrd, made the modification, and then repacked it as:

$gzip -dc initrd.gz | cpio -id

<Make the modification>
<Remove the file 'initrd', left behind after gzip, which cpio had extracted>

Repack initrd as:

$find . | cpio -oF  initrd
$gzip -9 -n initrd

Thereafter i get a file initrd.gz, in which a script is moified.
On using this initrd, the kernel panics, for unknown block device.

This implies that something somewhere is not correct with the initrd I repackaged.

Any help please???

---

### Post by Pumalite on 2008-08-31
Maybe reading this will help:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)
[http://ubuntuforums.org/showthread.php?t=611763&page=2](http://ubuntuforums.org/showthread.php?t=611763&page=2)

---

### Post by karthikb23 on 2008-08-31
Thanks!

i realized i missed out t format option, coz I was getting a message of inodes being chopped, when repacking.

---

### Post by aimeesonfl on 2011-01-13
> **karthikb23 said:**
> Hi,After making ubuntu bootable on my USB, i checked about the casper script bug in hardy. To fix it I extracted the initrd, made the modification, and then repacked it as:$gzip -dc initrd.gz | cpio -idRepack [[COLOR=#000000]initrd[/COLOR]](http://www.tanapple.net/th/advice/what-makes-the-babyliss-pro-ceramic-curling-iron.html) as:$find . | cpio -oF initrd$gzip -9 -n initrdThereafter i get a file initrd.gz, in which a script is moified.On using this initrd, the kernel panics, for unknown block device.This implies that something somewhere is not correct with the initrd I repackaged.Any help please???What you offered cannnot solve my issue, Anybody can help?

---

