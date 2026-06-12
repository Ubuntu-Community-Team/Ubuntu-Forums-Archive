---
title: "power button shutdown?"
date: 2005-11-28
forum: Installation &amp; Upgrades
---

### Post by OmegaOne on 2005-11-28
im using ubuntu with a kde desktop, and for some reason the power button on the front of my case doesnt send the shutdown signal like it did with windows. is there a way to make it work like it did before in windows?

thanks

---

### Post by daller on 2005-12-01
[QUOTE=OmegaOne]im using ubuntu with a kde desktop, and for some reason the power button on the front of my case doesnt send the shutdown signal like it did with windows. is there a way to make it work like it did before in windows?

thanks[/QUOTE]

Do you have the "acpid" package installed?

---

### Post by OmegaOne on 2005-12-04
[QUOTE=daller]Do you have the "acpid" package installed?[/QUOTE]

sorry for being a bit slow here.

i just checked and yes i have it installed. do i need to configure it somehow or something?

thanks

---

### Post by az on 2005-12-04
Is it an older motherboard that does both APM and ACPI?  Because sometimes it will default to apm (The power button may still work with apm, though)  You can tell it to boot using acpi by appending

apci=force

at the boot prompt.

If you can, change the bios setting to ACPI instead of APM and ACPI, if that is the case.

---

