---
title: "how to sd bios boot?"
date: 2017-04-22
forum: MINT
---

### Post by dojohn on 2017-04-22
Not sure where to go with this question, any help appreciated.

I would like to boot lubuntu and other linux distros from different sd cards. My usb ports became unreliable and damaged, so i need to get the sd card slot to be bootable.

The sd slot is not listed at boot in bios, sd slot booting not supported.

So i need to find a way to either

- update the oem bios to some other bios having the drivers for the sd slot. This would be my preference, if at all realistically achievable. Which bios will do this?

- use some boot manager loaded from internal disk with drivers for sd slot. i tried plopkexec iso and img burnt to usb stick. Bios sees sticks as uefi but boots to efi shell. i tried copying the iso and img and plopkexec file in / and /boot/ on internal disk. update-grub does not see them. Maybe another boot manager, but which?

or some other way ...

Can anyone help me achieve sd booting?


Bios is
    Vendor: American Megatrends Inc.
    Version: 1.00.01.MN x64
    Release Date: 06/23/2016
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 5120 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 5.11
    Firmware Revision: 1.1

SD slot is mmcblk0 and I think it sits on ISA or more probable PCI bus. Not sure which command to use to know exactly where it hardware sits.

---

### Post by howefield on 2017-04-23
Thread moved to the "*MINT*" forum.

---

