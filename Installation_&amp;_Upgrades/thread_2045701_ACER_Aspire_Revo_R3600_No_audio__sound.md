---
title: "ACER Aspire Revo R3600 No audio / sound"
date: 2012-08-21
forum: Installation &amp; Upgrades
---

### Post by roadrash on 2012-08-21
I have just installed Ubuntu 12.04 on my Revo replacing a previous old version of linux mint. 
The problem I have is there is no longer any sound otherwise everything else is Ok. The sound setting only list a "dummy output". I have searched the forums but found nothing that gets it working for 12.04.
 I have posted some outputs of modules & harware etc to help diagnose it.
Please can someone help me to get this working.

**Output of lspci**
> 
00:00.0 Host bridge: NVIDIA Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: NVIDIA Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: NVIDIA Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: NVIDIA Corporation MCP79 Co-processor (rev b1)
00:04.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: NVIDIA Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: NVIDIA Corporation ION VGA (rev b1)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)


**output of lsmod**

> Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
vesafb                 13516  1 
arc4                   12473  2 
psmouse                72846  0 
nvidia              10962290  44 
ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
serio_raw              13027  0 
cfg80211              178679  3 ath5k,ath,mac80211
shpchp                 32325  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
wmi                    18744  0 
mac_hid                13077  0 
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
forcedeth              58096  0 

**output of lshw**

>     description: Desktop Computer
    product: Aspire R3600 (To Be Filled By O.E.M.)
    vendor: Acer
    serial: 92G1DYZUI0938015792700
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: administrator_password=disabled boot=normal chassis=desktop cpus=1 family=To Be Filled By O.E.M. frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=To Be Filled By O.E.M. uuid=00016C6C-C49D-2009-0913-161740000000
  *-core
       description: Motherboard
       product: FMCP7A-ION
       vendor: Acer
       physical id: 0
       serial: U00T093602874
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: R01-A2L
          date: 07/22/2009
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU  230   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: Intel
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
          configuration: cores=1 enabledcores=1 id=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 24KiB
             capacity: 24KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 0
             serial: FFFFFFFF
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-08-01 20:31+0000X-Generator: Launchpad (build 15719)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-08-01 20:31+0000X-Generator: Launchpad (build 15719) [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: DIMM2
     *-pci
          description: Host bridge
          product: MCP79 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: b1
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP79 LPC Bridge
             vendor: NVIDIA Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
             resources: ioport:4f00(size=256)
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP79 SMBus
             vendor: NVIDIA Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:10 ioport:4900(size=64) ioport:4d00(size=64) ioport:4e00(size=64)
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-processor
             description: Co-processor
             product: MCP79 Co-processor
             vendor: NVIDIA Corporation
             physical id: 3.5
             bus info: pci@0000:00:03.5
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=nvidia latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:fae80000-faefffff
        *-usb:0
             description: USB controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: NVIDIA Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:fae7f000-fae7ffff
        *-usb:1
             description: USB controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: NVIDIA Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:fae7ec00-fae7ecff
        *-pci:0
             description: PCI bridge
             product: MCP79 PCI Bridge
             vendor: NVIDIA Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-network
             description: Ethernet interface
             product: MCP79 Ethernet
             vendor: NVIDIA Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: b1
             serial: 00:01:6c:6c:c4:9d
             capacity: 1Gbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
             resources: irq:23 memory:fae7d000-fae7dfff ioport:d080(size=8) memory:fae7e800-fae7e8ff memory:fae7e400-fae7e40f
        *-storage
             description: SATA controller
             product: MCP79 AHCI Controller
             vendor: NVIDIA Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: scsi1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
             resources: irq:40 ioport:d000(size=8) ioport:cc00(size=4) ioport:c880(size=8) ioport:c800(size=4) ioport:c480(size=16) memory:fae7a000-fae7bfff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54321
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: FB2O
                serial: 090829FB2200VCGMMHXA
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=8aef827b
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: b332f500-fb36-4ebd-94bd-23c0ea41f05d
                   size: 12GiB
                   capacity: 12GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-08-21 20:08:48 filesystem=ext4 lastmountpoint=/ modified=2012-08-21 20:32:32 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-08-21 21:04:12 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 870cdde0-81fd-444a-b980-1301b8d6816b
                   size: 39GiB
                   capacity: 39GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-03-08 15:16:45 filesystem=ntfs label=Windows state=clean
              *-volume:2
                   description: Windows FAT volume
                   vendor: mkdosfs
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /media/Data
                   version: FAT32
                   serial: 4e2a-cfc2
                   size: 96GiB
                   capacity: 96GiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=Data mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
              *-volume:3
                   description: Linux swap volume
                   physical id: 4
                   bus info: scsi@1:0.0.0,4
                   logical name: /dev/sda4
                   version: 1
                   serial: 625c3afd-5ead-45b6-a11a-6957c979eb21
                   size: 1027MiB
                   capacity: 1027MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
        *-pci:1
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:23
        *-pci:2
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi normal_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:faf00000-fbffffff ioport:e0000000(size=436207616)
           *-display
                description: VGA compatible controller
                product: ION VGA
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: b1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:21 memory:fb000000-fbffffff memory:e0000000-efffffff memory:f8000000-f9ffffff ioport:ec00(size=128) memory:fafe0000-faffffff
        *-pci:3
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:22
        *-pci:4
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:21 memory:feb00000-febfffff
           *-network
                description: Wireless interface
                product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wlan0
                version: 01
                serial: 00:25:56:18:6e:c0
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=3.2.0-23-generic-pae firmware=N/A ip=10.0.0.9 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
                resources: irq:19 memory:febf0000-febfffff
        *-pci:5
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:20
        *-pci:6
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 18
             bus info: pci@0000:00:18.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:23


---

### Post by roadrash on 2012-08-22
Onboard Sound was turned off in bios

---

