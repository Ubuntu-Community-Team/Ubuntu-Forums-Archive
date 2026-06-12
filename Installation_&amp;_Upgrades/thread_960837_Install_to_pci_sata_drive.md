---
title: "Install to pci sata drive"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by eddweed on 2008-10-27
Hi,
I've added a pci sata card to my pc but the card is a cheap one from ebay and i'm unable to boot from it after installation of mythbuntu to the sata drive. I've only space for the one hard drive so have also installed a compact flash to ide adapter and put a /boot partition on the 2gig card on the ide channell but it still won't boot. I think I need some sort of boot manager on the ide compact flash card which has support for the pci sata card that will allow me to boot from it. Is this possible?

Thanks for taking the time to read this

Alan Edwards

---

### Post by lemming465 on 2008-10-28
It's probably possible, but a lot depends on the motherboard BIOS, as that what has   to be used for the initial kernel load.  When you  say "put a /boot partition on the 2gig card" was that before or after the install?  Before is much easier.  There are ways of dealing with after if need be.  Could you provide a few more details about the install order?

---

### Post by eddweed on 2008-10-30
Thanks for the reply. The bios on the motherboard and firmware of the sata pci card wont allow boot from a sata drive so during installation I manually partioned a 2 gig compact flash card in an adapter on the ide channel and formatted in ext 3 with a mount point of /boot. I then placed the swap and / points onto the sata drive thinking the kernal on the ide drive would load drivers to work the sata drive ok to continue booting and use. 

Alan

---

### Post by lemming465 on 2008-10-30
Can you post the output from *sudo fdisk -l*.  Assuming the IDE flash is bootable, which ought to be the case (but might not be), a possible problem is that grub got installed to the sata drive rather than the IDE drive.

You might be able to do that directly from the install CD; otherwise if the IDE drive is mounted you can do it manually from a terminal window with something like```
sudo grub-install --root-directory=/media/sdb1 /dev/sdb
```
That assumed that the IDE drive identified as sdb and the partition mounted at /boot was the first one, and that you mounted it at /media/sdb1.

---

