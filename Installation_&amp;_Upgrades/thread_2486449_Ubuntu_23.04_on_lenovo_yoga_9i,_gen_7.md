---
title: "Ubuntu 23.04 on lenovo yoga 9i, gen 7"
date: 2023-05-01
forum: Installation &amp; Upgrades
---

### Post by morgangdfp2 on 2023-05-01
Hi, 
I got hold of a Lenovo Yoga 9i, Gen 7 with a 12th Gen Intel® Core™ i7-1260P processor. Everything appears to be working fine but there are some errors during boot up and when checking the logs I find this many instances of something that appears to be related to BIOS:

```
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.TXHC.RHUB.SS01._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)

```

There are some other entries too, something about bluetooth.. But my bluetooth seems to be working, I have paired my logitech mouse and it works fine. 
Can someone help me figure out if I need to do something about these errors or warnings.. thanks. 


```
08:51:32 systemd: Failed to start app-gnome-snap\x2duserd\x2dautostart-2165.scope - Application launched by gnome-session-binary.
08:51:30 gdm-session-wor: gkr-pam: unable to locate daemon control file
08:51:19 kernel: Bluetooth: hci0: Malformed MSFT vendor event: 0x02
08:51:18 (uetoothd): src/plugin.c:plugin_init() Failed to init bap plugin
08:51:17 systemd-udevd: event_source: Failed to get device name: No such file or directory
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.SS04._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.SS03._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.SS02._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.SS01._PLD], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.SS01._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS10._PLD], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS10._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS09._PLD], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS09._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS08._PLD], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS08._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS07._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS06._PLD], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS06._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS05._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS04._PLD], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS04._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS03._PLD], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS03._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS02._PLD], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS02._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.XHCI.RHUB.HS01._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.TXHC.RHUB.SS04._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.TXHC.RHUB.SS03._PLD], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.TXHC.RHUB.SS03._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.TXHC.RHUB.SS02._PLD], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.TXHC.RHUB.SS02._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.TXHC.RHUB.SS01._PLD], AE_ALREADY_EXISTS (20221020/dswload2-326)
08:51:17 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
08:51:17 kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.TXHC.RHUB.SS01._UPC], AE_ALREADY_EXISTS (20221020/dswload2-326)
```

---

### Post by morgangdfp2 on 2023-05-03
Anyone?

---

### Post by pantazi on 2023-05-04
This may help:

[COLOR=#000000]https://linux.org/threads/acpi-error-after-installing-ubuntu-22-04.40993/[/COLOR]

---

