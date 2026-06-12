---
title: "System won't boot Windows (2 Drives)"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by VincentRP on 2007-03-06
Hey,

I just installed a second hard drive in my laptop.  The original drive has Windows XP on it.  The new drive contains Ubuntu.  Everything installed just fine, and I'm currently in the process of getting the necessary software to make the system productive.  However, I can't seem to boot into Windows.  The Ubuntu installer automatically configured and installed GRUB and I didn't get much chance to see what it was doing.  When I restart, it boots into Ubuntu by default with no bootloader option.  Does anyone know where the bootloader installs to so I can try to diagnose this problem?

---

### Post by Kateikyoushi on 2007-03-06
It is in /boot/grub/menu.lst. To add windows to the menu read this. [LINK]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_Windows_entry_into_GRUB_menu")

Can list your partitions with the following command. 
```
fdisk -l
```

---

