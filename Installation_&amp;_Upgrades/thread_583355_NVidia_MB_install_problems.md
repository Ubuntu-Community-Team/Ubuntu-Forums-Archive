---
title: "NVidia MB install problems"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by dcwest01 on 2007-10-20
I am trying to install vers 6 LTS on NVidia motherboard (EVGA nForce 680i SE SLI (TR Version)) purchased from Tiger Direct.

It is a Core 2 Duo MB with NVidia PCIe craphics card.

Is this hardware compatible with Ubuntu???

Thanks

---

### Post by ddrichardson on 2007-10-20
Run the Live CD and all will be revealed ;-)

---

### Post by dcwest01 on 2007-10-20
I've tried & it hangs with a timing error...

MP-BIOS bug: 8254 timer not connected to IO-APIC

Kernel panic - not synching: IO-APIC & timer doesn't work!

---

### Post by ddrichardson on 2007-10-20
Press F6 at the menu and add the following to the kernel then press enter:```
noapic
```

---

### Post by dcwest01 on 2007-10-20
There's already a lengthy string after the F6 option, Do I just add "noapic" to the end of it?

I tried that & still no luck.

---

### Post by ddrichardson on 2007-10-20
Yes just add it to the end, if it doesn't help try looking in the system BIOS and disabling IOAPIC. There is a more detailed thread [here.]("http://ubuntuforums.org/showthread.php?t=191355")

---

### Post by davantalus on 2007-10-20
As far as I can tell - You'll be much much better supported running Feisty.

---

### Post by dcwest01 on 2007-10-21
I finally got 7.10 working...

I tried "noapic" in boot with no success.  The process would continue a little further but still hang.  My CD burner was down on my Windows machine or I would have downloaded/tried 7.10 sooner.

I guess the support for later model CPU's is better in the later Ubuntu releases.

Thanks for all  your suggestions.

---

