---
title: "Re-installing grub with LVM"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by paul68 on 2014-04-24
Hi,

I am using Ubuntu 14.04 server and last night had a power cut. Afterwards, when trying to boot Ubuntu, it would hang for a few moments and then sometimes I would get an error that the LVM drive couldn't be found in grub. Clearly something went wrong. Thinking my SSD was fried, I loaded up the 14.04 live CD, mounted the disk and it seems to be working fine. I performed an fsck with no errors and can access files on the disk.

So, I thought possibly grub has somehow gotten corrupted and have been trying various methods of re-installing grub. My disk is /dev/sda, one partition (/) and using LVM. So far I've tried: 

* Entirely via the command line using chroot.
* Via boot-repair, installed on top of the live CD.
* Using the boot repair live cd.

Logs of the latest attempt from the boot-repair live CD is here: [http://paste.ubuntu.com/7319740/](http://paste.ubuntu.com/7319740/)

At the moment, grub boots to the grub menu as if there is no configured options. 

Any ideas? Am desperate for help as I don't want to have to do a re-install.

Thankyou!

Paul Morabito.

---

### Post by paul68 on 2014-04-24
one update - my boot partition doesn't contain any kernels even though querying dpkg I can see they are installed. So, I tried to re-install linux-generic and still nothing. Generated initrd images with initramfs then re-generated grub config but still get taken to grub menu.

I've read it is possible to reinstall all packages via the live CD without overwriting the current configuration. however, when I try to do so, possibly because of LVM the installer is unable to detect the filesystem type and insists on formatting my root partition (which is where I stop).

---

### Post by paul68 on 2014-04-24
Fixed - [http://askubuntu.com/questions/150691/missing-vmlinuz-from-boot](http://askubuntu.com/questions/150691/missing-vmlinuz-from-boot)

---

