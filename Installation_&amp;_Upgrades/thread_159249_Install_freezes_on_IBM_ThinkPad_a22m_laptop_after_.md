---
title: "Install freezes on IBM ThinkPad a22m laptop after &quot;noacpi&quot; option used..."
date: 2006-04-12
forum: Installation &amp; Upgrades
---

### Post by drudge on 2006-04-12
Install freezes on IBM ThinkPad a22m (P3-850MHz, 512MB RAM, 80GB HD) with the default install command and with the "linux pci=noacpi" option used to start install.

When I use "linux pci=noacpi" it gets passed the previous ACPI freeze but stops at a new line. The last few lines are:
[4294672.066000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.066000] PCI: found IRQ 11 for device 0000:00:03.1
[4294672.066000] PCI: Sharing IRQ 11 with 0000:0:03.0

This is where all activity on HD and CD freeze.

BONUS: Windows 98 is intalled first on HD and works. Windows 2000 is installed next on HD and working. Windows XP pro would not install (freezes up during hardware detection: RAM tested with memtst for 8hours 'no errors found'. HD is brand new came sealed not refurbished. Same exact Windows XP error occurs with different 20GB HD and with one of the two RAM chips installed in each different RAM slot).

Whats the next step?

---

### Post by drudge on 2006-04-18
So I guess "Ubuntu" can also mean "lack of support".

I notice most of yall check the easy threads and answer but the hard ones are plain skipped.

and people wonder why linux has little foot-hold in the desktop world. at least offer up some suggestings

---

### Post by asaturn on 2007-11-26
try the alternate CD - it's a text-based install and doesn't require the resources to run that the live CD requires.

---

