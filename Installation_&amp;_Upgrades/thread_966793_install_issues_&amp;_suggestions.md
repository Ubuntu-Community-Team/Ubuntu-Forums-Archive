---
title: "install issues &amp; suggestions"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by TheSHAD0W on 2008-11-01
Hi.  I was playing w/ Ubuntu and Xubuntu on my Eee, trying to install a full running version onto an SD card and a jump drive so I could do things like get the wifi working.  My first issue was that the LiveCD version auto-mounted the card and jump drive, so when running the install script those devices weren't available to install on.  This was doubly a problem with Xubuntu, since the gui doesn't give the option to unmount a partition, only to eject a device; I was finally able to run umount from a command shell.

It would be a huge boon if the install script were able to detect mounted partitions, offer them as potential install points, and unmount them as necessary.  I understand that for desktop machines this is largely unneeded, but as netbooks get more popular, this option will become desirable.

Second issue:  The LiveCD versions of Ubuntu and its flavors are the size of a CD, but an install from that CD wouldn't fit on my 2 GB SD card.  I understand that the boot image is highly compressed and static, but the ability to try the OS out on a cheap SD card or jump drive would be desirable.  Aren't there any filesystems out there that include compression available?  You could auto-select a compressed filesystem when the partition chosen for installation was smaller than a certain size.

---

