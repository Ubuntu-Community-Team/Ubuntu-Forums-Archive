---
title: "Bugs? Or mistakes?"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by sirsquishy on 2007-03-25
When trying to DualBoot Linux, using the Ubuntu 6.06LTS Desktop Edition with the 64bit AMD and Intel Computers.

When I try to install I get this:

```
Decompressing Linux... Done
Booting the kernel
[ 30.855282].. MP-BIOS Bug: 8254 time not connected to IO-APC.

[ 31.035458] Kernel Panic - not syncing: IO-APC + timer doesn't work! Try using the "noapic" parameter.
```

Im using a HP Pavillion 7580n with 2GB ram, 300 some hardrive, 2.41ghz AMD Athlon 64X2 Dual Core Processor.

If you can find out what i did wrong, it would be greatly appreciated! 

Also: If you tell me what to do, could you use it in easy-to-understand language? Thanks

---

### Post by sirsquishy on 2007-03-25
BUMP

Don't forget about this thread! I need help please

---

### Post by Rui Pais on 2007-03-25
hi,
it suggests you, at error message, to use "noapic":

If you don't know how to do it:

boot
press 'E' key on keyboard when grub shows up
go to the line started with the word "kernel"
Press 'E' again.
Go to the end of the line and type **noapic **at the end of the line (with a space separating)
Press 'B'
(& cross your fingers)

hth

---

### Post by sirsquishy on 2007-03-25
[CENTER]Ubunto

[LOADiNG BAR GOES HERE]

Loading Essential Drives...   OK
Mounting Root File system...  [/CENTER]


--------------

Thats what its like now, it doesnt finish loading, i've left it on for a long time and the bar never moved, can someone help me

---

### Post by Rui Pais on 2007-03-25
well, that's another problem...

you could redo the above, adding the noapic option, but now deleting the word **quiet**
and **_before booting_**, select the line that contain only the word **quiet** alone, press 'D' (for delete it).

Press then 'B' and check error messages or any strange/warning output.

---

