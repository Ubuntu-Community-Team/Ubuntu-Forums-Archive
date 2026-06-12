---
title: "Installing using debootstrap from local repository"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by dipaktc on 2008-09-02
Am trying to install Ubuntu 7.04 on a existing linux machine which is running on PowerPC.

I followed the instructions at [https://help.ubuntu.com/7.04/installation-guide/i386/linux-upgrade.html](https://help.ubuntu.com/7.04/installation-guide/i386/linux-upgrade.html)

When I give the internet location as mentioned, debootstrap works well and the installation is complete.

But when I have copied the contents of a CD which I downloaded from here - [http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/) ( Alternate CD Image) to a local disk ( /mnt/cdrom) and gave that path to debootstrap, it gave me an error saying

(/usr/sbin/debootstrap --arch powerpc feisty /mnt/ubuntu file:/mnt/cdrom/)

E: Couldn't download dists/feisty/main/binary_powerpc/Packages.

If I check the folder //mnt/ubuntu/var/lib/apt/lists, I find a file debootstrap.invalid_dists_feisty_Release.

Is this something to do with the validity of the CD contents?? ( When I wrote the CD ( in windows), all the folder and filenames were in upper case. When I copied to the linux machine, I wrote a script to change them to lower case)

Can someone tell me if am missing something?

Any help is duly appreciated.

Thanks in advance.

---

