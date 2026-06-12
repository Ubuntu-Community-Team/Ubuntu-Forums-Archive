---
title: "Old computer, new install dapper, won't finish restarting"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by catnappist on 2007-10-15
I tried installing Feisty on my old Compaq Deskpro, it had issues with the old bios (it said so when booting up, but it booted anyway). Then it would freeze up when either rebooting or shutting down, to the point that I would have to unplug the computer. The monitor would shut down fine.

So I tried Dapper. I don't get the message about the bios, and I don't have to unplug it any more. But it still won't shut all the way down and it won't finish rebooting. It's not a big deal, since it also wants a sound card and I don't want to give it one (win98 works fine without one, and I've still got Feisty on my newer model). I'm just curious.

Thanks to anyone who might know. :-({|=

---

### Post by jimrz on 2007-10-15
> **catnappist said:**
> I tried installing Feisty on my old Compaq Deskpro, it had issues with the old bios (it said so when booting up, but it booted anyway). Then it would freeze up when either rebooting or shutting down, to the point that I would have to unplug the computer. The monitor would shut down fine.

So I tried Dapper. I don't get the message about the bios, and I don't have to unplug it any more. But it still won't shut all the way down and it won't finish rebooting. It's not a big deal, since it also wants a sound card and I don't want to give it one (win98 works fine without one, and I've still got Feisty on my newer model). I'm just curious.

Thanks to anyone who might know. :-({|=

what msg does it give you?
my old ThinkPad 600x gives me a msg that the BIOS miss the cutoff date (year 2000) and that acpi will not be applied. On mine adding 
```
acpi=force
```
as a kernel parameter fixes that issue for me. In addition, since it is a laptop, I have to also add 
```
pci=noacpi
```
in order for my pcmia cards (wifi or nic) to function.

---

### Post by catnappist on 2007-10-15
> **jimrz said:**
> what msg does it give you?
my old ThinkPad 600x gives me a msg that the BIOS miss the cutoff date (year 2000) and that acpi will not be applied. On mine adding 
```
acpi=force
```
as a kernel parameter fixes that issue for me. In addition, since it is a laptop, I have to also add 
```
pci=noacpi
```
in order for my pcmia cards (wifi or nic) to function.

Don't remember exact message, something about BIOS being out of date. When shutting down, it goes through the shut-down screen, the monitor blanks, shuts off, and the computer stays on.

---

### Post by catnappist on 2007-10-15
Mine's from 1998, and I don't know anything about the kernel. :confused:

---

