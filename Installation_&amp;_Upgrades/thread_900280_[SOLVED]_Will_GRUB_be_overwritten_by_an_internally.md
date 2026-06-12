---
title: "[SOLVED] Will GRUB be overwritten by an internally installed, external hard disk driv"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by Berean on 2008-08-25
Hi,

I've got an ageing laptop that's on the way out.  To this end, I intend to remove the internal hard disk drive - which solely has Ubuntu as the OS - and install it in a casing.  This will make it a bootable external hard disk drive.  My worry is if I then boot from it using my wife's Vista will it overwrite her MBR?  To my mind it won't, but I need to be absolutely certain: My life would become unpleasant should I mess with her OS!  Thanks in advance for your help and advice.

---

### Post by bobbob1016 on 2008-08-25
I don't think it will overwrite your MBR.  However, I don't think it'll be bootable unless you play with it a bit.

---

### Post by gatenby_jp on 2008-08-25
If I understand ... you will be placing your existing disk in an external caddy and then plugging it into your wifes pc via usb and booting the usb disk. The external disk will simply run a separate system ... you will need to toggle the bios boot preferences in order to boot from either source. they would remain independent systems until you start mounting her filesytem.

---

### Post by Berean on 2008-08-25
> **gatenby_jp said:**
> If I understand ... you will be placing your existing disk in an external caddy and then plugging it into your wifes pc via usb and booting the usb disk. The external disk will simply run a separate system ... you will need to toggle the bios boot preferences in order to boot from either source. they would remain independent systems until you start mounting her filesytem.
Yes, that's exactly as I thought, but wanted to be sure.  Changing the BiOS preference is no problem, but I was concerned that I may have overwritten her MBR, to which I would have no idea how to correct.  Ubuntu is easy, Vista is not to reinstall GRUB.  Thanks to you both.

---

