---
title: "USB installation"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by vnaveen on 2010-12-13
Hi ,

I have made 10.04LTS-64 bit server  USB installable using unetBoot.

During installation, I would get option of choosing Lang, Keyboard...etc, after that it looks for archive/internet for downloading the installation source.

How can make the installation source from USB.

Thanks
Naveen V

---

### Post by alexpolt on 2010-12-14
make sure you are back in main menu stuck on step "mount cdrom"

you should switch to console (ctrl-alt-f2) and mount your usb
as "/cdrom" (or, better, mount usb to some dir and then mount cdrom ISO copied on usb beforehand)

next return back to menu (ctrl-alt-f1) and proceed 

beaware of problems in ubuntu server 64 installation from usb ("failed to determine "cdrom/codename") and if it happens look for help in my other post

---

