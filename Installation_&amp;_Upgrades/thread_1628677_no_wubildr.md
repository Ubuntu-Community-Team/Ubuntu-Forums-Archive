---
title: "no wubildr"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by jtmedin on 2010-11-22
I had a large upgrade on my 10.04 & when i rebooted got 'no wubildr' & a repeat when it rebooted. Tried the copy of c:/ubuntu/winboot/wubildr to c:/wubildr from my windows 7 boot. Got the same thing :-(. Anyone got any other ideas? TIA

---

### Post by wilee-nilee on 2010-11-22
> **jtmedin said:**
> I had a large upgrade on my 10.04 & when i rebooted got 'no wubildr' & a repeat when it rebooted. Tried the copy of c:/ubuntu/winboot/wubildr to c:/wubildr from my windows 7 boot. Got the same thing :-(. Anyone got any other ideas? TIA

Did that upgrade include a grub update?

Do you have a install DVD or recovery cd for Windows 7? it is probably that you just need to reload the MS bootloader in the mbr.

Besides these questions if you can boot a Live Ubuntu cd and run the bootscript in my signature it would be helpful as well. If you post it click on the # in the reply panel for code tags paste the text in between.

---

### Post by jtmedin on 2010-11-23
Forgot to mention that i can boot to win7 no problem but when i select ubuntu i get the boot failure. Will see about doing the bootscript.

---

