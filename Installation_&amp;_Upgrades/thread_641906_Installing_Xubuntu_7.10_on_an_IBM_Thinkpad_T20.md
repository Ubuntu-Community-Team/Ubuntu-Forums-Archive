---
title: "Installing Xubuntu 7.10 on an IBM Thinkpad T20"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by PeterRJG on 2007-12-16
I'm getting 

[SIZE="1"]<some digits> BIOS age (1999) fails cutoff (2000) acpi=force is required to enable ACPI.[/SIZE]

when I try and boot to the Xubuntu 7.10 CD. It hangs at this point. Googling for help and the Thinkwiki site tell me to add "acpi=force" to the boot line. I've done that and it still gives me the same error message and locks up. In fact doing things like "apm=on" "pci=noacpi" etc, don't do anything either.

I'm not sure what to do - I've tried flashing the BIOS to the latest 2004 revision but it fails - it just won't flash it - at all (yes, enable flashing is turned on in the BIOS).

There doesn't seem to be an option to turn ACPI off in the BIOS, so I'm stuck.

---

### Post by jimrz on 2007-12-16
> **Peter1968 said:**
> I'm getting 

[SIZE="1"]<some digits> BIOS age (1999) fails cutoff (2000) acpi=force is required to enable ACPI.[/SIZE]

when I try and boot to the Xubuntu 7.10 CD. It hangs at this point. Googling for help and the Thinkwiki site tell me to add "acpi=force" to the boot line. I've done that and it still gives me the same error message and locks up. In fact doing things like "apm=on" "pci=noacpi" etc, don't do anything either.

I'm not sure what to do - I've tried flashing the BIOS to the latest 2004 revision but it fails - it just won't flash it - at all (yes, enable flashing is turned on in the BIOS).

There doesn't seem to be an option to turn ACPI off in the BIOS, so I'm stuck.

try
```
acpi=force pci=noacpi
```
this works nicely on my old TP 600x. On that one I need "pci=noacpi" for my pcmia cards to work once acpi is forced.

---

### Post by PeterRJG on 2007-12-16
> **jimrz said:**
> try
```
acpi=force pci=noacpi
```
this works nicely on my old TP 600x. On that one I need "pci=noacpi" for my pcmia cards to work once acpi is forced.

Yep, tried that one as well. Thing is though -once I reboot the installed system, I hit escape to bring Grub's menu up and I hit e to edit the line and append these instructions. I hit b to boot and it still locks up with that message I gave in my first post.

Is that how I'm supposed to be appending these switches or is there something I'm missing?

Edit: OK, I tried the recovery mode so I could see what was happening verbose. On all occasions, the loading hangs at this:

```
PCI: Found IRQ for device 0000:00:03.1
PCI: Sharing IRQ with 0000:00:03.0

```

If I try running the install for Mandrake 9.1, or running a live Open Suse KDE 4 CD, it locks up at the same place. So I'm guessing Linux as a whole isn't keen on how IRQ's are shared on this laptop...

---

### Post by fuseblower1123 on 2008-01-09
I use a IBM T20 with Ubuntu 7.10, and using APM rather than ACPI works like a charm. About every fourth try, the computer boots, and there may be problems with your sources list also.

---

