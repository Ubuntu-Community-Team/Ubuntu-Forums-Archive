---
title: "Possible to Write Ubuntu Boot Image to Disconnected Drive?"
date: 2013-04-21
forum: Installation &amp; Upgrades
---

### Post by libria on 2013-04-21
I have a Toshiba Portege 3505 which
[LIST]
[*]currently has no bootable OS
[*]has no CDROM drive built in
[*]does not have factory CDROM drive
[*]does not have a restore image on-drive
[*]cannot boot to USB stick or USB attached CDROM
[*]can PXE boot, but router does not support
[*]cannot boot Floppy
[*]has no data worth saving
[/LIST]

If I remove the hard drive and hose the entire partition, can I install a minimal Ubuntu image, reinstall the HD, boot it, connect to the internet to finish the install?

---

### Post by Cheesemill on 2013-04-21
If you have another machine to use then just plug the drive into that to do the full installation before putting the drive back in your laptop, there's no reason to do a minimal installation and then finish it off in the laptop.

To be on the safe side it's best to disconnect all other drives from the machine you will be installing with to make sure that the bootloader ends up on your laptop drive instead of one of the other machines drive(s).

---

### Post by sammiev on 2013-04-21
When I look up the specs it shows that this model has a  Optical Drive DVD-ROM - External . If this is the case then you can make a bootable DVD. ( even if you have to do it on another R/W DVD )

---

### Post by libria on 2013-04-23
> **Cheesemill said:**
> If you have another machine to use then just plug the drive into that to do the full installation before putting the drive back in your laptop, there's no reason to do a minimal installation and then finish it off in the laptop.

Thanks, I do have a desktop I can plug it into.  Will try this to get it started.

> **sammiev said:**
> When I look up the specs it shows that this model has a Optical Drive DVD-ROM - External.

It probably did originally; as stated, I do not have that.

---

