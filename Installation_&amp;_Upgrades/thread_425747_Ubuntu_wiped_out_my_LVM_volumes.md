---
title: "Ubuntu wiped out my LVM volumes"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by rockyl on 2007-04-27
First a little history. I've been a Linux user since 1995. I've heard such good things about Ubuntu I thought I would switch from Fedora Core 6. I've been running FC6 on an LVM partition for months.  I noticed here that you need to download and boot from an alternative CD, so I downloaded Feisty-alt. (BTW, the 30 minute wait for it to find the LVM volumes really sucks.) No luck. I didn't install Grub since it was already installed, and just modified the existing grub.conf. After rebooting it uncompressed vmlinuz but soon after it hung. I rebooted FC6 and it was OK. 

I figured I had enough normal partition space to try the standard desktop CD, so I downloaded 6.10 live. I did an apt-get on lvm2 just in case the install program might find my LVM volumes. No luck again, but I proceeded with the install. I chose to install Grub on one of the partitions since there didn't appear to be an option not to install it, and I didn't want to overwrite the existing one. BTW this partition was on hda and my LVM was on hdb. The installation proceeded and finished. I had to reboot to FC6 to play with grub.conf, so I tried that.

FC6 tried to boot but reported that it couldn't locate any LVM volumes. I booted my FC7 live CD and it can find the physical volume, but there are no logical volumes. My entire FC6 is wiped out. Luckily I made a backup of my /home directories, but it will be a pain to rebuild everything.

Bye-bye Ubuntu. I think I will file a bug report too.

---

### Post by zvacet on 2007-04-28
[https://help.ubuntu.com/community/Installation/LVMOnRaid]("https://help.ubuntu.com/community/Installation/LVMOnRaid")

---

### Post by rockyl on 2007-04-28
> **zvacet said:**
> [https://help.ubuntu.com/community/Installation/LVMOnRaid]("https://help.ubuntu.com/community/Installation/LVMOnRaid")

Doesn't help me. Like I said I decided to install on a non-LVM partition after the Alt-ISO installation didn't boot.

I think it may have tried to use my LVM partition for swap. My swap partition was located just before the LVM. I did check the format box for swap. Maybe it either overran the swap size or formatted the wrong partition. Fdisk still shows it as an LVM partition, but I downloaded a utility called testdisk that shows the contents as swap.

I did manage to restore the LVM partition structure from backup (/etc/lvm/backup), but I lost everything on the first partition.

---

