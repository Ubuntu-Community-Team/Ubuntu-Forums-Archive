---
title: "Installing kernel 3.16 at Xubuntu 14.04 LTS"
date: 2015-02-20
forum: Installation &amp; Upgrades
---

### Post by dowoshek on 2015-02-20
Hello,
I'm trying to install kernel 3.16 at Xubuntu 14.04 LTS. What is the recommended way to do it?

I tried the below instruction:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
But when I try to install packages:
xserver-xorg-lts-utopic
libgl1-mesa-glx-lts-utopic
libegl1-mesa-drivers-lts-utopic
it wants to remove a lot of stuff.

---

### Post by tokyobadger on 2015-02-21
with the release of ubuntu-14.04.2 which has the option of the 3.16 kernel you could 
```
sudo apt-get install --install-recommends linux-generic-lts-utopic xserver-xorg-lts-utopic libgl1-mesa-glx-lts-utopic libegl1-mesa-drivers-lts-utopic
```
[from the ubuntu wiki](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

