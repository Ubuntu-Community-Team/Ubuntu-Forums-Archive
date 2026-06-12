---
title: "Which disks can be main boot disks?"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by starbase1 on 2010-03-31
I have/had a PC with several hard drives, and a mix of ubuntu and windows on multi boot.

The old boot drive died screaming, and I need to start again. (But my data is safe! yay!)

Is there anything special about which drive can be the main drive to start booting from? Or to put it another way, can I install to any of the other 3 and expect it to work, or do I need to switch them around so a different drive is on the connections for the recently dead one?

As ever, all clues gratefully received!
Nick

---

### Post by raymondh on 2010-03-31
Nick,

Assuming you were using GRUB as your bootloader and that GRUB was installed in the MBR of the HD that died ... 

You can change the order of the disks in BIOS. 

Just remember that GRUB has to be installed in the MBR of the HD that is set to boot first in BIOS.  After re-installing GRUB, you may have to update it to read the other OS.

Raymond

---

### Post by starbase1 on 2010-03-31
> **raymondh said:**
> Nick,

Assuming you were using GRUB as your bootloader and that GRUB was installed in the MBR of the HD that died ... 

You can change the order of the disks in BIOS. 

Just remember that GRUB has to be installed in the MBR of the HD that is set to boot first in BIOS.  After re-installing GRUB, you may have to update it to read the other OS.

Raymond

That makes sense to me - thanks for the instant answer, it's very much apprecuated!

---

