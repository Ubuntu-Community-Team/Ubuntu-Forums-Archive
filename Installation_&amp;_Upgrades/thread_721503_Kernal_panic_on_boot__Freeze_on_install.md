---
title: "Kernal panic on boot / Freeze on install"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by thefoo on 2008-03-11
Hello,

I seem to be having problems installing uBuntu (and any version of Linux...same basic problem) onto a desktop. For reference, the hardware is as follows:

Asus A78NX Motherboard
Corsair Valueselect PC3200 Memory (2x512mb in Dual Channel, 1x256mb)
WD 80gb ATA Hard Drives (x2)
Pioneer DVD Burner
ATI Radeon 9200 AGP Graphics Card
Edimax Wireless PCI Card

Now, the problem started with the secretary having blue screens in Windows XP. The system has been active for around three years and has worked flawlessly. I swapped systems to get her going again, and decided to install uBuntu...thinking it was some weird Windows XP problem.

First I've wiped all the drives using dBan, and I ran a complete Memtest which resulted in no errors whatsoever.

When I reach the boot menu and select the option to install, the Linux kernel loads and then I'm presented with:

[44.209308] PANIC: double fault, gdt at c1a09000 [255 bytes]
[44.209351] double fault, tss at c1a05000
[44.209388] eip = c013efeb, esp = fec80000
[44.209425] eax = 0000015a, ebx = ffbfae6d, ecx = c03dfef0, edx = 00000000
[44.209465] esi = c043ca00, edi = b828e228

And this is as far as things go. NOW, I've tried booting with the extra options of:

"noapic nolapic acpi=off"

To which I can then proceed to boot into gNome. From here, I get through the partitioner and installation options...and at around 40% or so on installation the system freezes.

I'm stumped. I've pulled, checked, switched, PCI cards, etc...memory swaps, drives. I get the same results no matter the changes.

Any ideas?

---

### Post by thefoo on 2008-03-13
*BUMP*

Anyone have any ideas?

---

### Post by Pumalite on 2008-03-13
Try the Alternate CD

---

