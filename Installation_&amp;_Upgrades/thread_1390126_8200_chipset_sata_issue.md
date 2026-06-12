---
title: "8200 chipset sata issue"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by themoddingden on 2010-01-25
Hi;
Has anyone gotten around the can't see sata drive problem with the nvidia 8200 chipset?

this is on my main rig it's a XFX GeForce 8200 940 amd motherboard.
this is the model MI-A78S-8209.

Any help would be great.

---

### Post by emorak on 2010-03-16
Having the same issue here with the same board, it looks like the sata chipset is not detected, I have Ubuntu studio 9.10 installed.

sudo lshw -short
H/W path        Device     Class       Description
==================================================
                           system      To Be Filled By O.E.M.
/0                         bus         MI-A78S-8209
/0/0                       memory      64KiB BIOS
/0/3                       processor   AMD Phenom(tm) 9500 Quad-Core Processor
/0/3/5                     memory      512KiB L1 cache
/0/3/6                     memory      2MiB L2 cache
/0/3/7                     memory      2MiB L3 cache
/0/25                      memory      4GiB System Memory
/0/25/0                    memory      2GiB DIMM DDR2 Synchronous 400 MHz (2.5 ns)
/0/25/1                    memory      2GiB DIMM DDR2 Synchronous 400 MHz (2.5 ns)
/0/25/2                    memory      DIMM [empty]
/0/25/3                    memory      DIMM [empty]
/0/4                       memory      RAM memory
/0/1                       bridge      MCP78S [GeForce 8200] LPC Bridge
/0/1.1                     bus         MCP78S [GeForce 8200] SMBus
/0/1.2                     memory      RAM memory
/0/1.3                     processor   MCP78S [GeForce 8200] Co-Processor
/0/1.4                     memory      RAM memory
/0/2                       bus         MCP78S [GeForce 8200] OHCI USB 1.1 Controller
/0/2.1                     bus         MCP78S [GeForce 8200] EHCI USB 2.0 Controller
/0/5                       bus         MCP78S [GeForce 8200] OHCI USB 1.1 Controller
/0/4.1                     bus         MCP78S [GeForce 8200] EHCI USB 2.0 Controller
/0/6            scsi6      storage     MCP78S [GeForce 8200] IDE
/0/6/0.0.0      /dev/sda   disk        160GB WDC WD1600BB-56R
/0/6/0.0.0/1    /dev/sda1  volume      148GiB Windows NTFS volume
/0/6/0.1.0      /dev/sdb   disk        160GB WDC WD1600BB-56G
/0/6/0.1.0/1    /dev/sdb1  volume      142GiB EXT4 volume
/0/6/0.1.0/2    /dev/sdb2  volume      6236MiB Extended partition
/0/6/0.1.0/2/5  /dev/sdb5  volume      6236MiB Linux swap / Solaris partition
/0/7                       multimedia  MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
/0/8                       bridge      MCP78S [GeForce 8200] PCI Bridge
/0/8/8          wmaster0   network     Atheros AR5001X+ Wireless Network Adapter
/0/9                       storage     MCP78S [GeForce 8200] SATA Controller (non-AHCI mode)
/0/b                       bridge      MCP78S [GeForce 8200] PCI Express Bridge
/0/b/0                     display     C77 [GeForce 8200]
/0/10                      bridge      MCP78S [GeForce 8200] PCI Express Bridge
/0/12                      bridge      MCP78S [GeForce 8200] PCI Express Bridge
/0/13                      bridge      MCP78S [GeForce 8200] PCI Bridge
/0/13/0         eth0       network     88E8056 PCI-E Gigabit Ethernet Controller
/0/14                      bridge      MCP78S [GeForce 8200] PCI Bridge
/0/100                     bridge      K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
/0/101                     bridge      K10 [Opteron, Athlon64, Sempron] Address Map
/0/102                     bridge      K10 [Opteron, Athlon64, Sempron] DRAM Controller
/0/103                     bridge      K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
/0/104                     bridge      K10 [Opteron, Athlon64, Sempron] Link Control
/0/a            scsi8      storage     
/0/a/0.0.0      /dev/sdc   disk        1TB 10EACS External
/0/a/0.0.0/1    /dev/sdc1  volume      931GiB Windows NTFS volume

---

