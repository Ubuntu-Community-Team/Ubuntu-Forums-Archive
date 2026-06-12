---
title: "Try to install again from USB - grub failed to install"
date: 2016-01-10
forum: Installation &amp; Upgrades
---

### Post by stribor2 on 2016-01-10
Since I had al these problems I posted in previous messages I tried to reinstall Ubuntu again. 
Installation wwnt fine until the point where I got this warning message. 

The "grub-Efi-amd64-signed" package failed to install into /target/. Without the GRUB boot loader the installation system will not boot"

---

### Post by Geoffrey_Arndt on 2016-01-10
Stribor, see the last 2 posts in your original thread  . . . the reason for the original problem is likely the lack of the proprietary gpu driver, which can be installed easily via:   System Settings>Software & Updates>Additional Drivers tab.

Now, about your current situation, what did you specify in the install screens when it got to the screen about where to put the grub bootloader?   More info would be helpful.

---

