---
title: "Installing Dual-Boot Breezy Over Dual-Boot Hoary"
date: 2006-03-11
forum: Installation &amp; Upgrades
---

### Post by floppy on 2006-03-11
I would like to do a fresh install of Ubuntu, overwriting my current Hoary installation. I have the install/live DVD.

My concern is that I am currently dual-booting Ubuntu and Windows XP using GRUB. How do I do this install and not lose my dual-boot to XP?

It is ESSENTIAL that I do not end up losing my current XP install and dual-boot.

Any hand-holding with this will be deeply appreciated.

---

### Post by munga_bill on 2006-03-11
Hi floppy, first back up any important files. You could follow herman's install site here [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) with pictures and yours will be the same until about step number 8 or so.
At step number 9, your picture will be different, you'll see a list of partitions, likely your Windows, Ubuntu and a swap area. Delete your old Ubuntu partitions, but do not delete any fat32 or ntfs partitions because they might be Windows'. That will turn that partition into 'free space'. Then just ignore a lot of the next steps on that web-page and skip all the way down to step number 22.4, where it says to highlight the free space and select it for automatically partition the free space. After that the rest is easy, it should be something like the rest of the install on that site.
munga_bill

---

### Post by floppy on 2006-03-13
Thanks! Very much appreciated!

---

