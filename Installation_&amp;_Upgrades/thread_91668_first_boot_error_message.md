---
title: "first boot error message"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by jrok311 on 2005-11-17
I installed the O/S and and after it loads the kernel, I get the error message: 

ALERT! /dev/hdc1 does not exist. Dropping to a shell!

BusyBox v1.00-pre10 (debian 20040623-1ubuntu22) Built-in shell (ash)

How do I fix it? thanks.

One more thing it also says: /bin/sh: can't access tty; job control turned off

---

### Post by BruceyBonus on 2005-12-05
Exactly the same error for me.

I'm a noob to Ubuntu, but used Mandriva a couple of times.

I tried installing Ubunto 5.10 "Breezy" on my system a couple of days ago - had this error message every time I try to boot Linux.

I almost gave up with Ubuntu and switched to Fedora Core, until I discovered this forum!

---

### Post by metoo on 2005-12-05
hdc1 is the first partition on the 3rd IDE harddisk. Do you have so many harddisks? Is the root file system on the first partition of the 3rd harddisk?

You can edit the harddisk/partition within grub.
Select the linux entry in grub, hit e, select the kernel line and hit e again. There should be the entry with hdc1. If your root partition is on another drive/partition, enter this instead and hit <Return> then b=boot
This is not permanent. Change /boot/grub/menu.lst if it works for you.

---

