---
title: "Interesting question"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by innoBy on 2008-01-23
Would it be possible, for someone to install windows to a separate partition without ever rebooting ubuntu?

If so can someone show me how.

---

### Post by Speedoo on 2008-01-23
I'm pretty sure you have to install Windows first to make a dual boot system.  Why don't you want to reboot Ubunutu?

---

### Post by Rocket2DMn on 2008-01-24
I don't see how this is possible without doing it in a Virtual Machine (VM).
It is suggested that you install Windows first, but since you already have Ubuntu installed, it's not terribly more difficult to get the dual boot setup.  You will just have to "recover" Ubuntu after you install Windows because Windows will install its own bootloader which doesn't give you the option to boot into Ubuntu.  See [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

You may want to consider resizing your hard drive partitions using GParted on the Ubuntu LiveCD so you can clear out an area to install Windows to.  Of course, make good backups first, because you never know!

---

