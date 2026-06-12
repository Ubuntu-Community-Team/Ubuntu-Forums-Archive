---
title: "Upgrade from 12.04 to 13.10 Problems"
date: 2014-04-15
forum: Installation &amp; Upgrades
---

### Post by kyaustad on 2014-04-15
I recently upgraded to 13.10 from 12.04 like the title says. 12.04 ran great on my computer. 64 bit. I upgraded to 13.10 with a clean install on a seperate hard drive so as not to interfere and ease. When i boot into it i get the GRUB menu but i boot into ubuntu and all i get is a black screen and then my monitor says no signal and shuts off. How do i fix this? I am going to upgrade to 14.04 in two days when it is released so if that version doesnt work with this same problem then i want to know how to fix it. Any help is appreciated!! Thanks!

---

### Post by grahammechanical on 2014-04-15
When you did that clean install of 13.10, did you tick to install third party software at the same time? If you did that then a proprietary video driver was also installed. That driver may be causing this problem.

At the Grub boot menu go to Advance Options for Ubuntu and open that sub-menu and then select Recovery mode. At the Recovery menu select Resume. That should get you to a desktop using the Ubuntu fallback open source video driver. Once at the desktop go to System Settings>Software and Updates>Additional Drivers tab and experiment with another video driver.

When we run the Ubuntu live session we use an open source video driver (Nouveau). And things work fine. But if we install and tick to install third party software then we switch to a proprietary video. That is why the first reboot can sometimes break the desktop.

We might need to know some more information about your computer hardware, especially the graphic adapter.

Regards.

---

### Post by kyaustad on 2014-04-15
ok thanks ill check it out when i install 14.04 if it doesnt work. Thanks!

---

