---
title: "Ubuntu 18.04 hangs at Started Update UTMP about System Runlevel Changes"
date: 2018-07-22
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2018-07-22
Hi 
I have done some installation yesterday trying to install tensorflow
I  use this link [https://medium.com/codezillas/step-by-step-guide-to-install-tensorflow-gpu-on-ubuntu-18-04-lts-6feceb0df5c0](https://medium.com/codezillas/step-by-step-guide-to-install-tensorflow-gpu-on-ubuntu-18-04-lts-6feceb0df5c0)
Today I tried to start my computer it hangs, it can't boot
 &#8220;Started Update UTMP about System Runlevel Changes.&#8221;
And I see also the system is read only state
howcan I change that ?
I have googled a lots but can find a solution
please help
Thanks

---

### Post by hoboy on 2018-07-23
Hi guys any ideas ?

---

### Post by mIk3_08 on 2018-07-23
Boot Repair [Click Here]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by mIk3_08 on 2018-07-24
try; 
```
keyboard keys: ctrl+alt+F2
```
remove gnome with
```
sudo apt-get autoremove gnome-core gnome-shell gnome-session
```
reinstall it 
```
sudo apt-get install gnome-core gnome-shell gnome-session
```
then reboot

---

### Post by axzxc1236 on 2018-08-13
I got the same problem today!

I was able to SSH into my Ubuntu VM, and I deleted some unused files, right after delete these files, the login screen just shows up.

---

