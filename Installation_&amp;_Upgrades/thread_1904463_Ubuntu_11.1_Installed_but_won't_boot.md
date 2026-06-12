---
title: "Ubuntu 11.1 Installed but won't boot"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by WCFTWeasel on 2012-01-04
I'm sure this has been answered already, but I'm tired of searching for an answer to my actual questions.

I've installed Ubuntu on a previously Windows PC (no dual boot, all Linux).

The install process worked without a hitch, but when I try to boot, all I get is a cursor.

I'm guessing Grub didn't install properly, but there's no terminal access... nothing.

If I boot to the CD, I don't have sufficient permissions to edit any of the files that other threads have suggested.

What do I do?

---

### Post by fantab on 2012-01-04
Re-Install and install GRUB on the hard disk (/dev/sda or /dev/sdb) and not on Partitions (/dev/sda1, /dev/sdb4, etc).

---

### Post by darkod on 2012-01-05
From live mode post the output of:
sudo fdisk -l (small L)

---

