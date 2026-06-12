---
title: "Ubuntu Server 20.04 LTS Failed Install (subiquity...install_fail/add_info)"
date: 2020-05-11
forum: Installation &amp; Upgrades
---

### Post by electr0 on 2020-05-11
Hey All,



I'm trying to update my home server to Ubuntu 20 however I'm having a bit of a problem.

I want to dual boot my current Ubuntu 16 with the new v20. I booted a Live USB and used GParted to shrink my dev/sda1 in size and then directly after it, I created a new partition dev/sda5 in the unallocated space to use for the as Ubuntu 20 install.



During the v20 install I select the custom install method and select the dev/sda5 partition to be formatted to ext4 and mounted a "/". I then select the SWAP partition from my v16 install to be used as the SWAP for the v20 install.

I then proceed to the next screen where I choose my username and password, and after a few moments this error screen pops up.

I downloaded the Ubuntu 20 ISO from the official site and used Rufus to burn it onto a USB, which worked perfectly fine for the Ubuntu 20 Desktop live usb that I ran Gparted off.


Does anyone have any idea what this error means, and how I can fix it?


I'm not sure what it's doing with sdf1. I have 5 other drives in the machine that are all part of a MDADM RAID array, unless for some reason the disk I'm trying to use is mounted as sdf in this case instead of sda as it was while using the live disk.


[IMG]https://i.imgur.com/77YMrUq.jpg[/IMG]

---

### Post by electr0 on 2020-05-15
I think this may be related to there being existing partitions on the drive.

This person seems to encounter a similar error:
[https://askubuntu.com/questions/1232261/ubuntu-20-04-server-install-fails-during-partitioning-subiquity-failure](https://askubuntu.com/questions/1232261/ubuntu-20-04-server-install-fails-during-partitioning-subiquity-failure)

Has anyone got any further insight?

---

