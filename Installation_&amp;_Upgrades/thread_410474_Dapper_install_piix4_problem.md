---
title: "Dapper install piix4 problem"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by BadPenny on 2007-04-15
I just installed Dapper on my mailserver, which was running Debian/etch. Unfortunately, etch was not supported, and the path of least resistance was to install Dapper rather than making the jump from 2.4.27 to 2.6.x to get NPTL support.

I am installing on a Penguin Computing Relion 120 with dual PIII/966 and 2GB of RAM. From lspci:

```

00:00.0 Host bridge: Broadcom CNB20HE Host Bridge (rev 23)
00:00.1 PCI bridge: Broadcom CNB20LE Host Bridge (rev 01)
00:00.2 Host bridge: Broadcom CNB20HE Host Bridge (rev 01)
00:00.3 Host bridge: Broadcom CNB20HE Host Bridge (rev 01)
00:04.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
00:05.0 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
00:05.1 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
00:06.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
00:0f.0 ISA bridge: Broadcom OSB4 South Bridge (rev 50)
00:0f.1 IDE interface: Broadcom OSB4 IDE Controller
00:0f.2 USB Controller: Broadcom OSB4/CSB5 OHCI USB Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage XL AGP 2X (rev 27)
02:01.0 RAID bus controller: American Megatrends Inc. MegaRAID (rev 02)
```

Install went fine, I used the server CD. However, the first boot after installation gave me the following error and went no further:

```

piix4_smbus 0000:00:0f:0: illegal interrupt configuration (or code out of date)!

```

Is there a workaround or fix for this?

Thanks,
--bp

---

