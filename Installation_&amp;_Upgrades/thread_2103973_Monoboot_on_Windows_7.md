---
title: "Monoboot on Windows 7"
date: 2013-01-11
forum: Installation &amp; Upgrades
---

### Post by Taluus on 2013-01-11
Hi,

I just received a new computer (a Sony Vaio SVS1511A4E/B), shipped with Windows 7 on it. I passed the step to install Ubuntu 12.10 on this machine on EFI mode via a LiveUSB key.

So far, so good (even if I spent a good day to solve the fact that even if my BIOS was on EFI mode, my CD device was kind of not into this mode - as I have a simple bios, using a liveUSB key). But, When I restart, grub does not load, and Windows is directly loaded.

I ran Boot-Repair on my machine two to three times (separated by reinstallations, ... etc), but it didn't solve the problem. Here is a screen of what my partitions looks like :

[CENTER][IMG]http://img824.imageshack.us/img824/1571/screenshotfrom201301112.png[/IMG][/CENTER]

The partitions from sda1 to sda5 are the ones that came shipped with the product. sda3 is the EFI partition, and sda5 is the ntfs partition, containing my Windows installation. sda6 is my /boot partition from my Ubuntu installation, sda9 my root (/) partition, and the last one, sda8 is the /home partition.

And you may find a boot-info here : [http://paste.ubuntu.com/1521011](http://paste.ubuntu.com/1521011)

For now, I'm thinking of using a VM, as I'm getting pretty tired for trying non-stop to get this working for the past couple of days... If you have any questions, please feel free to ask.

Thanks.

---

### Post by Taluus on 2013-01-12
A little Up ? 

Thanks for your attention.

(Note : I just removed the partitions from ubuntu, and using it in a vm, bnut it's way less sexier than having it not virtualized...)

---

