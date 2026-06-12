---
title: "genisoimage to make live USB of installed linux?"
date: 2013-10-31
forum: Installation &amp; Upgrades
---

### Post by Coder88 on 2013-10-31
I have a working ubuntu (Ubuntu 12.04 LTS, but now customized with xfce desktop so in some ways it is 'xubuntu') installed on a separate drive my daily use linux; because my goal is to take a nicely set up working ubuntu with no personal files of my own, but with custom wallpaper, my choice of apps installed, etc, and then somehow put *that* on a USB thumbdrive as a live bootable linux. I have looked at live-linux.org and One Button Installer (OBI) but those look so complicated. I am wondering if I could use genisoimage
[http://www.debianadmin.com/genisoimage-creates-iso-9660-cd-rom-filesystem-images.html](http://www.debianadmin.com/genisoimage-creates-iso-9660-cd-rom-filesystem-images.html)
to create an .iso of customized working ubuntu linux (that I want to put on a thumbdrive and make bootable), and then use this method
[http://www.pendrivelinux.com/creating-an-xubuntu-live-usb-from-cd/](http://www.pendrivelinux.com/creating-an-xubuntu-live-usb-from-cd/)
to take that .iso and put it on the thumbdrive and make it bootable.

Can the genisoimage command take a working linux filesystem that consists of just a "/" partition and a swap partition and make that into an .iso that would copy to the thumbdrive included everything including /home and swap?

Thoughts?

---

