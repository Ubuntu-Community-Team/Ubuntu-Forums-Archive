---
title: "change bootloader from pendrivelinux universal usb installer"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by moin339 on 2013-11-17
Hi guys,

I have a lubuntu installation on a usb stick. I installed it with the universal usb installer ([http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)). Now I would like to change the bootloader to start automatically the live mode in german. How is that possible? 

Thanks for your help :)

---

### Post by Herman on 2013-11-19
Hello moin339,
I believe pendrivelinux live USBs use syslinux as the  boot loader. You will probably need to locate your syslinux.cfg file and  edit it according to the documentation for syslinux. Here's a link to  the syslinux wiki which should give you a few clues to begin with, [syslinux.org/wiki]("http://www.syslinux.org/wiki/index.php/SYSLINUX")

---

