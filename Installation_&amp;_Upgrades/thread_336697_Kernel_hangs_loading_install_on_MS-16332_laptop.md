---
title: "Kernel hangs loading install on MS-16332 laptop"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by Joe_CoT on 2007-01-11
These are the last lines I see from the kernel before it hangs:

```
PCI: Setting latency timer of device 0000:00:0b.0 to 64
ohci_hcd 0000:00:0b.0: OHCI Host Controller
ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
ohci_hcd 0000:00:0b.0: irq 217, io mem 0xfebbe000
libata version 1.20 loaded
ieee1394: Initialized config rom entry 'ip1394'

```

Any Idea what the problem is? Anything I can do to disable ieee1394 from loading? If I have usb legacy support enabled in the bios, it hangs even earlier than this. Any help is appreciated.

---

### Post by Joe_CoT on 2007-01-12
](*,)  I waited **forever** to post because I didn't want to post and be able to answer it myself .... for future reference, everything worked after adding:

```
acpi=off noapic nolapic
```

to the boot options

---

