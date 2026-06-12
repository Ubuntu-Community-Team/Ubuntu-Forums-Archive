---
title: "Installation type no hard drive"
date: 2016-12-29
forum: Installation &amp; Upgrades
---

### Post by erik8752 on 2016-12-29
Hi,
I tried to install ubuntu 16.10 from live flash disc.
[LIST=1]
[*]I started in Windows 10, where I created 100 GB partition without formating. 
[*]I then restarted the computer, disabled Legacy support and secureboot. 
[*]I booted Ubuntu  16.10 from live USB flash disk and selected "try Ubuntu". 
[*]After Ubuntu loaded **I started Gparted and created ext4 partitions** for home and root and one for swap. 
[*]Then I clicked "install ubuntu 16.10" desktop icon. Selected language, connected to WiFi, Under "preparing to install ubuntu I checked both options and I got to "installation type", where I should select the partition I'd like to install on. **The problem is that I can only see the flash disc I am installing from and the hard drive partitions are completely missing.** 
[/LIST]
I am using:
HP ENVY TouchSmart 4-1160ec
4GB RAM
SSD and HD - (8GB and 512GB) in windows there is a sowtware raid which creates something like SSHD

I remember there used to be some problem with too many hard drive partitions or with the SSD and HD when I tried last time but it was like 2 years ago...

---

### Post by deadflowr on 2016-12-29
When you hover over those partitions in gparted that have the red dot with exclamation points in them (for /dev/sda3, sda4, and sda6)
what does it tell you. (You might need to click on the dot to get the info in wants to tell you)

That red dot usually means some error is preventing further procedures.

---

### Post by ajgreeny on 2016-12-29
I see you are using GPT partitions and UEFI and it is therefore essential that you boot the USB in UEFI mode, and thus install Ubuntu in uefi mode as well.

However, as you say that Windows is using software raid, I believe you will not have any success, as Linux can not see or use disks from a software raid system, if I remember correctly.

When you get to the installation stage from the live OS choose "Something Else" and the partitions available should all show if Linux can read the disk properly.

---

### Post by erik8752 on 2016-12-30
After removing dmraid it works. Thanks

---

### Post by ajgreeny on 2016-12-31
Great! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

