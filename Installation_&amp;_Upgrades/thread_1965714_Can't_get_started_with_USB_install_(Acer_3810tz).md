---
title: "Can't get started with USB install (Acer 3810tz)"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by Tombuntu81 on 2012-04-26
Hello, I've posted elsewhere* but hope it's ok to start a fresh query here.. 

I simply can't seem boot from my bootable Ubuntu 11.10 USB stick. While it works fine on one PC (a Dell) on my Acer (which has no CD drive) I immediately get:

SYSLINUX 4.06 EDD 4.06-pre1 Copyright (C) 1994-2011 H. Peter Anvin et al

it seems to just hang on this page.

couple of notes:
notes:
The usb boots absolutely fine into Ubuntu on my dell Studio laptop
I have flashed the bios to the latest version (1.28 ) 
I have tried switching the SATA mode from AHCI to IDE mode, but see no change.
I've tried 32 and 62 bit versions with the same result

any tips on what I might change would be great
thanks

Tom

*I've posted also on an old Acer-specific thread, but this is perhaps a more general and possibly more simple issue - I'm not sure.

---

### Post by oldfred on 2012-04-26
There were some old bugs that I thought they had long ago fixed. Some then report that pendrive then works. Sometimes you just have to press enter.

Bugs in usb-creator unetbootin is an alternative if usb-create does not work
[https://bugs.launchpad.net/ubuntu/+source/usb-creator](https://bugs.launchpad.net/ubuntu/+source/usb-creator)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)


syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
in the directory from "isolinux.cfg" to "syslinux.cfg"
Try replacing the file vesamenu.c32 on the USB disk drive with that one "/usr/lib/syslinux/vesamenu.c32" of Ubuntu Maverick system or use UNetbootin than works fine.
[http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/)

---

### Post by Tombuntu81 on 2012-04-26
> **oldfred said:**
> There were some old bugs that I thought they had long ago fixed. Some then report that pendrive then works. Sometimes you just have to press enter.

Bugs in usb-creator unetbootin is an alternative if usb-create does not work
[https://bugs.launchpad.net/ubuntu/+source/usb-creator](https://bugs.launchpad.net/ubuntu/+source/usb-creator)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)


syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)

Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
in the directory from "isolinux.cfg" to "syslinux.cfg"
Try replacing the file vesamenu.c32 on the USB disk drive with that one "/usr/lib/syslinux/vesamenu.c32" of Ubuntu Maverick system or use UNetbootin than works fine.
[http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/)

Pressing enter doesn't seem to have done the trick but I'll try UNetbootin now. thanks for your links - plenty of possibilities there.

---

