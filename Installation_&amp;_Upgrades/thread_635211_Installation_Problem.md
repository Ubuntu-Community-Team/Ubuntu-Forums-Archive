---
title: "Installation Problem"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by NewbieJD on 2007-12-08
Ok when i start installation, (Cd is fine memory check OK), Just after the orange bar dissapears i see a note saying that there is a problem with running in high resolution, When i try to change the settings to 1280x1024  or when i tried to run in low resolution a black screen with four lines show up each saying ok beside them, The installation dosent continue....any ideas, thanks!

---

### Post by Pumalite on 2007-12-08
Post your specs. You might need the Alternate CD.

---

### Post by NewbieJD on 2007-12-08
Custom Built:
XFX Geforce 7100GS
775 Intel celeron D 3.06GHZ
Hitachi Deskstar 250GB Serial ATA
MSI m-atx Motherboard
Acer Gamers line 2ms Crystalbrite monitor..

---

### Post by Pumalite on 2007-12-08
If you want to try some boot parameters first; here is a guide and a few you might try:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

---

### Post by NewbieJD on 2007-12-08
Belkin PCI wireless desktop Card
1gb Kensington Valueram

---

### Post by Pumalite on 2007-12-08
You have to be wired to the Internet during installation. You configure your wireless later.

---

### Post by NewbieJD on 2007-12-08
Right but it didnt consult me to connect to the internet

---

### Post by Pumalite on 2007-12-08
Make sure you are wired anyway.

---

### Post by NewbieJD on 2007-12-08
I just tried installing while wired, The exact same happened...

---

### Post by Pumalite on 2007-12-08
Start from scratch then. Do md5sum on iso before burn, burn at 4x in good quality CD-R media, check for CD integrity before installation, clean lens in your burner, try CD's in different computer, etc.

---

### Post by NewbieJD on 2007-12-08
Thankyou will try

---

