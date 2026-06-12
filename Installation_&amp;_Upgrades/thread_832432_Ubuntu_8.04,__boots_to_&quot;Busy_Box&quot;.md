---
title: "Ubuntu 8.04,  boots to &quot;Busy Box&quot;???"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by tenchidbz on 2008-06-17
Why cant I get to the GUI?  All other computers I boot the Live CD it works and goes into the Ubuntu GUI, but the computer it is ment for, only a CLI.   It gives me a "Busybox" Prompt.  Do I need to change anything in my BIOS? The computer has:

AMD Athlon64x2 4600+ Dule core CPU.
2.0 DDR2/800 ram
PCI ExpressX16, 256mb of GDDR3, ATI Raideon 9500 Pro
SATA Hard disk 256GB
SATA DVD+- RW

I had this working a year ago with Ubuntu 7.04, it booted to the GUI, but with the same version or the new one, it boots to the Busy Box command line.

---

### Post by Pumalite on 2008-06-17
You better install with the Alternate CD. If that fails, I'll give you some boot parameters to try.

---

### Post by underground on 2008-06-17
When at menu press F6 then add the following parameteres after --
all_generic_ide floppy=off irqpoll pci=nomsi

Then tell us if it boots.
I had the same problem as you and i solved it.

---

### Post by ak4322 on 2008-06-19
I have had this problem before, all i did was let the computer restart itself instead of pressing the button.

---

### Post by jrusso2 on 2008-06-19
This seems to be a common error message that doesn't really tell you what the problem is.

There are many threads about it and all you can do is see what others did to fix it.  I know some are hardware related and others are not.

---

