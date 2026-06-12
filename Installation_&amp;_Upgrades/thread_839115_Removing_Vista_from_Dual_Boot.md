---
title: "Removing Vista from Dual Boot"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by d4v1dv00 on 2008-06-24
Hi there,

I was thinking now its time to remove Vista from my dual boot configuration and reclaim the hard drive space occupied by Vista after comfortable with Ubuntu now.

What should I do? Currently /dev/sda1 - Vista and Ubuntu installed at /dev/sda5

How can I remove Vista (format it) and then make Ubuntu utilizes all space?

Many thanks

---

### Post by iaculallad on 2008-06-24
> **d4v1dv00 said:**
> Hi there,

I was thinking now its time to remove Vista from my dual boot configuration and reclaim the hard drive space occupied by Vista after comfortable with Ubuntu now.

What should I do? Currently /dev/sda1 - Vista and Ubuntu installed at /dev/sda5

How can I remove Vista (format it) and then make Ubuntu utilizes all space?

Many thanks

Im assuming that you're using a dedicated partition for your Ubuntu and this is not in Wubi.

Just edit your /boot/grub/menu.lst file and delete/comment the entry for your windoze vista boot option. From there, you can use GParted to format your /dev/sda1 where your windoze resides.

Be sure to backup your important data first from /dev/sda1 before formatting it.

---

