---
title: "Could Not Install Ubuntu Netbook Via Wubi Need Help"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by spysense on 2011-02-10
i'm new to this whole ubuntu, linux thing. my laptop doesnt have any cdrom drive and all usbs are broken so wubi is my only option. oh and i use win 7 starter. i tried to install netbook edition to my laptop but i always get error. i can install with only "acpi workarounds". i dont even understand what it is the error and why i'm getting this error. 

error is

> Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda2 does not exist. Dropping to a shell!

BusyBox v.1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash) Enter 'help' for a list of built-in commands

(initramfs)


---

### Post by dino99 on 2011-02-10
for real install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by spysense on 2011-02-10
sorry but as far as i understand you want me to create 3 separate partitions on my hdd. will this work? i can only install ubuntu with wubi

---

### Post by Rubi1200 on 2011-02-10
With no CD drive and USB broken you are likely to face difficulties no matter what you try and install.

I recommend you first get the USB issue sorted out before trying to move ahead.

If you install Wubi and something goes wrong (which can happen), the way to fix it is usually from either a LiveCD or LiveUSB.

What dino99 suggested is for installing to the drive on a dedicated partition. Do not try this with a Wubi install; it will not work.

For more information, read the Wubi Guide:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by spysense on 2011-02-10
i tried all of them liveusb or livecd but they arent working either. su wubi is my only option.

---

