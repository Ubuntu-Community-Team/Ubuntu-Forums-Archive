---
title: "cannot use cardreader"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phoogkamer on 2010-03-25
Using Lucid beta 1 with the latest patches and kernel I am not able to use my CB-712/4 Cardbus Controller.

Linux dikkiedik 2.6.32-17-generic #26-Ubuntu SMP Sat Mar 20 02:23:45 UTC 2010 x86_64 GNU/Linux

lspci | grep ENE
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

sudo lshw -short
[sudo] password for peter: 
H/W path               Device      Class       Description
==========================================================
                                   system      Aspire 5050
/0                                 bus         Prespa M
/0/0                               memory      107KiB BIOS
/0/4                               processor   AMD Turion(tm) 64 Mobile Technology MK-36
/0/4/5                             memory      512KiB L2 cache
/0/1b                              memory      1536MiB System Memory
/0/1b/0                            memory      512MiB DIMM DDR2 Synchronous
/0/1b/1                            memory      1GiB DIMM DDR2 Synchronous
/0/100                             bridge      RS480 Host Bridge
/0/100/1                           bridge      RS480 PCI Bridge
/0/100/1/5                         display     RS482 [Radeon Xpress 200M]
/0/100/4                           bridge      RS480 PCI Bridge
/0/100/5                           bridge      RS480 PCI Bridge
/0/100/6                           bridge      RS480 PCI Bridge
/0/100/7                           bridge      RS480 PCI Bridge
/0/100/12                          storage     IXP SB400 Serial ATA Controller
/0/100/13                          bus         IXP SB400 USB Host Controller
/0/100/13.1                        bus         IXP SB400 USB Host Controller
/0/100/13.2                        bus         IXP SB400 USB2 Host Controller
/0/100/14                          bus         IXP SB400 SMBus Controller
/0/100/14.1            scsi2       storage     IXP SB400 IDE Controller
/0/100/14.1/0.0.0      /dev/sda    disk        60GB Hitachi HTS54166
/0/100/14.1/0.0.0/1    /dev/sda1   volume      14GiB Windows NTFS volume
/0/100/14.1/0.0.0/2    /dev/sda2   volume      22GiB Windows NTFS volume
/0/100/14.1/0.0.0/3    /dev/sda3   volume      17GiB Extended partition
/0/100/14.1/0.0.0/3/5  /dev/sda5   volume      8871MiB Linux filesystem partition
/0/100/14.1/0.0.0/3/6  /dev/sda6   volume      9538MiB Linux filesystem partition
/0/100/14.1/0.0.0/4    /dev/sda4   volume      1153MiB Linux swap volume
/0/100/14.1/0.1.0      /dev/cdrom  disk        DVD-RAM UJ-850S
/0/100/14.2                        multimedia  IXP SB4x0 High Definition Audio Controller
/0/100/14.3                        bridge      IXP SB400 PCI-ISA Bridge
/0/100/14.4                        bridge      IXP SB400 PCI-PCI Bridge
/0/100/14.4/1                      bridge      CB-712/4 Cardbus Controller
/0/100/14.4/1.1                    memory      FLASH memory
/0/100/14.4/1.2                    generic     ENE PCI Secure Digital Card Reader Controller
/0/100/14.4/1.3                    memory      FLASH memory
/0/100/14.4/1.4                    memory      FLASH memory
/0/100/14.4/2          eth0        network     RTL-8139/8139C/8139C+
/0/100/14.4/4                      network     BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
/0/101                             bridge      K8 [Athlon64/Opteron] HyperTransport Technology Configuration
/0/102                             bridge      K8 [Athlon64/Opteron] Address Map
/0/103                             bridge      K8 [Athlon64/Opteron] DRAM Controller
/0/104                             bridge      K8 [Athlon64/Opteron] Miscellaneous Control
/1                     wlan0       network     Wireless interface

When I insert a card I cannot see any action. Even not in dmesg or /var/log/messages file.

Any suggestions or solutions?

---

