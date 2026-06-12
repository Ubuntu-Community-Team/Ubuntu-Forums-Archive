---
title: "boot menu gone after install of XP"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by jwflammer on 2010-03-08
yeah so i used gparted to resize a partion and installed windows xp now i cant get back to ubuntu

---

### Post by lindsay7 on 2010-03-08
Which version of Ubuntu did you have installed. 8.10, 9.04, 9.10, etc


This will tell you how to make sure which grub is loaded and how to fix your problem.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by bumanie on 2010-03-08
Windows doesn't play nicely with other OSes - the windows installation, will have overwritten the mbr and got rid of all references to grub. You will have to reinstall grub via a live cd - the process is different, depending on whether you have grub-legacy or grub 2 as the ubuntu boot manager. Read the link sent in the previous post and if you don't understand something, post back with specific questions.

---

