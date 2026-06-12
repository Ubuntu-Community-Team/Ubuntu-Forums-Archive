---
title: "Vista+Ubuntu on Ext Partn"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by bronzed.bison on 2010-10-24
Hi,

I have a Dell Inspiron Notebook (the usual 4 primary partitions were preinstalled). I knocked off the 4th MediaDirect partition and installed Ubuntu in an extended partition there (so now it's like [FONT="Courier New"]PrimPart1, PrimPart2, PrimVistaPart, ExtPart(UbuntuPart,Swap)[/FONT])

I installed grub in UbuntuPart. I wanted to avoid messing with the Vista bootloader, so I followed the instructions in the link below:

[_[COLOR="Blue"]Link to port25.technet.com article[/COLOR]_]("http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx")
(In short, made Vista's Bootloader point to grub.bin, which tells it how to boot into ubuntu)

Turns out that Ubuntu appears on the boot menu list, but fails to boot. I'm pretty sure this has something to do with UbuntuPart being in an extended partition, but I can't figure out what.

Does anyone know of a way around this? Or are extended partition boots hopeless thru the Vista bootloader?

Any help will be appreciated. Thanks.

---

### Post by arpanaut on 2010-10-24
First that article is from Oct. '06 I don't know if that is still valid since Grub has changed quite a lot since then.

Take a look here: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Seems to be a viable solution when one does not want to overwrite the mbr of windows with Grub.

I think that the issue here is that with Grub2 it does not like to be written to the "root" of a partition.
Hopefully Easy-BCD can be a viable solution for you.

---

### Post by bronzed.bison on 2010-10-29
Hi arpanaut,
Sorry for the delay. Thanks a lot for the EasyBCD tip: it worked!

---

