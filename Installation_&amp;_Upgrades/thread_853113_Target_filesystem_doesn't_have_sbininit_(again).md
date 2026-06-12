---
title: "Target filesystem doesn't have /sbin/init (again)"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by davidleelambert on 2008-07-08
I recently did a dist-upgrade to Hardy,  and now the computer won't boot.  Grub runs, but any option drops me to the BusyBox prompt.  In the "rescue-mode" options,  I can see the following message,  which might be significant:

[FONT="Courier New"]mount: Mounting /dev/disk/by-uuid/fc5... on /root failed: Device or resource busy[/FONT]

The last message before the BusyBox prompt is

[FONT="Courier New"]Target filesystem doesn't have /sbin/init[/FONT]

I've found old postings for a similar error that suggest changing the root=UUID=... lines in /boot/grub/menu.lst to root=/dev/sd... ; but that doesn't help.

Any idea what the problem is?

--
DLL

---

### Post by davidleelambert on 2008-07-08
From BusyBox,  the following command works:

[FONT="Courier New"]mount /dev/mapper/sda1 /root[/FONT]

However,  I'm not sure what to do after that,  or how to make the fix permanent so the system can reboot.  Any advice?

---

