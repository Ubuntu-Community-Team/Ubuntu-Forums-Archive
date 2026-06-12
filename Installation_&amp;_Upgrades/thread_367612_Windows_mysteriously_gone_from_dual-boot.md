---
title: "Windows mysteriously gone from dual-boot"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by Kaat on 2007-02-22
Hi everyone,

I'm kind of freaking out.

A couple of weeks ago I installed Linux Ubuntu 6.10 as a dual-boot with Windows XP Home. 
About an hour ago, Ubuntu did some updates and had to be restarted, so I shutdown my computer and restart. The dual-boot window shows, but it only says "Linux generic ..." and my Windows boot is gone.

Is my Windows partition still on my harddisk? How do I know where my Windows XP is hiding and how do I get it back in the dual-boot screen?

Kaat

---

### Post by Kateikyoushi on 2007-02-22
It just downloaded a new kernel and added to the list unfortunately seems it removed your XP from the grub list as well.

You can check your partitions with. 
```
sudo fdisk -l
```

I am sure it is there.

Follow these steps to add back windows to your grub. [LINK]("http://ubuntuguide.org/wiki/Dapper#How_to_add_Windows_entry_into_GRUB_menu")

---

### Post by Hendrixski on 2007-02-22
it could be a problem with GRUB?  maybe it's just not showing the other partitions, even though they're there?

---

### Post by Herman on 2007-02-23
Hello all,
This happens very often and is usually caused by misleading information being passed on by well intentioned people about how to make grub boot Windows by default instead of Ubuntu.
Many inexperienced users think that they can just edit their menu.lst files to do that by simply cutting their Windows entry from the bottom of the list and pasting it to the top of the list. Then they forget all about it and they are happy for a while until they receive a kernel update for Ubuntu. When the kernel is updated, Ubuntu runs a script called update-grub, which re-writes the menu.lst file according to pre-configured instructions in the debian automagic kernels list, right above the Ubuntu entries in the menu.lst file.
When the Windows entry is in the automagic kernels list, it is automagically deleted because it doesn't belong there. There is not anything wrong with grub. Grub is working perfectly. It is the user who has made a mistake.
The best way to make Windows boot by default is to paste the Windows entry above the top of the automagic kernels list.
Or, follow the advice in this link, [Changing the default (operating system booted by the timer)]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")

Happy dual booting,
Regards, Herman :)

---

