---
title: "ubuntu installation on sata"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by shivarider on 2008-06-26
hey,

i installed the ubuntu on a asus p5ad2-e deluxe motherboard with 1 ide hd and 1 sata. the installation was made on the sata hd.

the installation went well, but as soon as i try to boot off the hd rather than the cd, i get the folllowing message: "no hd detected"

what could the possible reasons for this behaviour be? is it the fact that i installed ubuntu on a sata drive and the os can't load its sata drivers?

thanks for your support

shivarider

---

### Post by logos34 on 2008-06-26
make sure the Bios hard disk detect settings are correct (they probably are since you could install)

Grub may have installed to the MBR of the IDE drive.  Change the hard disk boot order and see if that works.  If you manage to get the grub screen but it throws an error when trying to boot the ubuntu kernel, press 'e' on the selection, 'e' again to edit the 'root' line and change from (hd0,?) to (hd1,?) or vice-versa.  'enter' to save and 'b' to boot

---

### Post by shivarider on 2008-06-27
hi again.
il try a new isntallation with only the sata drive installed. the same problem :-( 
cant boot from the sata drive with a new ubuntu installation.
if there is only one drive installed the ubuntu setup shoud use the mbr of that drive!!

maybee you guys get some other ideas 

thanks 
shivarider

---

### Post by Bliepo32 on 2008-06-27
> **shivarider said:**
> hi again.
il try a new isntallation with only the sata drive installed. the same problem :-( 
cant boot from the sata drive with a new ubuntu installation.
if there is only one drive installed the ubuntu setup shoud use the mbr of that drive!!

maybee you guys get some other ideas 

thanks 
shivarider
Try and use the supergrub cd. Than choose Linux and MBR. Else you will need to modify your menu.lst. There are some great tutorials for doing that around the net. I have in fact looked up one for you: [http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)

---

