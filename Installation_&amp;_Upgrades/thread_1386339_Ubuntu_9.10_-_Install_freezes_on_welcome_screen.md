---
title: "Ubuntu 9.10 - Install freezes on welcome screen"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by profdrsung on 2010-01-20
I tried to install ubuntu 9.10 with the live cd, but my computer freezes on the welcome screen, where you select the language (for the second time).

Here's what I do in detail:

Booting from the live CD (works fine)
Boot menu (works fine)
Selecting install ubuntu (no problem there)
After that the ubuntu logo starts pulsing and after a while the welcome screen appears. At this point, my mouse and keyboard are frozen (though the laser is still working) and the only way is to turn my computer off. I can't even eject the cd rom.

My system:
Intel Core 2 Quadcore Q8300
HD SATA II
Grafics Card: NVIDIA GeForce GT 220
Mainboard: D2950 (Chipset NVIDIA MCP73PV)

Can somebody please help me? 

Oh, and I already tried the obvious: Checked the CD...

---

### Post by kitserve on 2010-01-21
Try enabling some of the expert mode options, e.g. noapic, nolapic, acpi=off. They often enable you to get around this sort of problem.

---

### Post by caravanman on 2010-01-21
I have the same problem Tried all sorts Hope we can get it solved

---

### Post by profdrsung on 2010-01-22
OK, I got ubuntu to install by disabling apic (select "noapic" in the Live-CD bootloader.

But (and it's a big but) after installing I tried to boot from the harddisk and the system freezes on the splash screen. I tried adding "noapic" to the linux-line in grub, but that didn't solve the problem this time.

Any suggestions?

---

### Post by mtaylor925 on 2010-01-22
I'm having the same exact problem.  I can boot with acpi=off.  I've tried to edit grub to permanently boot with acpi=off but it doesn't save.  I'm not sure if this is because I'm editing with the live cd.  Basically the only way I can get in and have use of my keyboard, etc. is by selecting acpi=off in the boot options with the live cd, upon restart after the installation, I'm stuck.

---

### Post by cfjdoedens on 2010-01-24
I have the same problem.

Bought in the Computerland shop an ap fujitsu li-5300. Has as mainboard  d2950-a mcpp73/m-atx/vga.

Can install Ubuntu desktop 9.10 64 bit with noapic option. But after installation does not work.

---

### Post by kitserve on 2010-01-25
Can one of you post your grub configuration file? If you've edited it to include noapic then that option should persist across reboots, if I can see the file then I might be able to figure out if there's a problem there.

---

