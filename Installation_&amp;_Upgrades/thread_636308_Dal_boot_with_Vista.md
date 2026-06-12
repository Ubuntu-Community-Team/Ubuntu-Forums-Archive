---
title: "Dal boot with Vista"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by eddweed on 2007-12-09
Hi,
I've just bought an Acer Aspire 5633 laptop with an 160 gig drive partitioned as follows.
8 gig hidden primary acer recovery partition
70 gig Vista 'C' drive
70 gig Data 'D' drive
I've shrunk the 'D' drive by 15 gig with Vista disk manager to make space for Ubuntu. All three above partitions are primary. I want to install Ubuntu to the 15 gig space I created and use the 'easybcd' programme to add it to the windows bootloader so as to not affect the original acer modified mbr/bootloader incase I need to recover Vista from the hidden partition. During the installation of Ubuntu when I try to manually create the swap and / partitions I can only create 1 more primary or the 2 logical partitions. I then add the Ubuntu entry via easybcd to the windows bootloader and find no matter what combination of partitions and options available it will not boot to Ubuntu. I deselect the install grub to bootsector during installation.
I'm now completely lost and appreciate any help.
Thanks

---

### Post by maybeway36 on 2007-12-09
When you install Ubuntu, make / and swap both logical. I think that should work.

---

### Post by eddweed on 2007-12-09
Thanks for the quick response. I've tried making them both logical and when I add the / partition to the boot loader via easybcd it doesn't boot. I tried many combinations and I think this one results in either an 'Insert a system disk error' or puts you to a grub command prompt. I will install again to 2 logical drives and report back.
Thanks for the help

---

