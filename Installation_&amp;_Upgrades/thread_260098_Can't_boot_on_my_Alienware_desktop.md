---
title: "Can't boot on my Alienware desktop"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by pickture on 2006-09-18
I've tried both 32 and 64 bit CDs and neither will boot. I used the same cd on my Dell laptop and it worked fine. It gets stuck at "Uncompressing Linux... Ok, booting the kernel." I've also tried Xubuntu and it does the same thing. Edgy Knot 3 gives me an error message:

[17179574.1640001] PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
[17179574.1640001] PCI: Not using MMCDNFIG.


Alienware ALX
AMD Athlon 64 FX-60

BIOS:
Manufacturer: American Megatrends Inc.
Name: BIOS Date: 12/22/05 11:27:11 Ver: 08.00.12
Version: 1101
Version: A M I - 12000522

---

### Post by zxee on 2006-09-18
You may need to use a boot option. Check out the installer options from the boot start menu. 
You could also download and try the alternate cd. [http://ubuntu.cs.utah.edu/releases/6.06/](http://ubuntu.cs.utah.edu/releases/6.06/)

---

### Post by pickture on 2006-09-22
I've tried "pci=noacpi" "acpi=off" and "nommconf" and none of them worked.

---

### Post by pickture on 2006-11-01
I was really hoping the final realease of Edgy would fix this problem so I could use Ubuntu on my Alienware, but no luck. There is no longer any error message, but it still gets stuck in the same place. The alternate install CD won't work either.

---

