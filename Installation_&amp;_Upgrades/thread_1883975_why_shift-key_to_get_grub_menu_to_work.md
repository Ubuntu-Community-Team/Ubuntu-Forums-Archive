---
title: "why shift-key to get grub menu to work?"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by deeppow on 2011-11-20
The grub menu does display fine after the boot process but the up-down arrows don't work (to change selection) unless I hold the shift-key down during to boot.  Is there a way to make the grub selectable available automatically with having to hold down the shift-key?

Thanks.

---

### Post by darkod on 2011-11-20
Do you have wireless or usb keyboard?

Sometimes you need to select options in BIOS to allow usb devices to work before the OS is loaded. Look for USB Legacy, or USB Keyboard.

---

### Post by deeppow on 2011-11-20
Yes, wireless.  I'll take a look in the bios.

Thanks.

---

### Post by darkod on 2011-11-20
Wireless is always tricky. In many cases until the OS loads with the driver it can't work.
Take a look at the USB options in BIOS since the wireless still has some sort of usb receiver, and if usb is disabled during boot, the signal from the keyboard has no way to be detected.

---

