---
title: "isohybrid error"
date: 2021-07-02
forum: Installation &amp; Upgrades
---

### Post by m3t3ors on 2021-07-02
so i fancied trying out some different distros and came across nitrux. i thought i could use it on my office laptop but when i try create the usb it asks if i want to burn as iso or DD. as iv'e not seen this before i searched google and it says its a isohybrid file.?

whats the easiest way to create the usb here?

thanks for any help

---

### Post by sudodus on 2021-07-02
If it is an isohybrid file, you can clone it (from the iso file to the USB pendrive) and you will get a bootable USB drive.

Are you trying with Rufus in Windows? Or some other tool, maybe in Linux?

[hr][/hr]
([This link](https://unix.stackexchange.com/questions/484541/how-to-install-nitrux-os) indicates that the distribution file is **not** an isohybrid file, not even an iso file that can create a live system. The linked page is from 2018, so it is probably obsolete (and there seems to be an isohybrid file now.))

[**This link** is more up to date](https://techviewleo.com/install-nitrux-linux-step-by-step-with-screenshots/) and indicates that there is an isohybrid file, and that you can use cloning tools. In Ubuntu I would try [**mkusb**](https://help.ubuntu.com/community/mkusb) but there are many alternatives, for example **Disks** (alias gnome-disks), that are safer than dd (nicknamed 'Disk Destroyer' or 'Data Destroyer') for this purpose.

---

### Post by m3t3ors on 2021-07-02
tried a few times in windows 7 through rufus, now installing ubuntu on spare laptop.

---

### Post by C.S.Cameron on 2021-07-03
I wrote this a few days ago about Rufus ISO vs dd: [https://askubuntu.com/a/1348460/43926](https://askubuntu.com/a/1348460/43926)

---

### Post by VMC on 2021-07-04
```
sudo dd if=hybrid.iso of=/dev/sdX bs=8M
```
Change "sdX" to location of usb stick.
Change "hybrid.iso" to location and name of iso

---

### Post by m3t3ors on 2021-07-05
now solved
i used mx linux tool     
live usb maker tool

completed on first try

nice little tool

---

