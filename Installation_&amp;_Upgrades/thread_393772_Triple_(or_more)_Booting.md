---
title: "Triple (or more) Booting"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by NoVista on 2007-03-26
Current setup is a dual boot with Edgy/WinXP.
I now want to install Ubuntu Ultimate, on another drive.
After the install, will Grub let me now choose  between Edgy/WinXP/Ubuntu Ultimate?

A noob needs to know .. ..

---

### Post by girishv on 2007-03-26
Hi,

I am (and most probably other Feisty users) triple booting Edgy, Feisty and windows. It is not a problem. All you have to modify is the /boot/grub/menu.lst
Ultimate is just another flavour of Ubuntu and when ultimate is installed, it should add windows automagically. Just add Edgy information into the above file.

Girish

---

