---
title: "Install Crash to Built-in Shell (ash) on Sony Vaio PCG-Z505SX"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by michaelblaz on 2007-12-27
I've installed and enjoyed Ubuntu on my new Pavillion DV9030 without issue. I remembered that I had a slim-line laptop that was stashed away in my closet, a Sony Vaio PCG-Z505SX. Great machine, but only capable of running Windows ME at best. 

Downloaded newest release of Xubuntu, burnt to cd and booted... sequence followed:

Main Menu -> Selected Start or Install Xubuntu

then

"Loading Linux Kernel"

then (error i assume, screen text below)

(     0.000000) ACPI: no DMI bios year, acpi=force is required to enable ACPI

then

Xubuntu Loading Graphic

then (screen text below)

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_


attempts to start the install via the shell have been unsuccessful using my limited knowledge base? Any ideas?

---

### Post by Partyboi2 on 2007-12-27
See if  acpi=off works. To test it add "acpi=off" (without quotes)  to the boot options
At the main menu press F6 and at the end of the line add "acpi=off" (without quotes) then press enter.
Another thing to try, is updating your bios if you are able. If you know that your bios supports acpi then you could try using the acpi=force option instead of acpi=off
If adding acpi=off or acpi=force work then you will need to add it to grub menu, so that it works all the time.

---

### Post by michaelblaz on 2007-12-28
I attempted both courses of action:

acpi=off
this resulted in the installer asking for a driver cd, which I don't have or have an idea of what driver it's asking for.

acpi=force
this resulted in the same crash to Built-in shell problem as before. 

Any other thoughts?

---

### Post by michaelblaz on 2007-12-28
i forgot to mention...

The bios version is the most current that the manufacturer has out...

---

### Post by Partyboi2 on 2007-12-28
I suggest trying the alternate cd. Works better with older hardware :)
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

---

### Post by michaelblaz on 2007-12-28
I've attempted install with Ubuntu 7.1, same results across the board. I actually tried this install before I knew Xubuntu existed. Still no luck.

---

