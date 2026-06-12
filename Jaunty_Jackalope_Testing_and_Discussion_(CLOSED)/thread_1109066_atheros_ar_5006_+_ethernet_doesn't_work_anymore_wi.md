---
title: "atheros ar 5006 + ethernet doesn't work anymore with the last update"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nowardev on 2009-03-28
ethernet and wifi  doesnt work anymore after the last update 28 mar 2009

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

```

---

### Post by tad1073 on 2009-03-28
[LEFT]Same problem here with Atheros 5008 wifi chip-set
[/LEFT]

---

### Post by nowardev on 2009-03-30
here now everything is working fine

---

### Post by rodneymillerpca on 2009-03-30
Try [http://www.hp2133guide.com/forums/viewtopic.php?p=10230](http://www.hp2133guide.com/forums/viewtopic.php?p=10230) Ubuntu users take notice of my post at the bottom of that one.

---

### Post by nowardev on 2009-03-31
now i got the same problem of some days ago OMG

as you can see i get ath5k but....  it doesn't work with wpa or unlocked wifi 

 lsmod | grep ath
ath5k                 126724  0
lbm_cw_mac80211       227364  1 ath5k
lbm_cw_cfg80211        73760  2 ath5k,lbm_cw_mac80211
led_class              12036  1 ath5k

---

### Post by taavikko on 2009-03-31
Try rmmodding "acer_wmi" if it's loaded, that caused some mess in my laptop. But after that it's working.

And if it works, just blacklist it for future references.

```
sudo rmmod acer_wmi && echo "blacklist acer_wmi" |sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by nowardev on 2009-03-31
lsmod | grep acer ---> nothing

---

### Post by rodneymillerpca on 2009-04-06
> **nowardev said:**
> now i got the same problem of some days ago OMG

as you can see i get ath5k but....  it doesn't work with wpa or unlocked wifi 

 lsmod | grep ath
ath5k                 126724  0
lbm_cw_mac80211       227364  1 ath5k
lbm_cw_cfg80211        73760  2 ath5k,lbm_cw_mac80211
led_class              12036  1 ath5k

I travel frequent and have had no troubles connecting with either unlocked or the wpa at home..

---

### Post by nowardev on 2009-04-07
oh right 

because on your machine it  works ...  it has to work in everymachine right right omg

---

### Post by taavikko on 2009-04-07
Please post as attachment or in pastebin

```
dmesg > ~/dmesg.txt
```

---

### Post by nowardev on 2009-04-07
done!

and of course
```
 
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset     
[    0.000000] Initializing cgroup subsys cpu        
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #40-Ubuntu SMP Fri Apr 3 17:39:51 UTC 2009 (Ubuntu 2.6.28-11.40-generic)                                                        
[    0.000000] KERNEL supported cpus:                                                                                 
[    0.000000]   Intel GenuineIntel                                                                                   
[    0.000000]   AMD AuthenticAMD                                                                                     
[    0.000000]   NSC Geode by NSC                                                                                     
[    0.000000]   Cyrix CyrixInstead                                                                                   
[    0.000000]   Centaur CentaurHauls                                                                                 
[    0.000000]   Transmeta GenuineTMx86                                                                               
[    0.000000]   Transmeta TransmetaCPU                                                                               
[    0.000000]   UMC UMC UMC UMC                                                                                      
[    0.000000] BIOS-provided physical RAM map:                                                                        
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)                                               
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)                                             
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)                                             
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f670000 (usable)                                               
[    0.000000]  BIOS-e820: 000000003f670000 - 000000003f700000 (ACPI NVS)                                             
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)                                             
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)                                             
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)                                             
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)                                             
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)                                             
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)                                             
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)                                             
[    0.000000] DMI present.                                                                                           
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.                                    
[    0.000000] last_pfn = 0x3f670 max_arch_pfn = 0x100000                                                             
[    0.000000] Scanning 0 areas for low memory corruption                                                             
[    0.000000] modified physical RAM map:                                                                             
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)                                              
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)                                                
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)                                              
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)                                              
[    0.000000]  modified: 0000000000100000 - 000000003f670000 (usable)                                                
[    0.000000]  modified: 000000003f670000 - 000000003f700000 (ACPI NVS)                                              
[    0.000000]  modified: 000000003f700000 - 0000000040000000 (reserved)                                              
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)                                              
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)                                              
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)                                              
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)                                              
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)                                              
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)                                              
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000                                              
[    0.000000] RAMDISK: 378c1000 - 37fefc0e                                                                           
[    0.000000] Allocated new RAMDISK: 00881000 - 00fafc0e                                                             
[    0.000000] Move RAMDISK from 00000000378c1000 - 0000000037fefc0d to 00881000 - 00fafc0d                           
[    0.000000] ACPI: RSDP 000F6960, 0024 (r2 TOSINV)                                                                  
[    0.000000] ACPI: XSDT 3F678718, 008C (r1 TOSINV TOSINV00  6040000  INV        0)                                  
[    0.000000] ACPI: FACP 3F681BF8, 00F4 (r3 TOSINV TOSINV00  6040000 ALAN        1)                                  
[    0.000000] ACPI: DSDT 3F67A4B1, 76D3 (r2 TOSINV CALISTGA  6040000 INTL 20050624)                                  
[    0.000000] ACPI: FACS 3F682FC0, 0040                                                                              
[    0.000000] ACPI: APIC 3F681CEC, 0068 (r1 INTEL  CALISTGA  6040000 LOHR       5A)                                  
[    0.000000] ACPI: HPET 3F681D54, 0038 (r1 INTEL  CALISTGA  6040000 LOHR       5A)                                  
[    0.000000] ACPI: MCFG 3F681D8C, 003C (r1 INTEL  CALISTGA  6040000 LOHR       5A)                                  
[    0.000000] ACPI: TCPA 3F681DC8, 0032 (r1 PTLTD  CALISTGA  6040000  PTL        1)                                  
[    0.000000] ACPI: APIC 3F681DFA, 0068 (r1 TOSINV   APIC    6040000  INV        0)                                  
[    0.000000] ACPI: SLIC 3F681E62, 0176 (r1 TOSINV TOSINV00  6040000  INV        0)                                  
[    0.000000] ACPI: BOOT 3F681FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)                                  
[    0.000000] ACPI: SSDT 3F679E62, 064F (r1 SataRe  SataPri     1000 INTL 20050624)                                  
[    0.000000] ACPI: SSDT 3F6797D0, 0692 (r1 SataRe  SataSec     1000 INTL 20050624)                                  
[    0.000000] ACPI: SSDT 3F678D30, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)                                  
[    0.000000] ACPI: SSDT 3F678C8A, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050624)                                  
[    0.000000] ACPI: SSDT 3F6787A4, 04E6 (r1  PmRef    CpuPm     3000 INTL 20050624)                                  
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0                                                      
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org                        
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                    
[    0.000000] 130MB HIGHMEM available.                                                                               
[    0.000000] 883MB LOWMEM available.                                                                                
[    0.000000]   mapped low ram: 0 - 373fe000                                                                         
[    0.000000]   low ram: 00000000 - 373fe000                                                                         
[    0.000000]   bootmap 00012000 - 00018e80                                                                          
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]                                           
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                          
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]                          
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]                          
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]                          
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]                          
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]                          
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]                          
[    0.000000]   #7 [0000881000 - 0000fafc0e]      NEW RAMDISK ==> [0000881000 - 0000fafc0e]                          
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]                          
[    0.000000] found SMP MP-table at [c00f6a10] 000f6a10                                                              
[    0.000000] Zone PFN ranges:                                                                                       
[    0.000000]   DMA      0x00000010 -> 0x00001000                                                                    
[    0.000000]   Normal   0x00001000 -> 0x000373fe                                                                    
[    0.000000]   HighMem  0x000373fe -> 0x0003f670                                                                    
[    0.000000] Movable zone start PFN for each node                                                                   
[    0.000000] early_node_map[2] active PFN ranges                                                                    
[    0.000000]     0: 0x00000010 -> 0x0000009f                                                                        
[    0.000000]     0: 0x00000100 -> 0x0003f670                                                                        
[    0.000000] On node 0 totalpages: 259583                                                                           
[    0.000000] free_area_init_node: node 0, pgdat c06d0f00, node_mem_map c1000200                                     
[    0.000000]   DMA zone: 32 pages used for memmap                                                                   
[    0.000000]   DMA zone: 0 pages reserved                                                                           
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0                                                                   
[    0.000000]   Normal zone: 1736 pages used for memmap                                                              
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31                                                             
[    0.000000]   HighMem zone: 261 pages used for memmap                                                              
[    0.000000]   HighMem zone: 33133 pages, LIFO batch:7                                                              
[    0.000000]   Movable zone: 0 pages used for memmap                                                                
[    0.000000] ACPI: PM-Timer IO Port: 0x1008                                                                         
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                    
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)                                                     
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)                                                     
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])                                                    
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])                                                    
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])                                                
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23                                         
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                                               
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)                                            
[    0.000000] ACPI: IRQ0 used by override.                                                                           
[    0.000000] ACPI: IRQ2 used by override.                                                                           
[    0.000000] ACPI: IRQ9 used by override.                                                                           
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs                                                          
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000                                                             
[    0.000000] Using ACPI (MADT) for SMP configuration information                                                    
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs                                                                   
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000                                      
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000                                      
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000                                      
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)                                 
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data                                                         
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1                                                              
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257554                            
[    0.000000] Kernel command line: root=UUID=57973f83-f921-4c8d-8374-854ba40efbbb ro quiet splash                    
[    0.000000] Enabling fast FPU save and restore... done.                                                            
[    0.000000] Enabling unmasked SIMD FPU exception support... done.                                                  
[    0.000000] Initializing CPU#0                                                                                     
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)                                                  
[    0.000000] Extended CMOS year: 2000                                                                               
[    0.000000] Fast TSC calibration using PIT                                                                         
[    0.000000] Detected 1595.994 MHz processor.                                                                       
[    0.004000] Console: colour VGA+ 80x25                                                                             
[    0.004000] console [tty0] enabled                                                                                 
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)                                       
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)                                         
[    0.004000] allocated 5193600 bytes of page_cgroup                                                                 
[    0.004000] please try cgroup_disable=memory option if you don't want                                              
[    0.004000] Scanning for low memory corruption every 60 seconds                                                    
[    0.004000] Memory: 1008780k/1038784k available (4126k kernel code, 29168k reserved, 2208k data, 532k init, 133576k highmem)                                                                                                             
[    0.004000] virtual kernel memory layout:                                                                          
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)                                                      
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)                                                      
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)                                                      
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)                                                      
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)                                                      
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)                                                      
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)                                                      
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.                            
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1                                
[    0.004000] hpet clockevent registered                                                                             
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer                                       
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.98 BogoMIPS (lpj=6383976)                                                                                                                    
[    0.004000] Security Framework initialized                                                                         
[    0.004000] SELinux:  Disabled at boot.                                                                            
[    0.004000] AppArmor: AppArmor initialized                                                                         
[    0.004000] Mount-cache hash table entries: 512                                                                    
[    0.004000] Initializing cgroup subsys ns                                                                          
[    0.004000] Initializing cgroup subsys cpuacct                                                                     
[    0.004000] Initializing cgroup subsys memory                                                                      
[    0.004000] Initializing cgroup subsys freezer                                                                     
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K                                                                  
[    0.004000] CPU: L2 cache: 1024K                                                                                   
[    0.004000] CPU: Physical Processor ID: 0                                                                          
[    0.004000] CPU: Processor Core ID: 0                                                                              
[    0.004000] using mwait in idle threads.                                                                           
[    0.004000] Checking 'hlt' instruction... OK.                                                                      
[    0.019488] ACPI: Core revision 20080926                                                                           
[    0.022721] ACPI: Checking initramfs for custom DSDT                                                               
[    0.408558] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1                                                   
[    0.450632] CPU0: Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c                                      
[    0.452001] Booting processor 1 APIC 0x1 ip 0x6000                                                                 
[    0.004000] Initializing CPU#1                                                                                     
[    0.004000] Calibrating delay using timer specific routine.. 3192.00 BogoMIPS (lpj=6384015)                        
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K                                                                  
[    0.004000] CPU: L2 cache: 1024K                                                                                   
[    0.004000] CPU: Physical Processor ID: 0                                                                          
[    0.004000] CPU: Processor Core ID: 1                                                                              
[    0.536433] CPU1: Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c                                      
[    0.536458] checking TSC synchronization [CPU#0 -> CPU#1]: passed.                                                 
[    0.540053] Brought up 2 CPUs                                                                                      
[    0.540056] Total of 2 processors activated (6383.99 BogoMIPS).                                                    
[    0.540120] CPU0 attaching sched-domain:                                                                           
[    0.540123]  domain 0: span 0-1 level MC                                                                           
[    0.540126]   groups: 0 1                                                                                          
[    0.540134] CPU1 attaching sched-domain:                                                                           
[    0.540136]  domain 0: span 0-1 level MC                                                                           
[    0.540139]   groups: 1 0                                                                                          
[    0.540232] net_namespace: 776 bytes                                                                               
[    0.540239] Booting paravirtualized kernel on bare hardware                                                        
[    0.540450] Time:  8:01:28  Date: 04/07/09                                                                         
[    0.540450] regulator: core version 0.5                                                                            
[    0.540450] NET: Registered protocol family 16                                                                     
[    0.540450] EISA bus registered                                                                                    
[    0.540450] ACPI: bus type pci registered                                                                          
[    0.540450] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255                                       
[    0.540450] PCI: Not using MMCONFIG.                                                                               
[    0.540473] PCI: PCI BIOS revision 2.10 entry at 0xfd604, last bus=7                                               
[    0.540475] PCI: Using configuration type 1 for base access                                                        
[    0.544337] ACPI: EC: Look up EC in DSDT                                                                           
[    0.572083] ACPI: BIOS _OSI(Linux) query ignored                                                                   
[    0.573258] ACPI: EC: non-query interrupt received, switching to interrupt mode                                    
[    0.580165] ACPI: Interpreter enabled                                                                              
[    0.580170] ACPI: (supports S0 S3 S4 S5)                                                                           
[    0.580194] ACPI: Using IOAPIC for interrupt routing                                                               
[    0.580259] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255                                       
[    0.653270] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources                                      
[    0.653274] PCI: Using MMCONFIG for extended config space                                                          
[    0.728671] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62                                          
[    0.728675] ACPI: EC: driver started in interrupt mode                                                             
[    0.776277] ACPI: ACPI Dock Station Driver: 1 docks/bays found                                                     
[    0.776293] ACPI: PCI Root Bridge [PCI0] (0000:00)                                                                 
[    0.776398] pci 0000:00:02.0: reg 10 32bit mmio: [0xf0a00000-0xf0a7ffff]                                           
[    0.776404] pci 0000:00:02.0: reg 14 io port: [0x1800-0x1807]                                                      
[    0.776410] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff]                                           
[    0.776417] pci 0000:00:02.0: reg 1c 32bit mmio: [0xf0b00000-0xf0b3ffff]                                           
[    0.776456] pci 0000:00:02.1: reg 10 32bit mmio: [0xf0a80000-0xf0afffff]                                           
[    0.776580] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf0b40000-0xf0b43fff]                                           
[    0.776624] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold                                                  
[    0.776630] pci 0000:00:1b.0: PME# disabled                                                                        
[    0.776702] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold                                                  
[    0.776707] pci 0000:00:1c.0: PME# disabled                                                                        
[    0.776781] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold                                                  
[    0.776787] pci 0000:00:1c.1: PME# disabled                                                                        
[    0.776861] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold                                                  
[    0.776866] pci 0000:00:1c.2: PME# disabled                                                                        
[    0.776939] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]                                                      
[    0.777006] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]                                                      
[    0.777073] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]                                                      
[    0.777140] pci 0000:00:1d.3: reg 20 io port: [0x1880-0x189f]                                                      
[    0.777211] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf0d44000-0xf0d443ff]                                           
[    0.777262] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold                                                  
[    0.777268] pci 0000:00:1d.7: PME# disabled                                                                        
[    0.777437] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO                                
[    0.777442] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO                                         
[    0.777497] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]                                                          
[    0.777506] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]                                                          
[    0.777515] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]                                                          
[    0.777524] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]                                                          
[    0.777533] pci 0000:00:1f.2: reg 20 io port: [0x18b0-0x18bf]                                                      
[    0.777560] pci 0000:00:1f.2: PME# supported from D3hot                                                            
[    0.777565] pci 0000:00:1f.2: PME# disabled                                                                        
[    0.777632] pci 0000:00:1f.3: reg 20 io port: [0x18c0-0x18df]                                                      
[    0.777798] pci 0000:00:1c.1: bridge io port: [0x2000-0x2fff]                                                      
[    0.777804] pci 0000:00:1c.1: bridge 32bit mmio: [0xf0700000-0xf07fffff]                                           
[    0.777814] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf0200000-0xf03fffff]                                      
[    0.777890] pci 0000:05:00.0: reg 10 64bit mmio: [0xf0800000-0xf080ffff]                                           
[    0.778030] pci 0000:00:1c.2: bridge io port: [0x3000-0x3fff]                                                      
[    0.778036] pci 0000:00:1c.2: bridge 32bit mmio: [0xf0800000-0xf08fffff]                                           
[    0.778046] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xf0400000-0xf05fffff]                                      
[    0.778110] pci 0000:07:06.0: reg 10 32bit mmio: [0x000000-0x000fff]                                               
[    0.778126] pci 0000:07:06.0: supports D1 D2                                                                       
[    0.778128] pci 0000:07:06.0: PME# supported from D0 D1 D2 D3hot D3cold                                            
[    0.778135] pci 0000:07:06.0: PME# disabled                                                                        
[    0.778188] pci 0000:07:06.1: reg 10 32bit mmio: [0xf0906000-0xf09067ff]                                           
[    0.778199] pci 0000:07:06.1: reg 14 32bit mmio: [0xf0900000-0xf0903fff]                                           
[    0.778252] pci 0000:07:06.1: supports D1 D2                                                                       
[    0.778255] pci 0000:07:06.1: PME# supported from D0 D1 D2 D3hot                                                   
[    0.778261] pci 0000:07:06.1: PME# disabled                                                                        
[    0.778314] pci 0000:07:06.2: reg 10 32bit mmio: [0xf0904000-0xf0904fff]                                           
[    0.778374] pci 0000:07:06.2: supports D1 D2                                                                       
[    0.778377] pci 0000:07:06.2: PME# supported from D0 D1 D2 D3hot                                                   
[    0.778383] pci 0000:07:06.2: PME# disabled                                                                        
[    0.778432] pci 0000:07:06.3: reg 10 32bit mmio: [0xf0906800-0xf09068ff]                                           
[    0.778492] pci 0000:07:06.3: supports D1 D2                                                                       
[    0.778494] pci 0000:07:06.3: PME# supported from D0 D1 D2 D3hot                                                   
[    0.778500] pci 0000:07:06.3: PME# disabled                                                                        
[    0.778554] pci 0000:07:08.0: reg 10 32bit mmio: [0xf0905000-0xf0905fff]                                           
[    0.778564] pci 0000:07:08.0: reg 14 io port: [0x4000-0x403f]                                                      
[    0.778608] pci 0000:07:08.0: supports D1 D2                                                                       
[    0.778610] pci 0000:07:08.0: PME# supported from D0 D1 D2 D3hot D3cold                                            
[    0.778616] pci 0000:07:08.0: PME# disabled                                                                        
[    0.778666] pci 0000:00:1e.0: transparent bridge                                                                   
[    0.778672] pci 0000:00:1e.0: bridge io port: [0x4000-0x4fff]                                                      
[    0.778678] pci 0000:00:1e.0: bridge 32bit mmio: [0xf0900000-0xf09fffff]                                           
[    0.778739] bus 00 -> node 0                                                                                       
[    0.778748] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                                                    
[    0.779206] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]                                               
[    0.779399] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]                                               
[    0.779589] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]                                               
[    0.779795] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]                                               
[    0.904427] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)                                        
[    0.904588] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)                                        
[    0.904747] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11                                     
[    0.904906] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10                                     
[    0.905062] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)                                        
[    0.905220] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.                           
[    0.905379] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)                                        
[    0.905536] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)                                        
[    0.905697] ACPI: Power Resource [FN00] (off)                                                                      
[    0.906081] ACPI: WMI: Mapper loaded                                                                               
[    0.906144] SCSI subsystem initialized                                                                             
[    0.906144] libata version 3.00 loaded.                                                                            
[    0.906144] usbcore: registered new interface driver usbfs                                                         
[    0.906144] usbcore: registered new interface driver hub                                                           
[    0.906144] usbcore: registered new device driver usb                                                              
[    0.906144] PCI: Using ACPI for IRQ routing                                                                        
[    0.912013] Bluetooth: Core ver 2.13                                                                               
[    0.912035] NET: Registered protocol family 31                                                                     
[    0.912035] Bluetooth: HCI device and connection manager initialized                                               
[    0.912035] Bluetooth: HCI socket layer initialized                                                                
[    0.912035] NET: Registered protocol family 8                                                                      
[    0.912035] NET: Registered protocol family 20                                                                     
[    0.912045] NetLabel: Initializing                                                                                 
[    0.912048] NetLabel:  domain hash size = 128                                                                      
[    0.912050] NetLabel:  protocols = UNLABELED CIPSOv4                                                               
[    0.912066] NetLabel:  unlabeled traffic allowed by default                                                        
[    0.912085] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0                                                                
[    0.912091] hpet0: 3 comparators, 64-bit 14.318180 MHz counter                                                     
[    0.916085] AppArmor: AppArmor Filesystem Enabled                                                                  
[    0.920016] Switched to high resolution mode on CPU 0                                                              
[    0.920512] Switched to high resolution mode on CPU 1                                                              
[    0.924014] pnp: PnP ACPI init                                                                                     
[    0.924027] ACPI: bus type pnp registered                                                                          
[    0.996275] pnp: PnP ACPI: found 10 devices                                                                        
[    0.996279] ACPI: ACPI bus type pnp unregistered                                                                   
[    0.996284] PnPBIOS: Disabled by ACPI PNP                                                                          
[    0.996298] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved                                      
[    0.996301] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved                                      
[    0.996305] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved                                      
[    0.996309] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved                                      
[    0.996312] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved                                      
[    0.996316] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved                                      
[    0.996319] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved                                      
[    0.996323] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved                                      
[    0.996332] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved                                      
[    0.996340] system 00:06: ioport range 0x3e8-0x3ef has been reserved                                               
[    0.996344] system 00:06: ioport range 0x400-0x401 has been reserved                                               
[    0.996347] system 00:06: ioport range 0x680-0x69f has been reserved                                               
[    0.996350] system 00:06: ioport range 0x800-0x80f has been reserved                                               
[    0.996354] system 00:06: ioport range 0x1000-0x107f has been reserved                                             
[    0.996357] system 00:06: ioport range 0x1180-0x11bf has been reserved                                             
[    0.996361] system 00:06: ioport range 0x1640-0x164f has been reserved                                             
[    0.996364] system 00:06: ioport range 0xfe00-0xfe01 has been reserved                                             
[    1.031138] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02                                                    
[    1.031141] pci 0000:00:1c.0:   IO window: disabled                                                                
[    1.031149] pci 0000:00:1c.0:   MEM window: disabled                                                               
[    1.031154] pci 0000:00:1c.0:   PREFETCH window: disabled                                                          
[    1.031163] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03                                                    
[    1.031167] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff                                                           
[    1.031174] pci 0000:00:1c.1:   MEM window: 0xf0700000-0xf07fffff                                                  
[    1.031181] pci 0000:00:1c.1:   PREFETCH window: 0x000000f0200000-0x000000f03fffff                                 
[    1.031190] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05                                                    
[    1.031194] pci 0000:00:1c.2:   IO window: 0x3000-0x3fff                                                           
[    1.031201] pci 0000:00:1c.2:   MEM window: 0xf0800000-0xf08fffff                                                  
[    1.031207] pci 0000:00:1c.2:   PREFETCH window: 0x000000f0400000-0x000000f05fffff                                 
[    1.031223] pci 0000:07:06.0: CardBus bridge, secondary bus 0000:08                                                
[    1.031226] pci 0000:07:06.0:   IO window: 0x004400-0x0044ff                                                       
[    1.031232] pci 0000:07:06.0:   IO window: 0x004800-0x0048ff                                                       
[    1.031239] pci 0000:07:06.0:   PREFETCH window: 0x50000000-0x53ffffff                                             
[    1.031245] pci 0000:07:06.0:   MEM window: 0x54000000-0x57ffffff                                                  
[    1.031252] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07                                                    
[    1.031256] pci 0000:00:1e.0:   IO window: 0x4000-0x4fff                                                           
[    1.031263] pci 0000:00:1e.0:   MEM window: 0xf0900000-0xf09fffff                                                  
[    1.031269] pci 0000:00:1e.0:   PREFETCH window: 0x00000050000000-0x00000053ffffff                                 
[    1.031291] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17                                           
[    1.031298] pci 0000:00:1c.0: setting latency timer to 64                                                          
[    1.031310] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16                                           
[    1.031316] pci 0000:00:1c.1: setting latency timer to 64                                                          
[    1.031327] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18                                           
[    1.031333] pci 0000:00:1c.2: setting latency timer to 64                                                          
[    1.031342] pci 0000:00:1e.0: setting latency timer to 64                                                          
[    1.031353] pci 0000:07:06.0: enabling device (0000 -> 0003)                                                       
[    1.031359] pci 0000:07:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                           
[    1.031369] bus: 00 index 0 io port: [0x00-0xffff]                                                                 
[    1.031372] bus: 00 index 1 mmio: [0x000000-0xffffffff]                                                            
[    1.031375] bus: 02 index 0 mmio: [0x0-0x0]                                                                        
[    1.031377] bus: 02 index 1 mmio: [0x0-0x0]                                                                        
[    1.031380] bus: 02 index 2 mmio: [0x0-0x0]                                                                        
[    1.031382] bus: 02 index 3 mmio: [0x0-0x0]                                                                        
[    1.031385] bus: 03 index 0 io port: [0x2000-0x2fff]                                                               
[    1.031388] bus: 03 index 1 mmio: [0xf0700000-0xf07fffff]                                                          
[    1.031391] bus: 03 index 2 mmio: [0xf0200000-0xf03fffff]                                                          
[    1.031393] bus: 03 index 3 mmio: [0x0-0x0]                                                                        
[    1.031396] bus: 05 index 0 io port: [0x3000-0x3fff]                                                               
[    1.031399] bus: 05 index 1 mmio: [0xf0800000-0xf08fffff]                                                          
[    1.031401] bus: 05 index 2 mmio: [0xf0400000-0xf05fffff]                                                          
[    1.031404] bus: 05 index 3 mmio: [0x0-0x0]                                                                        
[    1.031407] bus: 07 index 0 io port: [0x4000-0x4fff]                                                               
[    1.031409] bus: 07 index 1 mmio: [0xf0900000-0xf09fffff]                                                          
[    1.031412] bus: 07 index 2 mmio: [0x50000000-0x53ffffff]                                                          
[    1.031415] bus: 07 index 3 io port: [0x00-0xffff]                                                                 
[    1.031418] bus: 07 index 4 mmio: [0x000000-0xffffffff]                                                            
[    1.031421] bus: 08 index 0 io port: [0x4400-0x44ff]                                                               
[    1.031423] bus: 08 index 1 io port: [0x4800-0x48ff]                                                               
[    1.031426] bus: 08 index 2 mmio: [0x50000000-0x53ffffff]                                                          
[    1.031429] bus: 08 index 3 mmio: [0x54000000-0x57ffffff]                                                          
[    1.031443] NET: Registered protocol family 2                                                                      
[    1.044069] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)                                      
[    1.044380] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)                                   
[    1.045004] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)                                            
[    1.045356] TCP: Hash tables configured (established 131072 bind 65536)                                            
[    1.045360] TCP reno registered                                                                                    
[    1.052110] NET: Registered protocol family 1                                                                      
[    1.052267] checking if image is initramfs... it is                                                                
[    1.821729] Freeing initrd memory: 7355k freed                                                                     
[    1.821776] Simple Boot Flag at 0x36 set to 0x1                                                                    
[    1.822008] cpufreq: No nForce2 chipset.                                                                           
[    1.822181] audit: initializing netlink socket (disabled)                                                          
[    1.822210] type=2000 audit(1239091288.820:1): initialized                                                         
[    1.831401] highmem bounce pool size: 64 pages                                                                     
[    1.831408] HugeTLB registered 4 MB page size, pre-allocated 0 pages                                               
[    1.833139] VFS: Disk quotas dquot_6.5.1                                                                           
[    1.833216] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)                                             
[    1.834014] fuse init (API version 7.10)                                                                           
[    1.834128] msgmni has been set to 1724                                                                            
[    1.834368] alg: No test for stdrng (krng)                                                                         
[    1.834387] io scheduler noop registered                                                                           
[    1.834391] io scheduler anticipatory registered                                                                   
[    1.834393] io scheduler deadline registered                                                                       
[    1.834414] io scheduler cfq registered (default)                                                                  
[    1.834430] pci 0000:00:02.0: Boot video device                                                                    
[    1.834573] pci 0000:07:08.0: Firmware left e100 interrupts enabled; disabling                                     
[    1.976378] pcieport-driver 0000:00:1c.0: setting latency timer to 64                                              
[    1.976433] pcieport-driver 0000:00:1c.0: found MSI capability                                                     
[    1.976474] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X                                                   
[    1.976491] pci_express 0000:00:1c.0:pcie00: allocate port service                                                 
[    1.976512] pci_express 0000:00:1c.0:pcie02: allocate port service                                                 
[    1.976527] pci_express 0000:00:1c.0:pcie03: allocate port service                                                 
[    1.976607] pcieport-driver 0000:00:1c.1: setting latency timer to 64                                              
[    1.976659] pcieport-driver 0000:00:1c.1: found MSI capability                                                     
[    1.976696] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X                                                   
[    1.976713] pci_express 0000:00:1c.1:pcie00: allocate port service                                                 
[    1.976729] pci_express 0000:00:1c.1:pcie02: allocate port service                                                 
[    1.976744] pci_express 0000:00:1c.1:pcie03: allocate port service                                                 
[    1.976824] pcieport-driver 0000:00:1c.2: setting latency timer to 64                                              
[    1.976877] pcieport-driver 0000:00:1c.2: found MSI capability                                                     
[    1.976912] pcieport-driver 0000:00:1c.2: irq 2301 for MSI/MSI-X                                                   
[    1.976930] pci_express 0000:00:1c.2:pcie00: allocate port service                                                 
[    1.976950] pci_express 0000:00:1c.2:pcie02: allocate port service                                                 
[    1.976966] pci_express 0000:00:1c.2:pcie03: allocate port service                                                 
[    1.977066] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                                        
[    1.977181] pciehp: PCI Express Hot Plug Controller Driver version: 0.4                                            
[    1.977763] ACPI: AC Adapter [ADP0] (on-line)                                                                      
[    1.983412] ACPI: Battery Slot [BAT0] (battery present)                                                            
[    1.983513] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0                              
[    1.983516] ACPI: Power Button (FF) [PWRF]                                                                         
[    1.983575] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1                            
[    1.983649] ACPI: Lid Switch [LID]                                                                                 
[    1.983704] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2                     
[    1.983707] ACPI: Power Button (CM) [PWRB]                                                                         
[    1.983898] fan PNP0C0B:00: registered as cooling_device0                                                          
[    1.983907] ACPI: Fan [FAN0] (off)                                                                                 
[    1.984583] ACPI: SSDT 3F6794D6, 023D (r1  PmRef  Cpu0Ist     3000 INTL 20050624)                                  
[    1.985115] ACPI: SSDT 3F678F8F, 04C2 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)                                  
[    1.988312] ACPI: CPU0 (power states: C1[C1] C2[C2])                                                               
[    1.988336] processor ACPI_CPU:00: registered as cooling_device1                                                   
[    1.988340] ACPI: Processor [CPU0] (supports 8 throttling states)                                                  
[    1.988791] ACPI: SSDT 3F679713, 00BD (r1  PmRef  Cpu1Ist     3000 INTL 20050624)                                  
[    1.989277] ACPI: SSDT 3F679451, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)                                  
[    1.990635] ACPI: CPU1 (power states: C1[C1] C2[C2])                                                               
[    1.990660] processor ACPI_CPU:01: registered as cooling_device2                                                   
[    1.990664] ACPI: Processor [CPU1] (supports 8 throttling states)                                                  
[    2.064515] thermal LNXTHERM:01: registered as thermal_zone0                                                       
[    2.064678] ACPI: Thermal Zone [TZ00] (50 C)                                                                       
[    2.065442] thermal LNXTHERM:02: registered as thermal_zone1                                                       
[    2.066431] ACPI: Transitioning device [FAN0] to D0                                                                
[    2.066434] ACPI: Unable to turn cooling device [f6c15b40] 'on'                                                    
[    2.066438] ACPI: Thermal Zone [TZ01] (46 C)                                                                       
[    2.066510] isapnp: Scanning for PnP cards...                                                                      
[    2.420504] isapnp: No Plug & Play device found                                                                    
[    2.429333] Serial: 8250/16550 driver4 ports, IRQ sharing enabled                                                  
[    2.430603] brd: module loaded                                                                                     
[    2.430996] loop: module loaded                                                                                    
[    2.431087] Fixed MDIO Bus: probed                                                                                 
[    2.431095] PPP generic driver version 2.4.2                                                                       
[    2.431178] input: Macintosh mouse button emulation as /devices/virtual/input/input3                               
[    2.431214] Driver 'sd' needs updating - please use bus_type methods                                               
[    2.431226] Driver 'sr' needs updating - please use bus_type methods                                               
[    2.431322] ata_piix 0000:00:1f.2: version 2.12                                                                    
[    2.431345] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19                                      
[    2.431351] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]                                                           
[    2.584020] ata_piix 0000:00:1f.2: setting latency timer to 64                                                     
[    2.584135] scsi0 : ata_piix                                                                                       
[    2.584260] scsi1 : ata_piix                                                                                       
[    2.585622] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14                                        
[    2.585626] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15                                        
[    2.748532] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC7DP, max UDMA/100                                        
[    2.748536] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)                                           
[    2.764547] ata1.00: configured for UDMA/100                                                                       
[    2.928524] ata2.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.10, max UDMA/33                                             
[    2.944480] ata2.00: configured for UDMA/33                                                                        
[    2.945032] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5                           
[    2.945159] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)                                
[    2.945181] sd 0:0:0:0: [sda] Write Protect is off                                                                 
[    2.945184] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                              
[    2.945220] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                
[    2.945303] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)                                
[    2.945322] sd 0:0:0:0: [sda] Write Protect is off                                                                 
[    2.945325] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                              
[    2.945357] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                
[    2.945362]  sda: sda1 sda2 < sda5 sda6 >                                                                          
[    2.998714] sd 0:0:0:0: [sda] Attached SCSI disk                                                                   
[    2.998768] sd 0:0:0:0: Attached scsi generic sg0 type 0                                                           
[    3.000692] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.10 PQ: 0 ANSI: 5                           
[    3.005120] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray                                  
[    3.005124] Uniform CD-ROM driver Revision: 3.20                                                                   
[    3.005234] sr 1:0:0:0: Attached scsi CD-ROM sr0                                                                   
[    3.005283] sr 1:0:0:0: Attached scsi generic sg1 type 5                                                           
[    3.006096] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                                             
[    3.006127] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23                                      
[    3.006156] ehci_hcd 0000:00:1d.7: setting latency timer to 64                                                     
[    3.006160] ehci_hcd 0000:00:1d.7: EHCI Host Controller                                                            
[    3.006236] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1                                   
[    3.010164] ehci_hcd 0000:00:1d.7: debug port 1                                                                    
[    3.010172] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported                                          
[    3.010190] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0d44000                                                       
[    3.024012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00                                                      
[    3.024107] usb usb1: configuration #1 chosen from 1 choice                                                        
[    3.024142] hub 1-0:1.0: USB hub found                                                                             
[    3.024154] hub 1-0:1.0: 8 ports detected                                                                          
[    3.024304] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                                                 
[    3.024324] uhci_hcd: USB Universal Host Controller Interface driver                                               
[    3.024357] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23                                      
[    3.024365] uhci_hcd 0000:00:1d.0: setting latency timer to 64                                                     
[    3.024369] uhci_hcd 0000:00:1d.0: UHCI Host Controller                                                            
[    3.024421] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2                                   
[    3.024450] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820                                                      
[    3.024542] usb usb2: configuration #1 chosen from 1 choice                                                        
[    3.024573] hub 2-0:1.0: USB hub found                                                                             
[    3.024582] hub 2-0:1.0: 2 ports detected                                                                          
[    3.024686] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19                                      
[    3.024693] uhci_hcd 0000:00:1d.1: setting latency timer to 64                                                     
[    3.024697] uhci_hcd 0000:00:1d.1: UHCI Host Controller                                                            
[    3.024749] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3                                   
[    3.024787] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840                                                      
[    3.024878] usb usb3: configuration #1 chosen from 1 choice                                                        
[    3.024909] hub 3-0:1.0: USB hub found                                                                             
[    3.024919] hub 3-0:1.0: 2 ports detected                                                                          
[    3.025023] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18                                      
[    3.025031] uhci_hcd 0000:00:1d.2: setting latency timer to 64                                                     
[    3.025035] uhci_hcd 0000:00:1d.2: UHCI Host Controller                                                            
[    3.025089] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4                                   
[    3.025126] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860                                                      
[    3.025214] usb usb4: configuration #1 chosen from 1 choice                                                        
[    3.025246] hub 4-0:1.0: USB hub found                                                                             
[    3.025254] hub 4-0:1.0: 2 ports detected                                                                          
[    3.025363] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16                                      
[    3.025371] uhci_hcd 0000:00:1d.3: setting latency timer to 64                                                     
[    3.025375] uhci_hcd 0000:00:1d.3: UHCI Host Controller                                                            
[    3.025425] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5                                   
[    3.025462] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880                                                      
[    3.025564] usb usb5: configuration #1 chosen from 1 choice                                                        
[    3.025602] hub 5-0:1.0: USB hub found                                                                             
[    3.025612] hub 5-0:1.0: 2 ports detected                                                                          
[    3.025757] usbcore: registered new interface driver libusual                                                      
[    3.025798] usbcore: registered new interface driver usbserial                                                     
[    3.025812] USB Serial support registered for generic                                                              
[    3.025830] usbcore: registered new interface driver usbserial_generic                                             
[    3.025832] usbserial: USB Serial Driver core                                                                      
[    3.025890] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12                                 
[    3.028372] i8042.c: Detected active multiplexing controller, rev 1.1.                                             
[    3.030063] serio: i8042 KBD port at 0x60,0x64 irq 1                                                               
[    3.030071] serio: i8042 AUX0 port at 0x60,0x64 irq 12                                                             
[    3.030074] serio: i8042 AUX1 port at 0x60,0x64 irq 12                                                             
[    3.030078] serio: i8042 AUX2 port at 0x60,0x64 irq 12                                                             
[    3.030081] serio: i8042 AUX3 port at 0x60,0x64 irq 12                                                             
[    3.032054] mice: PS/2 mouse device common for all mice                                                            
[    3.048086] rtc_cmos 00:07: RTC can wake from S4                                                                   
[    3.048126] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0                                                  
[    3.048163] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs                                          
[    3.048244] device-mapper: uevent: version 1.0.3                                                                   
[    3.048372] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com                       
[    3.048479] device-mapper: multipath: version 1.0.5 loaded                                                         
[    3.048482] device-mapper: multipath round-robin: version 1.0.0 loaded                                             
[    3.048592] EISA: Probing bus 0 at eisa.0                                                                          
[    3.048600] Cannot allocate resource for EISA slot 1                                                               
[    3.048603] Cannot allocate resource for EISA slot 2                                                               
[    3.048606] Cannot allocate resource for EISA slot 3                                                               
[    3.048609] Cannot allocate resource for EISA slot 4                                                               
[    3.048629] EISA: Detected 0 cards.                                                                                
[    3.048765] cpuidle: using governor ladder                                                                         
[    3.048882] cpuidle: using governor menu                                                                           
[    3.049514] TCP cubic registered                                                                                   
[    3.049642] NET: Registered protocol family 10                                                                     
[    3.050162] lo: Disabled Privacy Extensions                                                                        
[    3.050567] NET: Registered protocol family 17                                                                     
[    3.050589] Bluetooth: L2CAP ver 2.11                                                                              
[    3.050592] Bluetooth: L2CAP socket layer initialized                                                              
[    3.050595] Bluetooth: SCO (Voice Link) ver 0.6                                                                    
[    3.050597] Bluetooth: SCO socket layer initialized                                                                
[    3.050648] Bluetooth: RFCOMM socket layer initialized                                                             
[    3.050651] Marking TSC unstable due to TSC halts in idle                                                          
[    3.050664] Bluetooth: RFCOMM TTY layer initialized                                                                
[    3.050666] Bluetooth: RFCOMM ver 1.10                                                                             
[    3.051526] Using IPI No-Shortcut mode                                                                             
[    3.051624] registered taskstats version 1                                                                         
[    3.051767]   Magic number: 5:320:17                                                                               
[    3.051872] rtc_cmos 00:07: setting system clock to 2009-04-07 08:01:30 UTC (1239091290)                           
[    3.051876] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found                                                   
[    3.051878] EDD information not available.                                                                         
[    3.052211] Freeing unused kernel memory: 532k freed                                                               
[    3.052392] Write protecting the kernel text: 4128k                                                                
[    3.052456] Write protecting the kernel read-only data: 1532k                                                      
[    3.087146] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4                     
[    3.401012] ohci1394 0000:07:06.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17                                      
[    3.450970] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f0906000-f09067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]                                                                                                         
[    3.458855] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI                                                  
[    3.458859] e100: Copyright(c) 1999-2006 Intel Corporation                                                         
[    3.461017] e100 0000:07:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20                                          
[    3.498444] e100 0000:07:08.0: PME# disabled                                                                       
[    3.503683] e100: eth0: e100_probe: addr 0xf0905000, irq 20, MAC addr 00:a0:d1:69:b6:f3                            
[    3.560041] usb 4-2: new low speed USB device using uhci_hcd and address 2                                         
[    3.733261] usb 4-2: configuration #1 chosen from 1 choice                                                         
[    3.743099] usbcore: registered new interface driver hiddev                                                        
[    3.758817] input: Logitech USB Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input5            
[    3.761130] generic-usb 0003:046D:C00C.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:1d.2-2/input0                                                                                                        
[    3.761155] usbcore: registered new interface driver usbhid                                                        
[    3.761159] usbhid: v2.6:USB HID core driver                                                                       
[    3.968535] PM: Starting manual resume from disk                                                                   
[    3.968540] PM: Resume from partition 8:1                                                                          
[    3.968542] PM: Checking hibernation image.                                                                        
[    3.968770] PM: Resume from disk failed.                                                                           
[    3.982136] EXT4-fs: barriers enabled                                                                              
[    3.996233] kjournald2 starting.  Commit interval 5 seconds                                                        
[    3.996252] EXT4-fs: delayed allocation enabled                                                                    
[    3.996255] EXT4-fs: file extents enabled                                                                          
[    3.997581] EXT4-fs: mballoc enabled                                                                               
[    3.997587] EXT4-fs: mounted filesystem with ordered data mode.                                                    
[    6.477446] ACPI: Transitioning device [FAN0] to D0                                                                
[    6.477452] ACPI: Unable to turn cooling device [f6c15b40] 'on'                                                    
[    9.243043] udev: starting version 140                                                                             
[    9.662386] acpi device:0a: registered as cooling_device3                                                          
[    9.662639] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/input/input6                   
[    9.668158] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)                                         
[    9.924746] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume                
[   10.083364] input: PC Speaker as /devices/platform/pcspkr/input/input7                                             
[   10.146815] yenta_cardbus 0000:07:06.0: CardBus bridge found [1179:ff10]                                           
[   10.146843] yenta_cardbus 0000:07:06.0: Enabling burst memory read transactions                                    
[   10.146850] yenta_cardbus 0000:07:06.0: Using CSCINT to route CSC interrupts to PCI                                
[   10.146853] yenta_cardbus 0000:07:06.0: Routing CardBus interrupts to PCI                                          
[   10.146861] yenta_cardbus 0000:07:06.0: TI: mfunc 0x01a01b22, devctl 0x66                                          
[   10.170705] sdhci: Secure Digital Host Controller Interface driver                                                 
[   10.170709] sdhci: Copyright(c) Pierre Ossman                                                                      
[   10.235536] intel_rng: FWH not detected                                                                            
[   10.253732] Linux agpgart interface v0.103                                                                         
[   10.266798] agpgart-intel 0000:00:00.0: Intel 945GM Chipset                                                        
[   10.267213] agpgart-intel 0000:00:00.0: detected 7932K stolen memory                                               
[   10.270762] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000                                          
[   10.311465] cfg80211: Using static regulatory domain info                                                          
[   10.311470] cfg80211: Regulatory domain: US                                                                        
[   10.311472]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)                                     
[   10.311476]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)                                          
[   10.311480]  (5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)                                          
[   10.311483]  (5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)                                          
[   10.311486]  (5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)                                          
[   10.311489]  (5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)                                          
[   10.311493]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)                                          
[   10.311536] cfg80211: Calling CRDA for country: US                                                                 
[   10.381417] yenta_cardbus 0000:07:06.0: ISA IRQ mask 0x0cf8, PCI irq 18                                            
[   10.381424] yenta_cardbus 0000:07:06.0: Socket status: 30000006                                                    
[   10.381429] pci_bus 0000:07: Raising subordinate bus# of parent bus (#07) from #07 to #0b                          
[   10.381438] yenta_cardbus 0000:07:06.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff                      
[   10.381442] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x4fff: clean.                                  
[   10.381733] yenta_cardbus 0000:07:06.0: pcmcia: parent PCI bridge Memory window: 0xf0900000 - 0xf09fffff           
[   10.381737] yenta_cardbus 0000:07:06.0: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff           
[   10.382269] sdhci-pci 0000:07:06.3: SDHCI controller found [104c:803c] (rev 0)                                     
[   10.382290] sdhci-pci 0000:07:06.3: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                     
[   10.382421] mmc0: SDHCI controller on PCI [0000:07:06.3] using DMA                                                 
[   10.382469] tifm_7xx1 0000:07:06.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                     
[   10.411380] iTCO_vendor_support: vendor-support=0                                                                  
[   10.413480] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05                                                        
[   10.413671] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x1060)                              
[   10.413784] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)                                                   
[   10.478925] cfg80211: Regulatory domain changed to country: US                                                     
[   10.478931]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)                                     
[   10.478934]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)                                          
[   10.478938]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)                                          
[   10.478941]  (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                          
[   10.478944]  (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                          
[   10.478948]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)                                          
[   10.578639] ath5k 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                         
[   10.578655] ath5k 0000:05:00.0: setting latency timer to 64                                                        
[   10.578735] ath5k 0000:05:00.0: registered as 'phy0'                                                               
[   10.726034] phy0: Selected rate control algorithm 'minstrel'                                                       
[   10.752701] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22                                     
[   10.752790] HDA Intel 0000:00:1b.0: setting latency timer to 64                                                    
[   10.785882] hda_codec: Unknown model for ALC660VD/ALC861VD, trying auto-probe from BIOS...                         
[   10.808427] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa0, PHY: 0x61)                                           
[   10.841854] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0                                
[   10.874749] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8                       
[   10.877321] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.                                    
[   10.879392] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7                     
[   10.880242] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.                                    
[   10.880965] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.                                    
[   10.881917] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.                                    
[   11.082672] lp: driver loaded but no devices found                                                                 
[   11.174724] Adding 497972k swap on /dev/sda1.  Priority:-1 extents:1 across:497972k                                
[   11.722286] EXT4 FS on sda5, internal journal on sda5:8                                                            
[   12.664529] EXT4-fs: barriers enabled                                                                              
[   12.664775] kjournald2 starting.  Commit interval 5 seconds                                                        
[   12.665058] EXT4 FS on sda6, internal journal on sda6:8                                                            
[   12.665061] EXT4-fs: delayed allocation enabled                                                                    
[   12.665063] EXT4-fs: file extents enabled                                                                          
[   12.676954] EXT4-fs: mballoc enabled                                                                               
[   12.676960] EXT4-fs: mounted filesystem with ordered data mode.                                                    
[   13.089107] type=1505 audit(1239091300.536:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1913                                                                                                            
[   13.089266] type=1505 audit(1239091300.536:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1913                                                                                                                  
[   13.089324] type=1505 audit(1239091300.536:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1913                                                                                    
[   13.089375] type=1505 audit(1239091300.536:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1913                                                                                         
[   13.269738] type=1505 audit(1239091300.717:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1918                                                                                                   
[   13.269973] type=1505 audit(1239091300.717:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1918                                                                                                                  
[   13.316203] type=1505 audit(1239091300.764:8): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=1922
[   13.359074] type=1505 audit(1239091300.804:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1926
[   14.161345] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.535668] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.535673] Bluetooth: BNEP filters: protocol multicast
[   16.575681] Bridge firewalling registered
[   17.823616] ppdev: user-space parallel port driver
[   20.392171] [drm] Initialized drm 1.1.0 20060810
[   20.411196] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.411203] pci 0000:00:02.0: setting latency timer to 64
[   20.411411] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   20.414986] [drm:i915_setparam] *ERROR* unknown parameter 4
[   20.415018] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   21.570275] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.573145] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   21.580412] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.827534] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   31.664045] eth0: no IPv6 routers present
[  955.321193] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

```
lsmod | grep ath
ath5k                 126724  0
lbm_cw_mac80211       227364  1 ath5k
lbm_cw_cfg80211        73760  2 ath5k,lbm_cw_mac80211
led_class              12036  1 ath5k

---

### Post by nowardev on 2009-04-20
SOLVED

ath5k sucks with network manager i don't know and don't want know.
i have installed madwifi but not the 0.9.4 standard because i get this error

ieee80211_power.c:240: error: implicit declaration of function '__skb_append'



**YOU HAVE TO USE SVN **

anyway what i done here works with wpa2-psk 

```
svn checkout [http://svn.madwifi-project.org/madwifi/trunk](http://svn.madwifi-project.org/madwifi/trunk) madwifi ; cd madwifi ; make
```

then if you have not get error... 

```
sudo make install
```

today i have installed from zero and it works with ath5k 

OMG

---

