---
title: "Dual boot problem."
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by Xtremegamerjonnyd on 2008-05-14
I had ubuntu set up as the only operating system on my laptop, but needed windows for something so I partitioned out space, etc. etc. and installed it. Now whenever I boot my system it boots in windows and not ubuntu and I don't know how to set it to boot in ubuntu.

P.S. There is now message or pop-up or whatever asking if I want to boot in ubuntu.

---

### Post by housam on 2008-05-14
use this guide :
[[COLOR="Red"]_https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?")

---

### Post by forestpixie on 2008-05-14
You need to reinstall grub is all 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Edit - 
You weren't there when I refreshed

---

### Post by hermes0710 on 2008-05-14
Start ubuntu in live mode from the installation cd. Run a terminal and execute: ```
sudo grub

```
```
find /boot/grub/stage1
```
Let's suppose it gives "(hda,b)" as an output.
Execute:
```
root (hda,b)
```
```
setup (hda)
```
replacing "a","b" accordingly.

Reboot

---

### Post by Xtremegamerjonnyd on 2008-05-14
Thanks for the help guys. [Solved]

---

