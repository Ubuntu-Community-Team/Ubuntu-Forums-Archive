---
title: "ACPI issues when installing"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by guy_smiley:) on 2010-05-13
Hardware: DFI Infinity RS482 M/B
AMD X2+ 3800+ CPU
2GB Memory DDR2
ATI Graphics Card
G15 and G5 Logitech Peripherals

When trying to install Lucid Lynx 64bit via USB (UNetbootin) or CDROM it has two issues. When ACPI is disabled in the BIOS, the installer will boot fine but I have no access to my keyboard or mouse. When ACPI is enabled in the BIOS, the installer won't start and stalls at child_rip+0x0/0x20.

Furthermore, enabling ACPI in the BIOS and trying "acpi=off noapic nolapic" to boot the installer only sees me lose access to my keyboard and mouse again.

Any ideas would be muchly appreciated.

---

### Post by halversondm on 2010-05-17
Similar issue here.  And we don't have the same hardware at all.

---

### Post by davidmohammed on 2010-05-17
have you tried booting with combinations of acpi=off, noapic and nolapic

e.g. I can boot with either noapic or nolapic.  If I boot with acpi=off noapic, then I get no fan control.

---

### Post by guy_smiley:) on 2010-05-17
> **davidmohammed said:**
> have you tried booting with combinations of acpi=off, noapic and nolapic

I think I originally managed to install it with acpi=off but then I couldn't edit grub so that when ubuntu started it had acpi=off since my keyboard and mouse wouldn't load :P

I went for 32bit as was suggested on Whirlpool forums, but now it seems one of my harddrives is failing. Great thing about Ubuntu... nice and easy to scan them and see which one it is!

---

