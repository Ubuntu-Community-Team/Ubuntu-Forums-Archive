---
title: "Downloading an ubuntu image file using wget"
date: 2014-01-14
forum: Installation &amp; Upgrades
---

### Post by jhsjues on 2014-01-14
Hello, I am trying to get a fresh install image for ubuntu 13.10 & I would like to download it using wget in the terminal. Your help is appreciated.

---

### Post by arsenic23 on 2014-01-14
Just right click on the link, select 'Copy Link Address', then type 'wget ' into a terminal, paste the address and hit enter.

---

### Post by oldos2er on 2014-01-14
64-bit: ```
wget http://releases.ubuntu.com/saucy/ubuntu-13.10-desktop-amd64.iso
``` or 32-bit: ```
wget http://releases.ubuntu.com/saucy/ubuntu-13.10-desktop-i386.iso
```

---

### Post by jhsjues on 2014-01-15
Oldos2er, what is the potential easiest way to convert .iso files to .img files using the terminal?

---

### Post by Bucky Ball on 2014-01-15
The ISO is an image file.

[http://pcsupport.about.com/od/termsi/g/isofile.htm](http://pcsupport.about.com/od/termsi/g/isofile.htm)

---

### Post by jhsjues on 2014-01-15
I'm trying to make a usb bootable image. :) suggestions?

---

### Post by coffeecat on 2014-01-15
This wiki page is about installing Ubuntu from a bootable USB, but of necessity tells you how to make the bootable USB from the ISO in the first place: 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) 

There are several methods given for when using Ubuntu, and also how to make a bootable USB from MacOS and Windows.

---

