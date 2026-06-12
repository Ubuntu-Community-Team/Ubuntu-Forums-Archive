---
title: "Can't create bootable usb on any linux."
date: 2015-02-18
forum: Installation &amp; Upgrades
---

### Post by Sekendiz on 2015-02-18
As a long time i'm trying a lot of distros. But every time i am getting same problem. the distros that i burned to usb with Unetbooting on Ubuntu or another linux distribution doesn't work. 
"this is not a bootable disk, insert a floppy and press enter"
To install a new system i have to find a Windows pc and use Universal Usb Installer. It works well. I don't know what can cause the problem. 
Same problem and same solution; windows:
[https://bbs.archlinux.org/viewtopic.php?id=181844](https://bbs.archlinux.org/viewtopic.php?id=181844)

---

### Post by sudodus on 2015-02-18
***Unetbootin*** works well for me most of the time. But there are several other tools that work in linux and in Windows. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

1. Check with ***md5sum*** that the download was good. Compare with [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2. Try [mkusb]("https://help.ubuntu.com/community/mkusb") in linux or [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") in Windows

---

### Post by Sekendiz on 2015-02-20
Thank you. Unetbooting and Yumi has problem but mkusb works well.

---

