---
title: "trouble with bootable raid 1 setup"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by jeff_k on 2010-10-04
Hi, I am trying to set up a Debian install, creating 2 raid1 arrays, 1 for / and 1 for swap. I was following the link here:
[http://advosys.ca/viewpoints/2007/04...ubuntu-server/]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/")
I created the arrays (wrote the partitions and arrays) before I realized  that I probably did not set the bootable flag on the drives /dev/sda1  and /dev/sdb1. I therefore need to delete the raid arrays and start  over. However, upon reboot the raid arrays still exist. Do I simply need  to select the "erase data on raid disk" option of the installer, or is  this still not going to eliminate the array? How do I get back to having  separated drives again, or do I have another opportunity to set the  boot flag on the drives?
Thanks in advance for any help.
Jeff

---

