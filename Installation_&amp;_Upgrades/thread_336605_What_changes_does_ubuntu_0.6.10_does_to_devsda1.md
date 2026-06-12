---
title: "What changes does ubuntu 0.6.10 does to /dev/sda1?"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by tejvenim on 2007-01-11
Suppose that I have Windows XP in /dev/sda1. Suppose I install ubuntu 0.6.10.

Is this all the changes that ubuntu makes to /dev/sda1?
-- 512bytes MBR
-- 30kb Grub stage 1.5

I want to know because I want to backup everything before installing ubuntu 0.6.10, so that I can restore everything in case something goes wrong.

Also I want to know how to backup /dev/sda1. I know that I can backup MBR by using "dd if=/dev/sda1 of=mbr.backup bs=512 count=1".

Can I also use dd to backup the 30kb Grub stage 1.5, i.e. "dd if=/dev/sda1 of=grub_1_5.backup bs=30720 count=1"?

---

