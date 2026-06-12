---
title: "Questions about &quot;Hard Disk Installation&quot; of Ubuntu10.04."
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by Randy Schilling on 2010-06-30
I have xp on sda, fedora 13 on sdb, and I want to install ubuntu 10.04
on sdc.  I've been having lots of boot problems following my attempts
to install ubuntu, all coming down, I believe, to unreliable media.
I'm considering what Ubuntu's installation guide describes as "Hard Disk Booting," see
Ubuntu Documentation > Ubuntu 10.04 > Ubuntu Installation Guide > Obtaining System Installation Media > Preparing Files for Hard Disk Booting.

I can use my fedora installtion to carry out this process.

Ubuntu's installation guide breaks a hard disk installation into the following 3 steps.

1. Copy the files vmlinuz (kernel binary) and initrd.gz (ramdisk image)
from the Ubuntu archives to a convenient location on your hard drive, for instance to [Fedora's] /boot/newinstall/.

2. Add the following lines to [Fedora's] grub's menu.lst file:

title  New Install
kernel (hd1,0)/boot/newinstall/vmlinuz
initrd (hd1,0)/boot/newinstall/initrd.gz

(hd1,0) because fedora is on the first partition of sdb.


3. Reboot into [Fedora's] grub and select New Install.

I have questions on step 1.  The manifest file in the Ubuntu archives
([http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/MANIFEST](http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/MANIFEST)) lists versions of vmlinuz and initrd.gz for CD installation, USB stick installation and and netboot installation, nothing specifically for a hard disk installation.  Which of these versions should I download and save to Fedora's /boot/newinstall/.

Also, should i download a ubuntu installation iso file to my fedora's file system?  

The rest seems ok to me but please, anything you can tell about how this is going to go would be most appreciated.

Thanks - Randy

---

