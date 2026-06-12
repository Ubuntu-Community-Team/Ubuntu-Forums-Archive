---
title: "Old Kernel In Grub After 9.10-10.04 LTS Upgrade"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by Cody Larson on 2010-05-12
I performed an upgrade via the Update Manager from 9.10 to 10.04 LTS and it seemed to go flawlessly.

However, now I cannot seem to be able to remove the old Kernel from 9.10 in the package manager. It does not even show 2.6.32-21 as installed but it still shows the old Kernel in Grub. I did a sudo update-grub but it was to no avail. Any ideas? I am a Linux/Ubuntu n00b so I'm not the brightest when it comes to this.

Nevermind, I solved this. Thank you. I was searching for 2.6.32-21 rather than 2.6.31-21. Oops.

---

### Post by davidmohammed on 2010-05-12
when you do sudo update-grub is the following displayed in the output?

Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst

if so delete the menu.lst file.

regenerate  your grub.cfg as follows

sudo grub-mkconfig -o /boot/grub/grub.cfg

---

