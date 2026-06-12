---
title: "Installing windows XP to system with Ubuntu"
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by wezzer-foo on 2005-11-10
Hi all,

Currently I have setup like this:
/dev/hda1 Ubuntu linux
/dev/hda5 Swap for ubuntu
/dev/hda3 Windows 2000

Now I'd like to wipe Windows 2000 completely and then install Windows XP on that partition. I am afraid that installing Windows XP will ruin my completely working Ubuntu. Do you have any tips regarding this matter? Is it even possible to install Windows without breaking Ubuntu? I have tried it before and that totally mixed up GRUB etc.

---

### Post by Susana on 2005-11-10
[QUOTE=wezzer-foo]Hi all,

Currently I have setup like this:
/dev/hda1 Ubuntu linux
/dev/hda5 Swap for ubuntu
/dev/hda3 Windows 2000

Now I'd like to wipe Windows 2000 completely and then install Windows XP on that partition. I am afraid that installing Windows XP will ruin my completely working Ubuntu. Do you have any tips regarding this matter? Is it even possible to install Windows without breaking Ubuntu? I have tried it before and that totally mixed up GRUB etc.[/QUOTE]

Hi!

You can see how to restore grub here:
[http://www.ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://www.ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

---

### Post by wezzer-foo on 2005-11-10
Thanks! I'll try that if something goes wrong.

---

### Post by wezzer-foo on 2005-11-10
Next question: is it even possible to install Windows to non-primary partition, /dev/hda3 for example? I thought that Windows needs to be installed on /dev/hda1...

---

