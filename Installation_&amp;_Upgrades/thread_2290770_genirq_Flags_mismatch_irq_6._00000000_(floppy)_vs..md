---
title: "genirq: Flags mismatch irq 6. 00000000 (floppy) vs. 00000080 (ohc i_hcd:us1)"
date: 2015-08-15
forum: Installation &amp; Upgrades
---

### Post by Daniyal_Javani on 2015-08-15
I try to installing lubuntu 14.10 on an old computer with gigabyte mother board. But i'm facing with this error:
```
genirq: Flags mismatch irq 6. 00000000 (floppy) vs. 00000080 (ohc i_hcd:us1)
...
(initramsf) Unable to find a medium cotaining a live file system
```

I read many topics about `Unable to find a medium cotaining a live file system` but seems they have not first line of my error!.
I try with DVD and with iso ('Help me to boot from CD' software for windows) both have same problem.

Seems it's a kernel problem, so is there any way to fix that?

---

### Post by mörgæs on 2015-08-15
14.10 is out of support. Better to install 15.04.

---

### Post by Daniyal_Javani on 2015-08-31
> **mörgæs said:**
> 14.10 is out of support. Better to install 15.04.

I try 15.04 but still have the same trouble. It seems Linux does not support my mother board:
Mother board details:
```

Brand: Gigabyte
P4 Titan series 333+
Dual bios
Model Name: GA-8SRX
Socket 478 FSB 400 CPU
3 DDR DIMMs / ATX Form Factor
Creative PCI 128 Sound
6 PCI / ATA100 / AGP4X
```

[https://wiki.ubuntu.com/HardwareSupportComponentsMotherboardsIntelSocket478Gigabyte](https://wiki.ubuntu.com/HardwareSupportComponentsMotherboardsIntelSocket478Gigabyte)

Is there any way to install Linux on the old PC?

---

### Post by mörgæs on 2015-08-31
Did you also try the [alternate Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") ISO?

---

### Post by ab612 on 2015-10-02
I have encountered similar IRQ conflicts on another platform with a floppy controller.  I found some helpful tips in the following forum:    1. Is the floppy _drive_ disabled (drive type set to 'none'), or the floppy _controller_ (in an 'on-board devices' menu)? [BIOS]    2. In any case, the BIOS performs initial assignment of IRQs, so this conflict is probably a BIOS bug. [you might try checking to see if a new BIOS version is available from Gigabyte]  Also try:   - Disable/enable the floppy controller in the BIOS (invert the current setting)  - Disable assignment of IRQ#6 by the BIOS, if possible (probably an option in a menu labeled 'Plug and Play' or similar)  - Add kernel parameter 'pci=usepirqmask' (but the bug this works around seems to be mostly found in laptops)  - Blacklist the floppy driver in terminal:     echo 'blacklist floppy' > /etc/modprobe.d/floppy-blacklist.conf    [http://www.eenyhelp.com/bug-780175-linux-image-3-16-0-4-686-pae-flags-mismatch-irq-6-00000080-sata-sil-vs-00000000-floppy-help-215606945.html#215606947](http://www.eenyhelp.com/bug-780175-linux-image-3-16-0-4-686-pae-flags-mismatch-irq-6-00000080-sata-sil-vs-00000000-floppy-help-215606945.html#215606947)    If nothing else works, maybe you can install GhostBSD or PC-BSD   (check if you need 32 or 64 bit version before downloading)    [https://en.wikipedia.org/wiki/Comparison_of_BSD_operating_systems](https://en.wikipedia.org/wiki/Comparison_of_BSD_operating_systems)

---

