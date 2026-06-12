---
title: "bootable usb"
date: 2012-08-31
forum: Installation &amp; Upgrades
---

### Post by 1Waffle on 2012-08-31
I want a bootable version of ubuntu 12.04 lts on my pendrive that works as if it was installed on the local hard drive and still has the install ubuntu option

---

### Post by mattpatey on 2012-08-31
If you have ubuntu already installed then you can use "Startup Disk Creator". You will need the ubuntu .iso or CD and a blank USB flash drive. It allows you to specify a persistance file to store settings between reboots.

If you are using Windows then I would recommend the Universal USB installer available from here:

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by 1Waffle on 2012-08-31
I used this but I download an app but when i restarted it it was gone
why is this

---

### Post by mattpatey on 2012-08-31
I didn't have to do anything extra to get it to remember settings and extra installed programs. Are you sure you selected the box labelled "Stored in reserved extra space" and the size of the persistence file? It should have created a persistence file on the usb drive named casper-rw.

If you want step-by-step guides there are plenty available on the net. For example:

[http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/#more-5191](http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/#more-5191)

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by oldfred on 2012-08-31
How large is USB flash? If smaller you want persistence, but that only allows saving your files not a full upgrade to Ubuntu. 

I have a full install on a 8GB partition on my 16GB flash and then use the other 8GB to store several ISO files and use grub2 to loopmount them. I then can use those ISO to install or as repair tools.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

