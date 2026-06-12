---
title: "Boot only possible in recovery mode after upgrade to 9.10"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by Fly.By.Wire on 2010-01-19
Hi,
for the first time in 3 years I have a problem I cannot solve...
After upgrading to 9.10 Karmic Koala, my  Amilo Laptop (AMD64) refuses to boot.
I installed GRUB2 which works fine for my WinXP ... and Karmic will boot in recovery mode.

When trying a normal boot, I get a black screen. CRTL-ALT-F1 yields just a blinking cursor. The system will immediately reboot when pressing CRTL-ALT-Entf.

When booting in recovery mode, I choose "Resume normal boot" from the menu, log in while in cosole mode and enter "startx" ... and the grafic environtment works fine!

Why does the system work in recovery mode, but does not start with a normal boot?

Thanks in advance if anyone has an idea to indentify the problem...

Fly.By.Wire

Here's some information on my system:

cat /proc/version

Linux version 2.6.31-17-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009

lshw

mistral                                                                        
    description: Notebook                                                      
    product: Amilo A3667G Series                                               
    vendor: FUJITSU SIEMENS                                                    
    serial: 50C17DB2                                                           
    width: 64 bits                                                             
    capabilities: smbios-2.3 dmi-2.3 vsyscall64 vsyscall32                     
    configuration: boot=normal chassis=notebook uuid=F8E5BA9E-74FE-D511-8948-762E2CC0D0D1                                                                     
  *-core                                                                       
       description: Motherboard                                                
       product: P71CA                                                          
       physical id: 0                                                          
       serial: 00000000                                                        
     *-firmware                                                                
          description: BIOS                                                    
          vendor: American Megatrends Inc.                                     
          physical id: 0                                                       
          version: 1.06C (01/13/2006)                                          
          size: 64KiB                                                          
          capacity: 448KiB                                                     
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification                                                           
     *-cpu                                                                     
          description: CPU                                                     
          product: AMD Turion(tm) 64 Mobile Technology ML-37                   
          vendor: Advanced Micro Devices [AMD]                                 
          physical id: 4                                                       
          bus info: cpu@0                                                      
          version: AMD Turion(tm) 64 Mobile Technology ML-37                   
          serial: To Be Filled By O.E.M.                                       
          slot: CPU 1                                                          
          size: 800MHz                                                         
          capacity: 2GHz                                                       
          width: 64 bits                                                       
          clock: 200MHz                                                        
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up rep_good pni lahf_lm cpufreq                  
        *-cache:0                                                              
             description: L1 cache                                             
             physical id: 5                                                    
             slot: L1-Cache                                                    
             size: 64KiB                                                       
             capacity: 64KiB                                                   
             capabilities: pipeline-burst internal varies data                 
        *-cache:1                                                              
             description: L2 cache                                             
             physical id: 6                                                    
             slot: L2-Cache                                                    
             size: 1MiB                                                        
             capacity: 1MiB                                                    
             capabilities: pipeline-burst internal varies unified              
     *-memory                                                                  
          description: System Memory                                           
          physical id: 25                                                      
          slot: System board or motherboard                                    
          size: 1GiB                                                           
        *-bank:0                                                               
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)                
             product: PartNum0                                                 
             vendor: Manufacturer0                                             
             physical id: 0                                                    
             serial: SerNum0                                                   
             slot: DIMM0                                                       
             size: 512MiB                                                      
             width: 64 bits                                                    
             clock: 333MHz (3.0ns)                                             
        *-bank:1                                                               
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)                
             product: PartNum1                                                 
             vendor: Manufacturer1                                             
             physical id: 1                                                    
             serial: SerNum1                                                   
             slot: DIMM1                                                       
             size: 512MiB                                                      
             width: 64 bits                                                    
             clock: 333MHz (3.0ns)                                             
        *-bank:2                                                               
             description: DIMM [empty]                                         
             product: PartNum2                                                 
             vendor: Manufacturer2                                             
             physical id: 2                                                    
             serial: SerNum2                                                   
             slot: DIMM2                                                       
        *-bank:3                                                               
             description: DIMM [empty]                                         
             product: PartNum3                                                 
             vendor: Manufacturer3                                             
             physical id: 3                                                    
             serial: SerNum3                                                   
             slot: DIMM3                                                       
     *-pci:0                                                                   
          description: Host bridge                                             
          product: K8T890 Host Bridge                                          
          vendor: VIA Technologies, Inc.                                       
          physical id: 100                                                     
          bus info: pci@0000:00:00.0                                           
          version: 00                                                          
          width: 32 bits                                                       
          clock: 66MHz                                                         
          configuration: latency=8                                             
        *-generic UNCLAIMED                                                    
             description: PIC                                                  
             product: K8T890 I/O APIC Interrupt Controller                     
             vendor: VIA Technologies, Inc.                                    
             physical id: 0.5                                                  
             bus info: pci@0000:00:00.5                                        
             version: 00                                                       
             width: 32 bits                                                    
             clock: 33MHz                                                      
             capabilities: bus_master                                          
             configuration: latency=0                                          
        *-pci:0                                                                
             description: PCI bridge                                           
             product: [K8T890 North / VT8237 South] PCI Bridge                 
             vendor: VIA Technologies, Inc.                                    
             physical id: 1                                                    
             bus info: pci@0000:00:01.0                                        
             version: 00                                                       
             width: 32 bits                                                    
             clock: 66MHz                                                      
             capabilities: pci pm bus_master cap_list                          
        *-pci:1                                                                
             description: PCI bridge                                           
             product: K8T890 PCI to PCI Bridge Controller                      
             vendor: VIA Technologies, Inc.                                    
             physical id: 2                                                    
             bus info: pci@0000:00:02.0                                        
             version: 00                                                       
             width: 32 bits                                                    
             clock: 33MHz                                                      
             capabilities: pci pciexpress pm msi bus_master cap_list           
             configuration: driver=pcieport-driver                             
             resources: irq:48 ioport:9000(size=12288) memory:fea00000-feafffff memory:aff00000-bfefffff(prefetchable)                                        
           *-display UNCLAIMED                                                 
                description: VGA compatible controller                         
                product: Radeon Mobility X700 (PCIE)                           
                vendor: ATI Technologies Inc                                   
                physical id: 0                                                 
                bus info: pci@0000:02:00.0                                     
                version: 00                                                    
                width: 64 bits                                                 
                clock: 33MHz                                                   
                capabilities: pm pciexpress msi bus_master cap_list            
                configuration: latency=0                                       
                resources: memory:b0000000-b7ffffff(prefetchable) memory:feaf0000-feafffff ioport:b000(size=256) memory:feac0000-feadffff(prefetchable)       
        *-pci:2                                                                
             description: PCI bridge                                           
             product: K8T890 PCI to PCI Bridge Controller                      
             vendor: VIA Technologies, Inc.                                    
             physical id: 3                                                    
             bus info: pci@0000:00:03.0                                        
             version: 00                                                       
             width: 32 bits                                                    
             clock: 33MHz                                                      
             capabilities: pci pciexpress pm msi bus_master cap_list           
             configuration: driver=pcieport-driver                             
             resources: irq:49                                                 
        *-pci:3                                                                
             description: PCI bridge                                           
             product: K8T890 PCI to PCI Bridge Controller                      
             vendor: VIA Technologies, Inc.                                    
             physical id: 3.2                                                  
             bus info: pci@0000:00:03.2                                        
             version: 00                                                       
             width: 32 bits                                                    
             clock: 33MHz                                                      
             capabilities: pci pciexpress pm msi bus_master cap_list           
             configuration: driver=pcieport-driver                             
             resources: irq:50                                                 
        *-firewire                                                             
             description: FireWire (IEEE 1394)                                 
             product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)        
             vendor: Texas Instruments                                         
             physical id: 8                                                    
             bus info: pci@0000:00:08.0                                        
             version: 00                                                       
             width: 32 bits                                                    
             clock: 33MHz                                                      
             capabilities: pm bus_master cap_list                              
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=3   
             resources: irq:16 memory:febff800-febfffff memory:febf8000-febfbfff                                                                              
        *-network:0                                                            
             description: Ethernet interface                                   
             product: RTL-8169 Gigabit Ethernet                                
             vendor: Realtek Semiconductor Co., Ltd.                           
             physical id: 9                                                    
             bus info: pci@0000:00:09.0                                        
             logical name: eth0                                                
             version: 10                                                       
             serial: 00:03:0d:42:9c:80                                         
             size: 10MB/s                                                      
             capacity: 1GB/s                                                   
             width: 32 bits                                                    
             clock: 66MHz                                                      
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation                   
             configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s                                                
             resources: irq:17 ioport:e800(size=256) memory:febff400-febff4ff memory:febc0000-febdffff(prefetchable)                                          
        *-network:1                                                            
             description: Network controller                                   
             product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller                                                                              
             vendor: Broadcom Corporation                                      
             physical id: a                                                    
             bus info: pci@0000:00:0a.0                                        
             version: 02                                                       
             width: 32 bits                                                    
             clock: 33MHz                                                      
             capabilities: bus_master                                          
             configuration: driver=b43-pci-bridge latency=64                   
             resources: irq:18 memory:febfc000-febfdfff                        
        *-ide:0                                                                
             description: IDE interface                                        
             product: VIA VT6420 SATA RAID Controller                          
             vendor: VIA Technologies, Inc.                                    
             physical id: f                                                    
             bus info: pci@0000:00:0f.0                                        
             version: 80                                                       
             width: 32 bits                                                    
             clock: 33MHz                                                      
             capabilities: ide pm bus_master cap_list                          
             configuration: driver=sata_via latency=64                         
             resources: irq:20 ioport:ec00(size=8) ioport:e480(size=4) ioport:e400(size=8) ioport:e080(size=4) ioport:e000(size=16) ioport:d800(size=256)     
        *-ide:1                                                                
             description: IDE interface                                        
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE  
             vendor: VIA Technologies, Inc.                                    
             physical id: f.1                                                  
             bus info: pci@0000:00:0f.1                                        
             logical name: scsi0                                               
             logical name: scsi1                                               
             version: 06                                                       
             width: 32 bits                                                    
             clock: 33MHz                                                      
             capabilities: ide pm bus_master cap_list emulated                 
             configuration: driver=pata_via latency=32                         
             resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)                                               
           *-disk                                                              
                description: ATA Disk                                          
                product: ST9100825A                                            
                vendor: Seagate                                                
                physical id: 0                                                 
                bus info: scsi@0:0.0.0                                         
                logical name: /dev/sda                                         
                version: 3.04                                                  
                serial: 5PL0GR93                                               
                size: 93GiB (100GB)                                            
                capabilities: partitioned partitioned:dos                      
                configuration: ansiversion=5 signature=7e6e45bd                
              *-volume:0                                                       
                   description: Windows NTFS volume                            
                   physical id: 1                                              
                   bus info: scsi@0:0.0.0,1                                    
                   logical name: /dev/sda1                                     
                   logical name: /media/hda1                                   
                   version: 3.1                                                
                   serial: 36e1b874-3acb-9c4e-8e0c-9d28507e3136                
                   size: 36GiB                                                 
                   capacity: 36GiB                                             
                   capabilities: primary bootable ntfs initialized             
                   configuration: clustersize=4096 created=2006-08-04 21:35:15 filesystem=ntfs modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true                                                                          
              *-volume:1                                                       
                   description: Extended partition                             
                   physical id: 2                                              
                   bus info: scsi@0:0.0.0,2                                    
                   logical name: /dev/sda2                                     
                   size: 56GiB                                                 
                   capacity: 56GiB                                             
                   capabilities: primary extended partitioned partitioned:extended                                                                            
                 *-logicalvolume:0                                             
                      description: Linux swap / Solaris partition              
                      physical id: 5                                           
                      logical name: /dev/sda5                                  
                      capacity: 1553MiB                                        
                      capabilities: nofs                                       
                 *-logicalvolume:1                                             
                      description: Linux filesystem partition                  
                      physical id: 6                                           
                      logical name: /dev/sda6                                  
                      logical name: /                                          
                      capacity: 15GiB                                          
                      configuration: mount.fstype=reiserfs mount.options=rw,relatime,notail state=mounted                                                     
                 *-logicalvolume:2                                             
                      description: Linux filesystem partition                  
                      physical id: 7                                           
                      logical name: /dev/sda7                                  
                      logical name: /home                                      
                      capacity: 39GiB                                          
                      configuration: mount.fstype=reiserfs mount.options=rw,relatime state=mounted                                                            
           *-cdrom                                                             
                description: DVD writer                                        
                product: DVD-RW GWA-4082N                                      
                vendor: HL-DT-ST                                               
                physical id: 1                                                 
                bus info: scsi@1:0.0.0                                         
                logical name: /dev/cdrom1                                      
                logical name: /dev/cdrw1                                       
                logical name: /dev/dvd1                                        
                logical name: /dev/dvdrw1                                      
                logical name: /dev/scd0                                        
                logical name: /dev/sr0                                         
                version: CW02                                                  
                capabilities: removable audio cd-r cd-rw dvd dvd-r             
                configuration: ansiversion=5 status=nodisc                     
        *-usb:0                                                                
             description: USB Controller                                       
             product: VT82xxxxx UHCI USB 1.1 Controller                        
             vendor: VIA Technologies, Inc.                                    
             physical id: 10                                                   
             bus info: pci@0000:00:10.0                                        
             version: 81                                                       
             width: 32 bits                                                    
             clock: 33MHz                                                      
             capabilities: pm bus_master cap_list                              
             configuration: driver=uhci_hcd latency=64                         
             resources: irq:21 ioport:dc00(size=32)                            
        *-usb:1                                                                
             description: USB Controller                                       
             product: VT82xxxxx UHCI USB 1.1 Controller                        
             vendor: VIA Technologies, Inc.                                    
             physical id: 10.1                                                 
             bus info: pci@0000:00:10.1                                        
             version: 81                                                       
             width: 32 bits                                                    
             clock: 33MHz                                                      
             capabilities: pm bus_master cap_list                              
             configuration: driver=uhci_hcd latency=64                         
             resources: irq:21 ioport:d480(size=32)                            
        *-usb:2                                                                
             description: USB Controller                                       
             product: VT82xxxxx UHCI USB 1.1 Controller                        
             vendor: VIA Technologies, Inc.                                    
             physical id: 10.2                                                 
             bus info: pci@0000:00:10.2                                        
             version: 81                                                       
             width: 32 bits                                                    
             clock: 33MHz                                                      
             capabilities: pm bus_master cap_list                              
             configuration: driver=uhci_hcd latency=64                         
             resources: irq:21 ioport:d400(size=32)                            
        *-usb:3                                                                
             description: USB Controller                                       
             product: VT82xxxxx UHCI USB 1.1 Controller                        
             vendor: VIA Technologies, Inc.                                    
             physical id: 10.3                                                 
             bus info: pci@0000:00:10.3                                        
             version: 81                                                       
             width: 32 bits                                                    
             clock: 33MHz                                                      
             capabilities: pm bus_master cap_list                              
             configuration: driver=uhci_hcd latency=64                         
             resources: irq:21 ioport:d080(size=32)                            
        *-usb:4                                                                
             description: USB Controller                                       
             product: USB 2.0                                                  
             vendor: VIA Technologies, Inc.                                    
             physical id: 10.4                                                 
             bus info: pci@0000:00:10.4                                        
             version: 86                                                       
             width: 32 bits                                                    
             clock: 33MHz                                                      
             capabilities: pm bus_master cap_list                              
             configuration: driver=ehci_hcd latency=64                         
             resources: irq:21 memory:febff000-febff0ff                        
        *-isa                                                                  
             description: ISA bridge                                           
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]            
             vendor: VIA Technologies, Inc.                                    
             physical id: 11                                                   
             bus info: pci@0000:00:11.0                                        
             version: 00                                                       
             width: 32 bits                                                    
             clock: 33MHz                                                      
             capabilities: isa pm bus_master cap_list                          
             configuration: latency=0                                          
        *-multimedia                                                           
             description: Multimedia audio controller                          
             product: VT8233/A/8235/8237 AC97 Audio Controller                 
             vendor: VIA Technologies, Inc.                                    
             physical id: 11.5                                                 
             bus info: pci@0000:00:11.5                                        
             version: 60                                                       
             width: 32 bits                                                    
             clock: 33MHz                                                      
             capabilities: pm cap_list                                         
             configuration: driver=VIA 82xx Audio latency=0                    
             resources: irq:22 ioport:c800(size=256)                           
        *-communication                                                        
             description: Communication controller                             
             product: AC'97 Modem Controller                                   
             vendor: VIA Technologies, Inc.                                    
             physical id: 11.6                                                 
             bus info: pci@0000:00:11.6                                        
             version: 80                                                       
             width: 32 bits                                                    
             clock: 33MHz                                                      
             capabilities: pm cap_list                                         
             configuration: driver=VIA 82xx Modem latency=0                    
             resources: irq:22 ioport:c400(size=256)                           
     *-pci:1                                                                   
          description: Host bridge                                             
          product: K8T890 Host Bridge                                          
          vendor: VIA Technologies, Inc.                                       
          physical id: 101                                                     
          bus info: pci@0000:00:00.1                                           
          version: 00                                                          
          width: 32 bits                                                       
          clock: 33MHz                                                         
     *-pci:2                                                                   
          description: Host bridge                                             
          product: K8T890 Host Bridge                                          
          vendor: VIA Technologies, Inc.                                       
          physical id: 102                                                     
          bus info: pci@0000:00:00.2                                           
          version: 00                                                          
          width: 32 bits                                                       
          clock: 33MHz                                                         
     *-pci:3                                                                   
          description: Host bridge                                             
          product: K8T890 Host Bridge                                          
          vendor: VIA Technologies, Inc.                                       
          physical id: 103                                                     
          bus info: pci@0000:00:00.3                                           
          version: 00                                                          
          width: 32 bits                                                       
          clock: 33MHz                                                         
     *-pci:4                                                                   
          description: Host bridge                                             
          product: K8T890 Host Bridge                                          
          vendor: VIA Technologies, Inc.                                       
          physical id: 104                                                     
          bus info: pci@0000:00:00.4                                           
          version: 00                                                          
          width: 32 bits                                                       
          clock: 33MHz                                                         
     *-pci:5                                                                   
          description: Host bridge                                             
          product: K8T890 Host Bridge                                          
          vendor: VIA Technologies, Inc.                                       
          physical id: 105                                                     
          bus info: pci@0000:00:00.7                                           
          version: 00                                                          
          width: 32 bits                                                       
          clock: 33MHz                                                         
     *-pci:6                                                                   
          description: Host bridge                                             
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration                                                                              
          vendor: Advanced Micro Devices [AMD]                                 
          physical id: 106                                                     
          bus info: pci@0000:00:18.0                                           
          version: 00                                                          
          width: 32 bits                                                       
          clock: 33MHz                                                         
     *-pci:7                                                                   
          description: Host bridge                                             
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 107
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 108
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 109
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:14:a5:88:e2:40
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.99.125 multicast=yes wireless=IEEE 802.11bg

---

### Post by cafeteriaboy on 2010-02-21
Same problem here. The source turned out to be my monitor (Samsung t240hd). Ubuntu booted without any problems after I switched to an older CRT I had in the closet. I'm working on finding a solution.

---

### Post by efflandt on 2010-02-21
In /etc/default/grub, try removing "splash" from the following line (and "quiet" if you want verbose output while booting).  You have to edit it as root (**gksu gedit** or **sudo nano**).

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

For example you could change the above line to following (# comments out that line for later reference) and if that works, you could later put the "quiet" back in.

#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT=""

Then do **sudo update-grub**.

Apparently usplash can crash if it does not think a digitally connected (HDMI or DVI) monitor is capable of the resolution in /etc/usplash.conf.  I had that problem when I switched from DVI 1280x1024 to DVI 1280x720 HDTV (but not when using VGA) until I changed usplash.conf to 720.  Although, it does not seem to be a problem with my DVI to HDMI 1080p display with 1920 1080 in usplash.conf, that initially boots in a low resolution (1024x768 I think) before automatically switching to 1080p for X login screen.

---

