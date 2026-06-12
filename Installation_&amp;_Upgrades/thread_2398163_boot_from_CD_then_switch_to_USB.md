---
title: "boot from CD then switch to USB"
date: 2018-08-08
forum: Installation &amp; Upgrades
---

### Post by 3dgraphdav on 2018-08-08
Is there a way that I can boot up from a CD to a shell then tell it to boot from usb. These are old computers I'm installing to and they don't support boot from usb and and they don't have dvd drives.

---

### Post by Autodave on 2018-08-08
I can't answer your question, but have you thought of purchasing / borrowing an external DVD drive?  I have used mine many times on machines similar to yours. I know that you said that it won't boot from USB, but the external drive will usually be seen as a bootable device.

---

### Post by sudodus on 2018-08-08
Yes, you can use Plop, which installs USB drivers and after that chainloads to USB. See this link,

[help.ubuntu.com/community/Installation/FromUSBStick#PLoP_Boot_Manager](https://help.ubuntu.com/community/Installation/FromUSBStick#PLoP_Boot_Manager)

---

### Post by C.S.Cameron on 2018-08-09
+1 for plop. boot a USB from a CD or from a corner of your hard drive.

---

### Post by oldos2er on 2018-08-10
> **3dgraphdav said:**
> Is there a way that I can boot up from a CD to a shell then tell it to boot from usb. These are old computers I'm installing to and they don't support boot from usb and and they don't have dvd drives.

Not as far as I know. I don't think any *buntu images will fit on a CD either, with the possible exception of Ubuntu Server.

---

### Post by C.S.Cameron on 2018-08-10
Plop - [https://www.plop.at/en/bootmanagers.html](https://www.plop.at/en/bootmanagers.html)

Plop will allow booting of Live USB on a computer who's BIOS will not boot USB, Like on 10 or 15 year old computers.
No need to put the OS image on the CD, it is on the USB.

Edit:
As I recall plop works as well from a floppy as from a CD.

---

