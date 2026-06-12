---
title: "Downloaded the Latest version of Ubuntu but Installation not working"
date: 2014-08-15
forum: Installation &amp; Upgrades
---

### Post by BioBeo_Inc. on 2014-08-15
Just downloaded the latest version of ubuntu from the official site. And extracted the ISO to the USB Drive but when I run the Wubi.exe it says me to reboot and when I reboot nothing happens. I want to dual boot with windows 7 64bit Ultimate and Ubuntu 14.4 64bit. Any help ?

---

### Post by ubfan1 on 2014-08-15
I don't think WUBI runs Ubuntu 14.04 -- you'll have to either run in a virtual machine like virtualbox, install to a USB, or make some room on your hard disk for the install.

---

### Post by ajgreeny on 2014-08-15
And you do not extract the iso to the USB to use it.  You have to make it into a bootable USB using something like unetbootin, available for both Linux and Windows.

This assumes that things are the same for wubi as for a real, partitioned installation, but I do not really know wubi, and in any case, as ubfan1 said, 14.04  with wubi is now not supported by canonical.

---

### Post by hakuna_matata on 2014-08-16
> **BioBeo_Inc. said:**
> but when I run the Wubi.exe it says me to reboot and when I reboot nothing happens.
If you run wubi.exe within desktop image, it says you to reboot because you should use desktop image for booting. This assumes that your desktop image is on a bootable DVD, USB, etc.

This function of wubi.exe has nothing to do with the install mode "Ubuntu within Windows". It is a default installation on real partitions.

---

### Post by QIII on 2014-08-16
Wubi does not install in proper separate partitions.  It creates a special directory in the Windows file heirarchy and sets up residence as a loop device.

Wubi is no longer maintained and the developers even recommend against its continued use.  It cannot be used at all with UEFI systems anyway.

---

