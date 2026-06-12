---
title: "Remove ATI/AMD proprietary FGLRX driver before doing an upgrade from 9.10 to 10.04?"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by proggy on 2010-10-04
I need a quick answer if possible, is it better to remove the proprietary drivers before upgrading to 10.04 from 9.10? Or should i have the open source drivers installed?
A clean install is not an option on this machine.

---

### Post by andrewthomas on 2010-10-04
Remove the proprietary driver before an upgrade.

Delete any xorg.conf

---

### Post by lukeiamyourfather on 2010-10-04
> **proggy said:**
> I need a quick answer if possible, is it better to remove the proprietary drivers before upgrading to 10.04 from 9.10? Or should i have the open source drivers installed?
A clean install is not an option on this machine.

If you installed it through the Ubuntu repositories then you can just remove the package for the driver. If you installed it manually things are more complicated. If installed through the package manage I imagine it would be upgraded automatically too. If you installed it manually then definitely when you upgrade it will break, so uninstall first.

---

### Post by proggy on 2010-10-04
Success! thank you! 
An upgrade is never for the faint of heart , luckily it was straight forward  and i was not asked to install grub on my Windows mbr destryoing like it did once but gave me the choice of keeping the local Grub already installed.:guitar:

---

