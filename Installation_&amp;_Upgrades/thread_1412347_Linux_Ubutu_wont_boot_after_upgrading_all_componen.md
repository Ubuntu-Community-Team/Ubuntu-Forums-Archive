---
title: "Linux Ubutu wont boot after upgrading all components of upgrade manager"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by LinuxN00bTM on 2010-02-21
After i updated all the components of my update manager and ubuntu booted
i get
GNU GRUB version 1.97 beta 4
[Minimal BASH-like line editing is supported . For first word, TAB lists possible commands completions . Anywhere else TAB lists possible device/completions 

What i tried 
```
sudo dpkg-reconfigure xserver-xorg
sudo fdisk -l
and got unknown command sudo
also 
cat /boot/grub/menu/lst
file not found
```

Any Help is Greatly Appreciated

---

### Post by oldfred on 2010-02-21
You are not at a linux command line but at a grub command line:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail)

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

