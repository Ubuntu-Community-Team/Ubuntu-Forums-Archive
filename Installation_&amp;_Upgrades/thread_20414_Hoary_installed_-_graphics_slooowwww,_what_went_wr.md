---
title: "Hoary installed - graphics slooowwww, what went wrong..."
date: 2005-03-16
forum: Installation &amp; Upgrades
---

### Post by total-noob on 2005-03-16
I just updated my Ubuntu box from Warty to Hoary Preview. Everything went fairly smooth and now my USB hotplug is working just the way it should   :) 

But there is something wrong. The system is quite slow - especially when it comes to graphics (screensavers go frame by frame)

Looking in my /var/log/syslog i find this:```
Mar 16 18:46:31 localhost kernel: ACPI: Looking for DSDT in initrd... not found!

...

Mar 16 18:46:31 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Mar 16 18:46:31 localhost kernel: pnp: PnP ACPI init
Mar 16 18:46:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\MCTH] (Node cf73ece0), AE_AML_BUFFER_LIMIT
Mar 16 18:46:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\OSFL] (Node cf73ed00), AE_AML_BUFFER_LIMIT
Mar 16 18:46:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_SB_.PCI0.SBRG.SYSR._CRS] (Node c123a5e0), AE_AML_BUFFER_LIMIT
Mar 16 18:46:31 localhost kernel:     ACPI-0158: *** Error: Method execution failed [\_SB_.PCI0.SBRG.SYSR._CRS] (Node c123a5e0), AE_AML_BUFFER_LIMIT
Mar 16 18:46:31 localhost kernel: pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0c02
Mar 16 18:46:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\MCTH] (Node cf73ece0), AE_AML_BUFFER_LIMIT
Mar 16 18:46:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\OSFL] (Node cf73ed00), AE_AML_BUFFER_LIMIT
Mar 16 18:46:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_SB_.SYSM._CRS] (Node c12385e0), AE_AML_BUFFER_LIMIT
Mar 16 18:46:31 localhost kernel:     ACPI-0158: *** Error: Method execution failed [\_SB_.SYSM._CRS] (Node c12385e0), AE_AML_BUFFER_LIMIT
Mar 16 18:46:31 localhost kernel: pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0c01
Mar 16 18:46:31 localhost kernel: pnp: PnP ACPI: found 11 devices
Mar 16 18:46:31 localhost kernel: PnPBIOS: Disabled by ACPI PNP
Mar 16 18:46:31 localhost kernel: PCI: Using ACPI for IRQ routing
Mar 16 18:46:31 localhost kernel: ** PCI interrupts are no longer routed automatically.  If this
Mar 16 18:46:31 localhost kernel: ** causes a device to stop working, it is probably because the
Mar 16 18:46:31 localhost kernel: ** driver failed to call pci_enable_device().  As a temporary
Mar 16 18:46:31 localhost kernel: ** workaround, the "pci=routeirq" argument restores the old
Mar 16 18:46:31 localhost kernel: ** behavior.  If this argument makes the device work again,
Mar 16 18:46:31 localhost kernel: ** please email the output of "lspci" to bjorn.helgaas@hp.com
Mar 16 18:46:31 localhost kernel: ** so I can fix the driver.
Mar 16 18:46:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\MCTH] (Node cf73ece0), AE_AML_BUFFER_LIMIT
Mar 16 18:46:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\OSFL] (Node cf73ed00), AE_AML_BUFFER_LIMIT
Mar 16 18:46:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_SB_.SYSM._CRS] (Node c12385e0), AE_AML_BUFFER_LIMIT
Mar 16 18:46:31 localhost kernel:     ACPI-0158: *** Error: Method execution failed [\_SB_.SYSM._CRS] (Node c12385e0), AE_AML_BUFFER_LIMIT
Mar 16 18:46:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\MCTH] (Node cf73ece0), AE_AML_BUFFER_LIMIT
Mar 16 18:46:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\OSFL] (Node cf73ed00), AE_AML_BUFFER_LIMIT
Mar 16 18:46:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_SB_.PCI0.SBRG.SYSR._CRS] (Node c123a5e0), AE_AML_BUFFER_LIMIT
Mar 16 18:46:31 localhost kernel:     ACPI-0158: *** Error: Method execution failed [\_SB_.PCI0.SBRG.SYSR._CRS] (Node c123a5e0), AE_AML_BUFFER_LIMIT
Mar 16 18:46:31 localhost kernel: pnp: 00:0a: ioport range 0x400-0x47f could not be reserved
Mar 16 18:46:31 localhost kernel: pnp: 00:0a: ioport range 0x680-0x6ff has been reserved
Mar 16 18:46:31 localhost kernel: pnp: 00:0a: ioport range 0x480-0x4bf has been reserved

...


Mar 16 18:46:31 localhost kernel: Evaluate _OSC Set fails. Status = 0x0005
Mar 16 18:46:31 localhost kernel: pciehp: add_host_bridge: status 5
Mar 16 18:46:31 localhost kernel: pciehp: Fails to gain control of native hot-plug
Mar 16 18:46:31 localhost kernel: hw_random hardware driver 1.0.0 loaded
Mar 16 18:46:31 localhost kernel: ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
Mar 16 18:46:31 localhost kernel: PCI: Setting latency timer of device 0000:00:1f.5 to 64
Mar 16 18:46:31 localhost kernel: intel8x0_measure_ac97_clock: measured 49525 usecs
Mar 16 18:46:31 localhost kernel: intel8x0: clocking to 48000
Mar 16 18:46:31 localhost kernel: e100: Intel(R) PRO/100 Network Driver, 3.2.3-k2-NAPI
```While booting, I noticed something failing with modprobe - i shall try to get that information as well and post it. (Can I find it in some log file?)

I am using kernel version 2.6.10-4-686. Any ideas on what I should do?

---

### Post by total-noob on 2005-03-16
Hmmm... I updated the kernel to version 2.6.10-5-686 and now the graphics feel much more responsive.

But I still have all these errors in my /var/log/syslog as mentioned above.

During the boot process I also see this:```
...
boot
Uncompressing Linux... Ok, booting the kernel.
pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0c02
pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0c01
...
```And later this:```
 *Starting hotplug subsystem...
modprobe: FATAL: Error inserting pciehp (/lib/modules/2.6.10-5-686/kernel/driver
s/pci/hotplug/pciehp.ko): No such device
                                                                         [ ok ]
```Ideas?

---

