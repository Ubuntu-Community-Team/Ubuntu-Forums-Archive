---
title: "Problems with Additional drivers and Installing graphic drivers"
date: 2012-07-19
forum: Installation &amp; Upgrades
---

### Post by MrDuki on 2012-07-19
I have problems with installing NVIDIA graphic drivers and Additional drivers.
I had tried to upgrade graphic drivers because current version have bug ,glitches and weird screen effects on some programs.
When i tried to upgrade current version with graphic drivers from NVIDIA, came message in which was written that i cant upgrade graphic drivers because of X server.After i disable X server , came message that i need to remove Nouveau drivers.
I followed procedure from [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) and i even tried to blacklist that driver on startup,but same message occur when i tried again.
I looked on web that i can turn off Nouveau using Additional drivers but they wont work.Window of it only loads and shut down itself.
Since i removed Nouveau drivers i have weird bug on System settings where mouse pointer disappears each time when i mouse hover on one of icon on it.
[LEFT]Im using Ubuntu 12.04 LTS .
[/LEFT]

---

### Post by efflandt on 2012-07-19
What video card or chip do you have?  When you install 12.04 with nvidia video card or chip it usually automatically installs nvidia-current during installation.  The x-swat repository can be added if you need most recent nvidia drivers.  However, I would not know what to do if you have older nvidia hardware that the current drivers do not support.

The only thing I needed to do to install with GTX 550 Ti was enable **nomodeset** kernel parameter to boot to a live/install system. But once nvidia-current was automatically installed during installation, I did not need any boot parameters for the installed system and everything works fine.

---

### Post by bogan on 2012-07-20
Hi!,** MrDuki,**

From your description you need to clear out the nvidia drivers and start again.

Please Post:
```
 lspci -nnk | grep  -iA3 VGA
sudo apt-cache policy nvidia-current 
cat /sys/module/nvidia/version 
/usr/lib/nux/unity_support_test -p
```Chao!, **bogan**.

---

