---
title: "Toshiba Satellite 1400-S151 ALI15x3"
date: 2014-05-21
forum: Installation &amp; Upgrades
---

### Post by Nopposan on 2014-05-21
Please help me get Lubuntu working on my friend's old laptop. He had XP on it and I told him XP needed to be replaced due to it no longer being supported with security updates. I've been struggling with getting Lubuntu working on this computer for quite awhile now. The upshot is that it won't start the GUI properly. Blank screen after booting. Initially did a Google search for the most obvious error messages that come up at boot time, "ALI15x3 not detected" and "ALI1535_smb can't enable device". What I found led me to try upgrading the BIOS to version 1.30, but that hasn't helped. 'Thought it might have something to do with enabling APIC in the BIOS but I actually don't see anything in the BIOS that looks like a good candidate for turning on/off APIC.

Signs and symptoms are that the system tries to boot, spits out a few messages about ALI15x3 and upgrading the BIOS or using force_addr=0xaddress, then goes to the Lubuntu splash, then the screen blanks out but stays powered on. On booting into rescue mode I cannot enable networking, even though it was enabled during installation.

FYI, I have installed Trusty version of Lubuntu 14.04 downloaded today and using the alternate CD with the "forcepae" boot option for the install disk. I tried before without using forcepae, but I got the same results. This machine does have a Celeron CPU, so forcing PAE seems like a good idea.

I'd love to give you the entire output of dmesg, but the rescue system seems to also fail to mount my USB memory stick, and so I haven't yet figured out how to save the output of dmesg to share with you. I decided to write down some of the lines from dmesg that seemed most interesting to me. Here they are. I won't pretend to understand what they all mean.

```

Notice: NX (Execute Disable) protection missing in CPU!

PAT not supported by CPU.

Using APIC driver default

Local APIC disabled by BIOS
APIC: disable apic facility
APIC: switched to apic NOOP

Booting paravirtualized Kernel on bare hardware

PAE forced!

smpboot: weird, boot CPU (#0) not listed by the BIOS
smpboot: SMP motherboard not detected

Local APIC not detected. Using dummy APIC emulation.

no APIC, boot with "lapic" boot parameter to force-enable it.

ACPI Exception: AE_NOT_FOUND, while evaluating Sleep State

acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM

acpi PNP0A03:00: fail to add MMCONFIG information, can't access extended PCI configuration space under this bridge.

address space collision: [io <"Sorry, I didn't bother writing down the numbers here">] conflicts with ACPI CPU throttle [??? . . . flags . . .]

system 00:00:[mem 0x. . .] could not be researved

BIOS EDD facility v.0.16 2004-Jun-25, 0 devices found
EDD information not available

pata_ali 0000:00:04.0 can't derive routing for PCI INT A

ata2.01: NODEV after polling detection

ata2.00: WARNING: ATAPI DMA disabled for reliability issues. It can't be enabled

ata2.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.

ali1535_smbus 0000:00:00.0: device not available (can't reserve [io 0xee0-0xee3f])

Detected unconfigured Toshiba laptop with ALi ISA bridge SMSC IrD A chip pre-configured device.


```

Please help me if you can. I really appreciate it.

---

