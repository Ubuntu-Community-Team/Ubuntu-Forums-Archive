---
title: "Grub legacy install"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by ags40 on 2009-12-10
Is there an option to install Grub legacy while first installing? Or is Grub2 forced onto you? Thanks.

---

### Post by lemming465 on 2009-12-12
If you are doing a live CD install of Ubuntu 9.10 you will get grub2 by default and not be able to control that.  I'm not sure if the alternate install CD would let you pick grub1 during package selection instead.  Personally, I don't find editing /etc/grub.d/40_custom instead of /boot/grub/menu.lst so onerous that I have to downgrade.  However, you could definitely downgrade back to grub1 after the install, if you needed to.

---

### Post by jollysnowman on 2009-12-12
What I did was install 9.04, use dpkg to keep grub from being upgrade, and then perform a dist-upgrade.

---

### Post by lemming465 on 2009-12-13
Also works, yup.  Actually, the 9.04 -> 9.10 upgrade won't upgrade grub by default; upgraders who want grub2 have to specifically install that afterwards.  Never argue with success is one motto; glad you got to where you wanted.

---

