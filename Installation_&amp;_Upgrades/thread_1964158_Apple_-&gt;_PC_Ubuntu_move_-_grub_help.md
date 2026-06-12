---
title: "Apple -&gt; PC Ubuntu move - grub help"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by Micronaut on 2012-04-23
Hi,

For a while I was using Ubuntu 11.10 on a Mac Pro with EFI Grub installed.  I recently moved back to a PC but forgot to change GRUB before I moved the hard drive.  In the new machine grub wont load and produces a "device not found error".  I attempted to re-install GRUB from the LiveCD but I can't see the Linux partition using fdisk or gparted.  I can only see the Windows partition.

The data should be still in place on the drive, I'm just not sure why Ubuntu wont see the Linux partition, and I'm not sure if it's the EFI GRUB.

Can anybody provide any assistance in recovering the Linux partition and re-installing regular GRUB?


Thanks for any assistance.

---

### Post by zvacet on 2012-04-23
Try [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") and first try **recommended repair**.

---

