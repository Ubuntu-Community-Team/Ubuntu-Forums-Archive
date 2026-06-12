---
title: "Invalid PBLK lenght[5]"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by Kuraboy on 2006-10-28
Hi!

I have a P4 desktop PC, and when I upgraded from Dapper to Edgy I got this message before the splash screen:

```
[17179575.304000]ACPI: Invalid PBLK length[5]
```

I searched on the web but couldnt find a solution, only thing I could understand is that ACPI is for laptops?

I get this problem when I want to enter to the generic kernel, but when I enter 386 kernel version it works well.

Why did they take 686 away? Is generic same as 686? Thanx in advance

---

### Post by pugs on 2007-05-20
Did you ever find what was causing this?  I just installed 7.04 on an old HP desktop and am seeing the same error on bootup.

This is what I have from dmesg:


[   28.988006] ACPI: Transitioning device [FAN1] to D0
[   28.988014] ACPI: Transitioning device [FAN1] to D0
[   28.988019] ACPI: Fan [FAN1] (off)
[   28.996690] ACPI: Invalid PBLK length [5]
[   29.001023] ACPI: Thermal Zone [THRM] (-273 C)
[   30.141784] SCSI subsystem initialized
[   30.156632] libata version 2.20 loaded.
[   30.165377] ata_piix 0000:00:1f.1: version 2.10ac1
[   30.165433] PCI: Setting latency timer of device 0000:00:1f.1 to 64

---

