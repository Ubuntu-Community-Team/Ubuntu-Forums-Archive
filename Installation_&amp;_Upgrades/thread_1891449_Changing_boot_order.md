---
title: "Changing boot order"
date: 2011-12-05
forum: Installation &amp; Upgrades
---

### Post by David McGlade on 2011-12-05
I have installed 11.04 on a partition on a second hard drive in my Fujitsu Siemens Scaleo P with a recent clean install of XP on the main drive. The PC boots into XP but I am unable to locate the BIOS to change the boot order. I press DEL for "Set- up" but cannot fathom how to find boot order. Pressing F2 or F12 does nothing.
 
Loads of thanks,
 
dave

---

### Post by jerrrys on 2011-12-07
If you are booting with GRUB you can install "startup manager" to change boot order.

---

### Post by drs305 on 2011-12-07
The bootloader is controlled by what is written to the boot drive's MBR. If the MBR points to Windows, the Windows bootloader will be used and probably doesn't know about Ubuntu.

If Grub 2 is installed in the MBR, it will point to the Ubuntu partition and launch Grub, which should be able to boot to either Windows or Ubuntu.

You can probably fix things by booting the Ubuntu LiveCD and installing Boot Repair (see signature line for link). It's a very good app and probably can do what you need.

If it can't fix things so you see both OS's, it has the ability of running the Boot Info Script. This script is great for analyzing problems, and if you post the link to the RESULTS.txt file it generates we can see what's going on.

Once things are running properly, if you need to tweak things, I'd recommend Grub Customizer. It's a great app for reordering, renaming, etc Grub menu items. See "Customizer" link.

---

### Post by David McGlade on 2011-12-08
Thank you for the advice, I'll give it a go.
 
dave

---

