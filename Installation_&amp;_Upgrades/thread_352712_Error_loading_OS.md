---
title: "Error loading OS"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by crumbum on 2007-02-03
I did a fresh install of  xp on my primary drive and ubuntu on my slave drive.  When I start up I get error loading OS.  If I use the live cd to load and the pick load frome hard disk  the grub loads and I can choose either operating system perfectly.  So I figured i most not have grub installed .  So I sudo apt get grub and it tells me I have the newst grub installed.

---

### Post by taurus on 2007-02-03
Assuming /boot/grub/menu.lst configured properly, you can install GRUB to MBR with

```
sudo grub-install /dev/hda
```

---

