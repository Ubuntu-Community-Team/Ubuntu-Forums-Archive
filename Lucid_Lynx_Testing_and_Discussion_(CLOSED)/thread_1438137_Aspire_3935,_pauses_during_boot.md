---
title: "Aspire 3935, pauses during boot"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by keithy on 2010-03-24
Hello,

I hope someone can shed some light on this. I'm getting a reasonable boot time (I think!) but bootchart shows an eleven second pause before anything starts happening.

In reality, just after selecting Ubuntu in Grub, I get a flashing cursor at the top left hand side of the screen for 11 seconds

Any input appreciated

thanks

[[IMG]http://img695.imageshack.us/img695/6415/keithylaptoplucid201003.png[/IMG]](http://img695.imageshack.us/i/keithylaptoplucid201003.png/)

---

### Post by keithy on 2010-03-25
No ideas :(

this seems to be the pertinent part of DMESG which clearly shows an 8 second "pause", but its completely beyond me as to what (if anything) can be done.

would love some clues!

Thanks

[    2.622285] pci 0000:00:1c.4: bridge 64bit mmio pref:  
[0xf0000000-0xf1ffffff]
[    2.622377] pci 0000:00:1e.0: transparent bridge
[    2.622434] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.622702] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    2.622912] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    2.623041] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    2.623176] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    2.623314] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[   10.620581] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[   10.620780] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
[   10.620975] ACPI: PCI Interrupt Link [LNKC] (IRQs *10 11)
[   10.621169] ACPI: PCI Interrupt Link [LNKD] (IRQs *10 11)
[   10.621362] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 *11)
[   10.621555] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[   10.621747] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   10.621942] ACPI: PCI Interrupt Link [LNKH] (IRQs *10 11)
[   10.622145] vgaarb: device added:  
PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[   10.622172] vgaarb: loaded
[   10.622385] SCSI subsystem initialized
[   10.622505] libata version 3.00 loaded.
[   10.622636] usbcore: registered new interface driver usbfs
[   10.622658] usbcore: registered new interface driver hub
[   10.622703] usbcore: registered new device driver usb
[   10.623069] ACPI: WMI: Mapper loaded
[   10.623073] PCI: Using ACPI for IRQ routing

---

### Post by keithy on 2010-03-29
fixed by adding pci=noacpi in grub options

now have nice 20 second boot time.

not sure of the ramifications of having the pci=noacpi option enabled - any comments??

---

