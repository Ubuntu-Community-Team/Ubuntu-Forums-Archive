---
title: "Boot from USB not allowed by Grub???"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by ddales on 2009-11-29
I installed 9.10 on my Netbook an Acer Aspire One.  Now I want to re-install the original Windows that I have prepared on a USB Stick.  Only one problem, Grub will not allow booting from the USB.

Message:

Please remove all removable media and press any key to continue.

WTF?  I can only boot Ubuntu and it won't allow booting from USB.

---

### Post by jocko on 2009-11-29
> **ddales said:**
> Please remove all removable media and press any key to continue.
That message is from your bios, not grub. It tells you that the usb is not bootable.

---

### Post by mikeac72 on 2009-11-29
Did you create a bootable USB from Ubuntu?
[https://help.ubuntu.com/9.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/9.04/installation-guide/i386/boot-usb-files.html)
Just replace any Ubuntu stuff with Windows.

Press F2/del when booting. Go to boot. Select your USB drive. Press + as many times as you need to move it to the top of the list.
Try installing it now.

---

### Post by phillw on 2009-11-29
> **ddales said:**
> I installed 9.10 on my Netbook an Acer Aspire One.  Now I want to re-install the original Windows that I have prepared on a USB Stick.  Only one problem, Grub will not allow booting from the USB.

Message:

Please remove all removable media and press any key to continue.

WTF?  I can only boot Ubuntu and it won't allow booting from USB.

Making bootable usbs with any iso image on is covered here --> [http://www.pendrivelinux.com/boot-iso-from-usb-flash-drive/](http://www.pendrivelinux.com/boot-iso-from-usb-flash-drive/)

That site also covers dual booting usb drives and multi-boot usb drives.

Regards,

Phill.

---

