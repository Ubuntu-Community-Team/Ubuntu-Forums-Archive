---
title: "creating kernel and initrd for ubuntu server image installation"
date: 2013-12-06
forum: Installation &amp; Upgrades
---

### Post by rameshg872 on 2013-12-06
Hi,

This might sound like tons of tutorial are out there, but I couldn't find information that I am looking for.

Basically my requirement is like this:
I have a root filesystem prepared, with which I wanted to create a bootable ISO.  I created a live cd image which boots well with casper installed, with the help of the below tutorial:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

But now, I need to create an installable system with my custom root fs that I have prepared.  Basically, I need to install the filesystem.squashfs file I have on my iso image onto a machine's disk.   I read many tutorials and got to know that I need to use the "debian-installer" with the "live-helper" udeb package.  So, I will need a customized initrd.gz which has the debian-installer on its initramfs and will be triggered by the /init script on it.

Now the information that I am looking for, is how to create such a initrd image OR how to tweak my current initrd image (which is already present inside my rootfs) to trigger debian-installer to install it onto a system. 

Or are there any tools which helps in creating debian-installer configured initramfs for my custom root filesystem ? 

Thanks in advance.

Regards,
Ramesh

---

