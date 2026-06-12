---
title: "installing windows XP after Ubuntu 7.04 has been installed"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by xargon on 2007-09-21
Hi everyone,

I am having a really hard time installing XP alongside my Ubuntu installation.

I have a 250 GB hard disk and about 100 GB of unpartitioned space that I want to install XP on. However, when I boot from the XP disk, I get the screen "Inspecting you hardware configuration" and then the screen does blank! I suspect that maybe it does like my linux partitions.

I am wondering if anyone faced similar issues before and found some solution for it.

Cheers,
xarg

---

### Post by Pumalite on 2007-09-21
Ideally XP should go first, among others, the issue you mentioned. XP likes to be sda1. In fact if you could save your /home and data, use Gparted to delete all partitions, format ntfs, install XP and then Ubuntu; you would end up with a trouble free machine.

---

