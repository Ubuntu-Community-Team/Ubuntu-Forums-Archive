---
title: "Encountered a section with no package"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by f.pier on 2012-05-01
I installed 12.04 (64) and I made alla updates, but unfortunately I have this problem after sudo apt-get update

```
pier@pier-desktop:~$ sudo apt-get update
Ign http://deb.opera.com stable InRelease                                      
Trovato http://packages.medibuntu.org precise InRelease                        
Scaricamento di:1 http://deb.opera.com stable Release.gpg [189 B]              
Trovato http://deb.opera.com stable Release                                    
Ign http://deb.opera.com stable Release                                        
Trovato http://packages.medibuntu.org precise/free amd64 Packages              
Ign http://dl.google.com stable InRelease                                      
Ign http://deb.opera.com stable/non-free amd64 Packages/DiffIndex              
Scaricamento di:2 http://dl.google.com stable Release.gpg [198 B]              
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://it.archive.ubuntu.com precise InRelease                             
Trovato http://packages.medibuntu.org precise/non-free amd64 Packages          
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex               
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Scaricamento di:3 http://dl.google.com stable Release [1338 B]                 
Ign http://it.archive.ubuntu.com precise-updates InRelease                     
Ign http://it.archive.ubuntu.com precise-backports InRelease                   
Ign http://security.ubuntu.com precise-security InRelease                      
Scaricamento di:4 http://extras.ubuntu.com precise Release.gpg [72 B]          
Scaricamento di:5 http://it.archive.ubuntu.com precise Release.gpg [198 B]     
Trovato http://packages.medibuntu.org precise/free i386 Packages               
Scaricamento di:6 http://it.archive.ubuntu.com precise-updates Release.gpg [198 B]
Scaricamento di:7 http://security.ubuntu.com precise-security Release.gpg [198 B]
Trovato http://extras.ubuntu.com precise Release                               
Err http://extras.ubuntu.com precise Release                                   
  
Trovato http://packages.medibuntu.org precise/non-free i386 Packages           
Scaricamento di:8 http://it.archive.ubuntu.com precise-backports Release.gpg [198 B]
Scaricamento di:9 http://it.archive.ubuntu.com precise Release [49,6 kB]       
Scaricamento di:10 http://security.ubuntu.com precise-security Release [49,6 kB]
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Scaricamento di:11 http://it.archive.ubuntu.com precise-updates Release [49,6 kB]
Scaricamento di:12 http://it.archive.ubuntu.com precise-backports Release [49,6 kB]
Scaricamento di:13 http://dl.google.com stable/main amd64 Packages [469 B]     
Scaricamento di:14 http://it.archive.ubuntu.com precise/main Sources [934 kB]  
Scaricamento di:15 http://dl.google.com stable/main i386 Packages [464 B]      
Trovato http://deb.opera.com stable/non-free amd64 Packages                    
Trovato http://deb.opera.com stable/non-free i386 Packages                     
Ign http://dl.google.com stable/main TranslationIndex                          
Scaricamento di:16 http://security.ubuntu.com precise-security/main Sources [2510 B]
Scaricamento di:17 http://security.ubuntu.com precise-security/restricted Sources [14 B]
Scaricamento di:18 http://security.ubuntu.com precise-security/universe Sources [2143 B]
Scaricamento di:19 http://security.ubuntu.com precise-security/multiverse Sources [14 B]
Scaricamento di:20 http://security.ubuntu.com precise-security/main amd64 Packages [14,9 kB]
Scaricamento di:21 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Ign http://deb.opera.com stable/non-free Translation-it_IT                     
Ign http://deb.opera.com stable/non-free Translation-it                        
Scaricamento di:22 http://security.ubuntu.com precise-security/universe amd64 Packages [3186 B]
Scaricamento di:23 http://security.ubuntu.com precise-security/multiverse amd64 Packages [14 B]
Scaricamento di:24 http://security.ubuntu.com precise-security/main i386 Packages [14,9 kB]
Scaricamento di:25 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Scaricamento di:26 http://security.ubuntu.com precise-security/universe i386 Packages [3190 B]
Ign http://deb.opera.com stable/non-free Translation-en                        
Scaricamento di:27 http://security.ubuntu.com precise-security/multiverse i386 Packages [14 B]
Scaricamento di:28 http://security.ubuntu.com precise-security/main TranslationIndex [72 B]
Scaricamento di:29 http://security.ubuntu.com precise-security/multiverse TranslationIndex [70 B]
Scaricamento di:30 http://security.ubuntu.com precise-security/restricted TranslationIndex [70 B]
Scaricamento di:31 http://security.ubuntu.com precise-security/universe TranslationIndex [72 B]
Scaricamento di:32 http://security.ubuntu.com precise-security/main Translation-en [5310 B]
Trovato http://security.ubuntu.com precise-security/multiverse Translation-en  
Trovato http://security.ubuntu.com precise-security/restricted Translation-en  
Ign http://dl.google.com stable/main Translation-it_IT                         
Ign http://dl.google.com stable/main Translation-it                            
Scaricamento di:33 http://security.ubuntu.com precise-security/universe Translation-en [1931 B]
Ign http://dl.google.com stable/main Translation-en                            
Scaricamento di:34 http://it.archive.ubuntu.com precise/restricted Sources [5470 B]
Scaricamento di:35 http://it.archive.ubuntu.com precise/universe Sources [5019 kB]
Ign http://packages.medibuntu.org precise/free Translation-it_IT               
Ign http://packages.medibuntu.org precise/free Translation-it                  
Ign http://packages.medibuntu.org precise/free Translation-en                  
Ign http://packages.medibuntu.org precise/non-free Translation-it_IT           
Ign http://packages.medibuntu.org precise/non-free Translation-it              
Ign http://packages.medibuntu.org precise/non-free Translation-en              
Scaricamento di:36 http://it.archive.ubuntu.com precise/multiverse Sources [155 kB]
Scaricamento di:37 http://it.archive.ubuntu.com precise/main amd64 Packages [1273 kB]
Scaricamento di:38 http://it.archive.ubuntu.com precise/restricted amd64 Packages [8452 B]
Scaricamento di:39 http://it.archive.ubuntu.com precise/universe amd64 Packages [4786 kB]
Scaricamento di:40 http://it.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB]
Scaricamento di:41 http://it.archive.ubuntu.com precise/main i386 Packages [1274 kB]
Scaricamento di:42 http://it.archive.ubuntu.com precise/restricted i386 Packages [8431 B]
Scaricamento di:43 http://it.archive.ubuntu.com precise/universe i386 Packages [4796 kB]
Scaricamento di:44 http://it.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]
Trovato http://it.archive.ubuntu.com precise/main TranslationIndex             
Trovato http://it.archive.ubuntu.com precise/multiverse TranslationIndex       
Trovato http://it.archive.ubuntu.com precise/restricted TranslationIndex       
Trovato http://it.archive.ubuntu.com precise/universe TranslationIndex         
Scaricamento di:45 http://it.archive.ubuntu.com precise-updates/main Sources [6917 B]
Scaricamento di:46 http://it.archive.ubuntu.com precise-updates/restricted Sources [765 B]
Scaricamento di:47 http://it.archive.ubuntu.com precise-updates/universe Sources [1032 B]
Scaricamento di:48 http://it.archive.ubuntu.com precise-updates/multiverse Sources [14 B]
Scaricamento di:49 http://it.archive.ubuntu.com precise-updates/main amd64 Packages [21,4 kB]
Scaricamento di:50 http://it.archive.ubuntu.com precise-updates/restricted amd64 Packages [757 B]
Scaricamento di:51 http://it.archive.ubuntu.com precise-updates/universe amd64 Packages [5577 B]
Scaricamento di:52 http://it.archive.ubuntu.com precise-updates/multiverse amd64 Packages [14 B]
Scaricamento di:53 http://it.archive.ubuntu.com precise-updates/main i386 Packages [22,7 kB]
Scaricamento di:54 http://it.archive.ubuntu.com precise-updates/restricted i386 Packages [770 B]
Scaricamento di:55 http://it.archive.ubuntu.com precise-updates/universe i386 Packages [5587 B]
Scaricamento di:56 http://it.archive.ubuntu.com precise-updates/multiverse i386 Packages [14 B]
Trovato http://it.archive.ubuntu.com precise-updates/main TranslationIndex     
Trovato http://it.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Trovato http://it.archive.ubuntu.com precise-updates/restricted TranslationIndex
Trovato http://it.archive.ubuntu.com precise-updates/universe TranslationIndex 
Scaricamento di:57 http://it.archive.ubuntu.com precise-backports/main Sources [700 B]
Scaricamento di:58 http://it.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Scaricamento di:59 http://it.archive.ubuntu.com precise-backports/universe Sources [14 B]
Scaricamento di:60 http://it.archive.ubuntu.com precise-backports/multiverse Sources [14 B]
Scaricamento di:61 http://it.archive.ubuntu.com precise-backports/main amd64 Packages [559 B]
Scaricamento di:62 http://it.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Scaricamento di:63 http://it.archive.ubuntu.com precise-backports/universe amd64 Packages [14 B]
Scaricamento di:64 http://it.archive.ubuntu.com precise-backports/multiverse amd64 Packages [14 B]
Scaricamento di:65 http://it.archive.ubuntu.com precise-backports/main i386 Packages [559 B]
Scaricamento di:66 http://it.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Scaricamento di:67 http://it.archive.ubuntu.com precise-backports/universe i386 Packages [14 B]
Scaricamento di:68 http://it.archive.ubuntu.com precise-backports/multiverse i386 Packages [14 B]
Trovato http://it.archive.ubuntu.com precise-backports/main TranslationIndex   
Trovato http://it.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Trovato http://it.archive.ubuntu.com precise-backports/restricted TranslationIndex
Trovato http://it.archive.ubuntu.com precise-backports/universe TranslationIndex
Trovato http://it.archive.ubuntu.com precise/main Translation-it               
Trovato http://it.archive.ubuntu.com precise/main Translation-en               
Trovato http://it.archive.ubuntu.com precise/multiverse Translation-it         
Trovato http://it.archive.ubuntu.com precise/multiverse Translation-en         
Trovato http://it.archive.ubuntu.com precise/restricted Translation-it         
Trovato http://it.archive.ubuntu.com precise/restricted Translation-en         
Trovato http://it.archive.ubuntu.com precise/universe Translation-it           
Trovato http://it.archive.ubuntu.com precise/universe Translation-en           
Trovato http://it.archive.ubuntu.com precise-updates/main Translation-en       
Trovato http://it.archive.ubuntu.com precise-updates/multiverse Translation-en 
Trovato http://it.archive.ubuntu.com precise-updates/restricted Translation-en 
Trovato http://it.archive.ubuntu.com precise-updates/universe Translation-en   
Trovato http://it.archive.ubuntu.com precise-backports/main Translation-en     
Trovato http://it.archive.ubuntu.com precise-backports/multiverse Translation-en
Trovato http://it.archive.ubuntu.com precise-backports/restricted Translation-en
Trovato http://it.archive.ubuntu.com precise-backports/universe Translation-en 
Recuperati 18,8 MB in 33s (558 kB/s)                                           
Lettura elenco dei pacchetti... Errore
W: Errore GPG: http://deb.opera.com stable Release: Le seguenti firme non erano valide: BADSIG AAFF4A5B336064B5 Opera Software Archive Automatic Signing Key 2012 <packager@opera.com>
W: Si è verificato un errore nel verificare la firma. Il repository non è aggiornato e verranno usati i file indice precedenti. Errore GPG: http://extras.ubuntu.com precise Release: Le seguenti firme non erano valide: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Impossibile recuperare http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Impossibile scaricare alcuni file di indice: saranno ignorati o verranno usati quelli vecchi.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
E: L'elenco dei pacchetti o il file di stato non può essere letto o aperto.
```



This is my sudo lshw

```
pier@pier-desktop:~$ sudo lshw
[sudo] password for pier: 
pier-desktop              
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=A0586422-329C-DD11-BB2A-002354BDD2CF
  *-core
       description: Motherboard
       product: P5KPL-SE
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: x.0x
       serial: MT708AK01617832
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0404
          date: 09/18/2008
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E8200  @ 2.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU E8200 @ 2.66GHz
          serial: To Be Filled By O.E.M.
          slot: Socket 775
          size: 1998MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 333MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: internal write-back instruction
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1,2 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM A1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1,2 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM B1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:fa000000-feafffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G86 [GeForce 8500 GT]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fd000000-fdffffff memory:e0000000-efffffff memory:fa000000-fbffffff ioport:dc00(size=128) memory:feae0000-feafffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:f9ffc000-f9ffffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:f4000000-f41fffff ioport:f4200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:e000(size=4096) memory:feb00000-febfffff ioport:f8f00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:23:54:bd:d2:cf
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:43 ioport:e800(size=256) memory:f8fff000-f8ffffff memory:f8fe0000-f8feffff memory:febf0000-febfffff
        *-usb:0
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:c480(size=32)
        *-usb:1
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c800(size=32)
        *-usb:2
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c880(size=32)
        *-usb:3
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:cc00(size=32)
        *-usb:4
             description: USB controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f9ffbc00-f9ffbfff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:c400(size=8) ioport:c080(size=4) ioport:c000(size=8) ioport:bc00(size=4) ioport:b880(size=16)
           *-disk
                description: ATA Disk
                product: MAXTOR STM332061
                vendor: Maxtor
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: MX15
                serial: 6SZ0EDTR
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000b01ac
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: eb9e94d3-1047-45e9-b09a-7781e81d7bf1
                   size: 294GiB
                   capacity: 294GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2012-04-25 14:07:06 filesystem=ext4 lastmountpoint=/ modified=2012-04-25 14:24:26 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-04-30 21:21:51 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 4095MiB
                   capacity: 4095MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 4095MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GH20NS15
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@2:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: IL00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
     *-scsi
          physical id: 1
          bus info: usb@1:5
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
pier@pier-desktop:~$ 
```

Can you help me, please?

---

