---
title: "All USB not working after upgrade to quantal"
date: 2013-06-30
forum: Installation &amp; Upgrades
---

### Post by aaronp on 2013-06-30
Hi all,

I upgraded my precise system to quantal (via the do-release-upgrade process).

It seemed to work fine until the reboot at which point it hung on the splash screen saying the disk for /media/store is not present/ready and gives me the option to wait, skip or manually resolve it. At this point my keyboard will not respond so I have to hard reset. Ultimately I am able to get grub into recovery mode or alter the boot parameters in grub no problems, but the keyboard is then unresponsive. 

Given /media/store is a USB external drive I suspect there is an issue with USB drivers since the update (not a hardware problem since my keyboard works in the grub menu) but without a keyboard I have no way of getting into anything to figure it out. Unfortunately I don't have a spare ps/2 keyboard or mouse available.

I figure I can get into a livecd but from there I have no idea how to debug and fix the issue in the USB drivers within the Ubuntu that is installed.

Any ideas?

Thanks
Aaron

---

