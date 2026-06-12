---
title: "Installation type window only shows usb option"
date: 2018-12-08
forum: Installation &amp; Upgrades
---

### Post by juicymelon on 2018-12-08
when reaching the "installation type" window on my Dell Inspiron 7472, when installing ubuntu 18.0.4.1, rather than showing any options it simply shows a partitioning screen with what appears to be my usb device. Any help would be appreciated

---

### Post by ajgreeny on 2018-12-09
Are you trying to install on a UEFI machine using a legacy BIOS booted install medium?

On boot up of the USB or DVD you're using to do the installation you should see two options for the USB or DVD, one showing UEFI at the start of the name, and the other without UEFI; make sure you choose the appropriate one and you may find the hard disk partitions appear.

It is also possible that you need a BIOS/UEFI update from Dell, particularly if you are using an SSD as their original version does not support some SSDs in Linux.

---

### Post by yancek on 2018-12-09
Is there currently another operating system on the primary drive, windows for example?  If it is windows 10, it defaults to hibernate and the installer will not mount hibernated partitions so they will not show in the installer.

---

