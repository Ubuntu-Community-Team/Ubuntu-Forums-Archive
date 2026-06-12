---
title: "ps/2 keyboard problems"
date: 2004-12-13
forum: Installation &amp; Upgrades
---

### Post by shinzon on 2004-12-13
I'm trying to install ubuntu on an older compaq I have laying around, but I am having issues with getting the keyboard to work.

The keyboard is useable in the bios, during ubuntu installation (booting from CD), and using the ubuntu live cd; it only becomes inoperable once the hotplug subsystem is loaded.

I get two errors after the hotplug subsystem is loaded:
```

modprobe: FATAL: error inserting shpchp (/lib/modules.2.6.8.1-3-386/rs/pci/hotplug/pciehp.ko) Operation not permitted

modprobe: FATAL: error inserting pciehp (/lib/modules.2.6.8.1-3-386/rs/pci/hotplug/pciehp.ko) Operation not permitted
```

however, the FAQ explains that these errors are harmless.

I have tried booting into recovery mode and I have also tried swapping to a Microsoft wireless keyboard which uses the ps/2 port to connect with the same results. I don't currently have a USB keyboard to test.

Thanks in advance for any help.


Compaq Presario
AMD Duron 700mhz
576mb ram
via chipset
The keyboard is an old hewlett packard ps/2 multimedia keyboard.

---

