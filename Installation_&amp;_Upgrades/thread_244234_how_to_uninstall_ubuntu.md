---
title: "how to uninstall ubuntu"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by macneil on 2006-08-26
need to no how to uninstall ubuntu BAD

---

### Post by Herman on 2006-08-26
That's very simple, depending on what else you have in your computer.

If you have no other operating systems you just format the disk using your favorite disk partitioning software and install a new operating system over the top of what was there before.

If there is another Linux operating system, and the other system has Grub, installed to MBR from that one, you can just delete the Ubuntu partition. You can also delete the other Linux's Grub's menu.lst entry for Ubuntu sometime when you get around to it.

If your only other operating system is some version of  Windows then you just need to overwrite your  IPL (stage1) for the Grub bootloader in the MBR with the IPL for the Windows bootloader.
The following web page has details, [Click Here.]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

Regards, Herman :D

---

