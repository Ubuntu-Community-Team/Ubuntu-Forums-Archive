---
title: "Bootable usb for 15.10 has invalid path argument and image"
date: 2015-10-29
forum: Installation &amp; Upgrades
---

### Post by Gafanhoto on 2015-10-29
I decided to update to Ubuntu 15.10 from 14.10. I tried upgrading through Package Manager which failed to install init and sysv and left me with a kernel panic screen everytime I start the notebook. So I decided to create a bootable usb using the official image to do a fresh install.
At work I'm running 14.10 too, so I used Startup Disk Creator to create the bootable usb, but now everytime I boot from it I get a message saying the path argument is invalid and that it cannot find a valid image.

Any clues?

---

### Post by howefield on 2015-10-29
Startup Disk creator has had some issues for some time.

I usually use dd to create startup media but perhaps [mkusb]("https://help.ubuntu.com/community/mkusb") would be a better (easier) way to make your bootable usb.

```
sudo add-apt-repository ppa:mkusb/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install mkusb
```

---

