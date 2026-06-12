---
title: "Install Windows while i got ubuntu on my hdd"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by gigermunit on 2007-03-24
How would i go about installing windows while keeping ubuntu on this hdd and be able to boot into both?

---

### Post by mac.ryan on 2007-03-24
The problem (at least with XP, I haven't tried with Vista), is that M$ doesn't like competitors, neither in the form of alternate OS on the same HD, so windows will install itself and make itself the only bootable thing.

You can however "recover" your ubuntu installation using the Live CD after windows will be installed. I never did this myself, but there is an extensive how-to on the community contributed documentation:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Just make sure windows installs itself on one specific partition, and does not erase the entire HD...

Best luck!

---

### Post by chewearn on 2007-03-24
In short:
1. create empty space on your harddisk for Windows by resizing one existing partition
2. install Windows on the empty space
3. reinstall grub from LiveCD
4. add entry for Windows in /etc/fstab

Reply (with output of "sudo fdisk -l"), if you need a more detailed walk through for each of these tasks.

---

### Post by gigermunit on 2007-03-24
how do i install just grub?

---

### Post by chewearn on 2007-03-24
Here is the howto:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

EDIT: Or see the link given by mac.ryan in post #2.

---

### Post by gigermunit on 2007-03-24
Screw it since it's so easy just to reinstall ubuntu and my wireless and gfx card drivers i just gunna do that.

---

