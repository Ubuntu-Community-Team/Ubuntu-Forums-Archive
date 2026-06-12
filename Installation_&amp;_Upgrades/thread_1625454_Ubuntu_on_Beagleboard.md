---
title: "Ubuntu on Beagleboard"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by nkrishna on 2010-11-19
First off, Hi all. I am new to Ubuntu Forums. Sorry if this has been asked before, but I am unable to get a display on my TV, nor am I able to get a command prompt on the serial port :-) Help please...

Texas Instruments X-Loader 1.4.4ss (Sep 22 2010 - 16:12:19)
Beagle Rev Ax/Bx
Reading boot sector
Loading u-boot.bin from mmc


U-Boot 2010.03-dirty (Oct 18 2010 - 11:31:58)

OMAP3530-GP ES2.1, CPU-OPP2, L3-165MHz, Max clock-600Mhz
OMAP3 Beagle board + LPDDR/NAND
I2C:   ready
DRAM:  128 MB
NAND:  256 MiB
*** Warning - bad CRC or NAND, using default environment

In:    serial
Out:   serial
Err:   serial

Probing for expansion boards, if none are connected you'll see a harmless I2C e.

timed out in wait_for_bb: I2C_STAT=1000                                         
timed out in wait_for_pin: I2C_STAT=0                                           
I2C read: I/O error                                                             
Unrecognized expansion board: 0                                                 
Beagle Rev Ax/Bx                                                                
Die ID #1364000200000000040316e80701601c                                        
Hit any key to stop autoboot:  0                                                
mmc1 is available                                                               
The user button is currently NOT pressed.                                       
reading boot.scr                                                                
                                                                                
679 bytes read                                                                  
Running bootscript from mmc ...                                                 
## Executing script at 80200000                                                 
Debug: Demo Image Install                                                       
mmc1 is available                                                               
reading uImage                                                                  
                                                                                
4098772 bytes read                                                              
reading uInitrd                                                                 
                                                                                
4215860 bytes read                                                              
## Booting kernel from Legacy Image at 80300000 ...                             
   Image Name:   2.6.35.8-l7                                                    
   Image Type:   ARM Linux Kernel Image (uncompressed)                          
   Data Size:    4098708 Bytes =  3.9 MB                                        
   Load Address: 80008000                                                       
   Entry Point:  80008000                                                       
   Verifying Checksum ... OK                                                    
## Loading init Ramdisk from Legacy Image at 81600000 ...                       
   Image Name:   initramfs                                                      
   Image Type:   ARM Linux RAMDisk Image (uncompressed)                         
   Data Size:    4215796 Bytes =  4 MB                                          
   Load Address: 00000000                                                       
   Entry Point:  00000000                                                       
   Verifying Checksum ... OK                                                    
   Loading Kernel Image ... OK                                                  
OK                                                                              
                                                                                
Starting kernel ...                                                             
                                                                                
Uncompressing Linux... done, booting the kernel.                                
[    0.000000] Initializing cgroup subsys cpuset                                
[    0.000000] Initializing cgroup subsys cpu                                   
[    0.000000] Linux version 2.6.35.8-l7 (root@beagle-256mb-0) (gcc version 4.40
[    0.000000] CPU: ARMv7 Processor [411fc082] revision 2 (ARMv7), cr=10c53c7f  
[    0.000000] CPU: VIPT nonaliasing data cache, VIPT nonaliasing instruction ce
[    0.000000] Machine: OMAP3 Beagle Board                                      
[    0.000000] Beagle expansionboard: unknown                                   
[    0.000000] Memory policy: ECC disabled, Data cache writeback                
[    0.000000] OMAP3430/3530 ES2.1 (l2cache iva sgx neon isp )                  
[    0.000000] SRAM: Mapped pa 0x40200000 to va 0xfe400000 size: 0x100000       
[    0.000000] Reserving 12582912 bytes SDRAM for VRAM                          
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pa2
[    0.000000] Kernel command line: console=ttyS2,115200n8 console=tty0 root=/d0
[    0.000000] PID hash table entries: 512 (order: -1, 2048 bytes)              
[    0.000000] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)   
[    0.000000] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)     
[    0.000000] allocated 655360 bytes of page_cgroup                            
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memos
[    0.000000] Memory: 128MB = 128MB total                                      
[    0.000000] Memory: 97452k/97452k available, 33620k reserved, 0K highmem     
[    0.000000] Virtual kernel memory layout:                                    
[    0.000000]     vector  : 0xffff0000 - 0xffff1000   (   4 kB)                
[    0.000000]     fixmap  : 0xfff00000 - 0xfffe0000   ( 896 kB)                
[    0.000000]     DMA     : 0xffc00000 - 0xffe00000   (   2 MB)                
[    0.000000]     vmalloc : 0xc8800000 - 0xf8000000   ( 760 MB)                
[    0.000000]     lowmem  : 0xc0000000 - 0xc8000000   ( 128 MB)                
[    0.000000]     modules : 0xbf000000 - 0xc0000000   (  16 MB)                
[    0.000000]       .init : 0xc0008000 - 0xc0049000   ( 260 kB)                
[    0.000000]       .text : 0xc0049000 - 0xc078f000   (7448 kB)                
[    0.000000]       .data : 0xc07fe000 - 0xc085d8c0   ( 383 kB)                
[    0.000000] SLUB: Genslabs=9, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, N1
[    0.000000] Hierarchical RCU implementation.                                 
[    0.000000]  RCU-based detection of stalled CPUs is disabled.                
[    0.000000]  Verbose stalled-CPUs detection is disabled.                     
[    0.000000] NR_IRQS:402                                                      
[    0.000000] Clocking rate (Crystal/Core/MPU): 26.0/332/500 MHz               
[    0.000000] omap_hwmod: l3_hwmod: cannot be enabled (3)                      
[    0.000000] omap_hwmod: l4_core_hwmod: cannot be enabled (3)                 
[    0.000000] omap_hwmod: l4_per_hwmod: cannot be enabled (3)                  
[    0.000000] omap_hwmod: l4_wkup_hwmod: cannot be enabled (3)                 
[    0.000000] Reprogramming SDRC clock to 332000000 Hz                         
[    0.000000] GPMC revision 5.0                                                
[    0.000000] IRQ: Found an INTC at 0xfa200000 (revision 4.0) with 96 interrups
[    0.000000] Total of 96 interrupts on 1 active controller                    
[    0.000000] OMAP GPIO hardware version 2.5                                   
[    0.000000] OMAP clockevent source: GPTIMER12 at 32768 Hz                    
[    0.000000] Console: colour dummy device 80x30                               
[    0.000000] console [tty0] enabled                                           
[    0.000000] Calibrating delay loop... 471.61 BogoMIPS (lpj=1843200)          
[    0.000000] pid_max: default: 32768 minimum: 301                             
[    0.000000] Security Framework initialized                                   
[    0.000000] Smack:  Initializing.                                            
[    0.000000] Mount-cache hash table entries: 512                              
[    0.000000] Initializing cgroup subsys ns                                    
[    0.000000] Initializing cgroup subsys cpuacct                               
[    0.000000] Initializing cgroup subsys memory                                
[    0.000000] Initializing cgroup subsys devices                               
[    0.000000] Initializing cgroup subsys freezer                               
[    0.000000] CPU: Testing write buffer coherency: ok                          
[    0.000000] devtmpfs: initialized                                            
[    0.000000] regulator: core version 0.5                                      
[    0.000000] NET: Registered protocol family 16                               
[    0.000000] OMAP3 Beagle Rev: Ax/Bx                                          
[    0.000000] Found NAND on CS0                                                
[    0.000000] hw perfevents: enabled with ARMv7 Cortex-A8 PMU driver, 5 countee
[    0.000000] Switched to new clocking rate (Crystal/Core/MPU): 26.0/600/332 Mz
[    0.000213] OMAP DMA hardware revision 4.0                                   
[    0.000610] omap-mcpdm omap-mcpdm: unable to get pdm_ck: -2                  
[    0.000701] omap-mcpdm: probe of omap-mcpdm failed with error -2             
[    0.006225] bio: create slab <bio-0> at 0                                    
[    0.007415] SCSI subsystem initialized                                       
[    0.008666] usbcore: registered new interface driver usbfs                   
[    0.008789] usbcore: registered new interface driver hub                     
[    0.009063] usbcore: registered new device driver usb                        
[    0.009460] i2c_omap i2c_omap.1: bus 1 rev3.12 at 2600 kHz                   
[    0.012207] twl4030: PIH (irq 7) chaining IRQs 368..375                      
[    0.012298] twl4030: power (irq 373) chaining IRQs 376..383                  
[    0.012786] twl4030: gpio (irq 368) chaining IRQs 384..401                   
[    0.016296] regulator: VUSB1V5: 1500 mV normal standby                       
[    0.016632] regulator: VUSB1V8: 1800 mV normal standby                       
[    0.016998] regulator: VUSB3V1: 3100 mV normal standby                       
[    0.018524] twl4030_usb twl4030_usb: Initialized TWL4030 USB module          
[    0.019165] regulator: VMMC1: 1850 <--> 3150 mV at 3000 mV normal standby    
[    0.019531] regulator: VDAC: 1800 mV normal standby                          
[    0.019927] regulator: VPLL2: 1800 mV normal standby                         
[    0.020416] regulator: VSIM: 1800 <--> 3000 mV at 1800 mV normal standby     
[    0.020690] i2c_omap i2c_omap.2: bus 2 rev3.12 at 400 kHz                    
[    0.029357] i2c_omap i2c_omap.3: bus 3 rev3.12 at 100 kHz                    
[    0.030303] Advanced Linux Sound Architecture Driver Version 1.0.23.         
[    0.030883] NetLabel: Initializing                                           
[    0.030914] NetLabel:  domain hash size = 128                                
[    0.030944] NetLabel:  protocols = UNLABELED CIPSOv4                         
[    0.031036] NetLabel:  unlabeled traffic allowed by default                  
[    0.031127] Switching to clocksource 32k_counter                             
[    0.054840] musb_hdrc: version 6.0, musb-dma, otg (peripheral+host), debug=0 
[    0.060424] musb_hdrc musb_hdrc: USB OTG mode controller at fa0ab000 using D2
[    0.060821] NET: Registered protocol family 2                                
[    0.061126] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)   
[    0.062072] TCP established hash table entries: 4096 (order: 3, 32768 bytes) 
[    0.062225] TCP bind hash table entries: 4096 (order: 2, 16384 bytes)        
[    0.062316] TCP: Hash tables configured (established 4096 bind 4096)         
[    0.062347] TCP reno registered                                              
[    0.062377] UDP hash table entries: 256 (order: 0, 4096 bytes)               
[    0.062530] UDP-Lite hash table entries: 256 (order: 0, 4096 bytes)          
[    0.062805] NET: Registered protocol family 1                                
[    0.063293] RPC: Registered udp transport module.                            
[    0.063354] RPC: Registered tcp transport module.                            
[    0.063385] RPC: Registered tcp NFSv4.1 backchannel transport module.        
[    0.063720] Trying to unpack rootfs image as initramfs...                    
[    0.507812] Freeing initrd memory: 4116K                                     
[    0.508819] PMU: registered new PMU device of type 0                         
[    0.508941] dspbridge_init: 600000 bytes @ 82700000                          
[    0.509582] audit: initializing netlink socket (disabled)                    
[    0.509704] type=2000 audit(0.890:1): initialized                            
[    0.660430] VFS: Disk quotas dquot_6.5.2                                     
[    0.660858] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)       
[    0.666595] fuse init (API version 7.14)                                     
[    0.668518] Btrfs loaded                                                     
[    0.668579] msgmni has been set to 198                                       
[    0.670898] alg: No test for stdrng (krng)                                   
[    0.671417] Block layer SCSI generic (bsg) driver version 0.4 loaded (major )
[    0.671508] io scheduler noop registered                                     
[    0.671539] io scheduler deadline registered                                 
[    0.671691] io scheduler cfq registered (default)                            
[    0.734527] OMAP DSS rev 2.0                                                 
[    0.734649] OMAP DISPC rev 3.0                                               
[    0.734710] OMAP VENC rev 2                                                  
[    1.063507] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled          
[    1.083892] serial8250.0: ttyS0 at MMIO 0x4806a000 (irq = 72) is a ST16654   
[    1.103424] serial8250.1: ttyS1 at MMIO 0x4806c000 (irq = 73) is a ST16654   
[    1.122955] serial8250.2: ttyS2 at MMIO 0x49020000 (irq = 74) is a ST16654   
[    1.828094] console [ttyS2] enabled                                          
[    1.839385] brd: module loaded                                               
[    1.846343] loop: module loaded                                              
[    1.852539] omap2-nand driver initializing                                   
[    1.856994] NAND device: Manufacturer ID: 0x2c, Chip ID: 0xba (Micron NAND 2)
[    1.865783] Creating 5 MTD partitions on "omap2-nand.0":                     
[    1.871215] 0x000000000000-0x000000080000 : "X-Loader"                       
[    1.878082] 0x000000080000-0x000000260000 : "U-Boot"                         
[    1.885131] 0x000000260000-0x000000280000 : "U-Boot Env"                     
[    1.891784] 0x000000280000-0x000000680000 : "Kernel"                         
[    1.899627] 0x000000680000-0x000010000000 : "File System"                    
[    2.004486] OneNAND driver initializing                                      
[    2.008911] usbcore: registered new interface driver cdc_ether               
[    2.014892] usbcore: registered new interface driver rndis_host              
[    2.021514] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver       
[    2.028472] ehci-omap ehci-omap.0: OMAP-EHCI Host Controller                 
[    2.034545] ehci-omap ehci-omap.0: new USB bus registered, assigned bus numb1
[    2.042236] ehci-omap ehci-omap.0: irq 77, io mem 0x48064800                 
[    2.062591] ehci-omap ehci-omap.0: USB 2.0 started, EHCI 1.00                
[    2.069274] hub 1-0:1.0: USB hub found                                       
[    2.073150] hub 1-0:1.0: 3 ports detected                                    
[    2.101745] Initializing USB Mass Storage driver...                          
[    2.106811] usbcore: registered new interface driver usb-storage             
[    2.112945] USB Mass Storage support registered.                             
[    2.117706] g_ether gadget: using random self ethernet address               
[    2.123596] g_ether gadget: using random host ethernet address               
[    2.130645] usb0: MAC 26:33:a3:ac:1d:06                                      
[    2.134582] usb0: HOST MAC fa:6e:40:bb:d0:2d                                 
[    2.138946] g_ether gadget: Ethernet Gadget, version: Memorial Day 2008      
[    2.145690] g_ether gadget: g_ether ready                                    
[    2.149780] musb_hdrc musb_hdrc: MUSB HDRC host driver                       
[    2.155364] musb_hdrc musb_hdrc: new USB bus registered, assigned bus number2
[    2.163482] hub 2-0:1.0: USB hub found                                       
[    2.167358] hub 2-0:1.0: 1 port detected                                     
[    2.172058] mice: PS/2 mouse device common for all mice                      
[    2.178344] input: twl4030_pwrbutton as /devices/platform/i2c_omap.1/i2c-1/10
[    2.189392] i2c /dev entries driver                                          
[    2.194274] OMAP Watchdog Timer Rev 0x31: initial timeout 60 sec             
[    2.201293] device-mapper: uevent: version 1.0.3                             
[    2.207122] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-m
[    2.216217] device-mapper: multipath: version 1.1.1 loaded                   
[    2.221801] device-mapper: multipath round-robin: version 1.0.0 loaded       
[    2.229431] sdhci: Secure Digital Host Controller Interface driver           
[    2.235717] sdhci: Copyright(c) Pierre Ossman                                
[    2.243652] mmci-omap-hs: probe of mmci-omap-hs.1 failed with error -16      
[    2.254699] No device for DAI tlv320aic23                                    
[    2.319183] No device for DAI omap-mcbsp-dai-0                               
[    2.323760] No device for DAI omap-mcbsp-dai-1                               
[    2.328277] No device for DAI omap-mcbsp-dai-2                               
[    2.332763] No device for DAI omap-mcbsp-dai-3                               
[    2.337280] No device for DAI omap-mcbsp-dai-4                               
[    2.341796] No device for DAI omap-mcpdm                                     
[    2.345794] Not OMAP3 EVM!                                                   
[    2.348510] Not OMAP3517 / AM3517 EVM!                                       
[    2.352355] OMAP3 Beagle/Devkit8000 SoC init                                 
[    2.358154] asoc: twl4030 <-> omap-mcbsp-dai-0 mapping ok                    
[    2.367523] ALSA device list:                                                
[    2.370574]   #0: omap3beagle (twl4030)                                      
[    2.376190] TCP cubic registered                                             
[    2.380615] NET: Registered protocol family 10                               
[    2.386993] lo: Disabled Privacy Extensions                                  
[    2.393493] NET: Registered protocol family 17                               
[    2.398284] ThumbEE CPU extension supported.                                 
[    2.404815] Power Management for TI OMAP3.                                   
[    2.418975] VFP support v0.3: implementor 41 architecture 3 part 30 variant 1
[    2.427764] registered taskstats version 1                                   
[    2.432189] fbcvt: 1280x720@60: CVT Name - .921M9-R                          
[    2.460815] Console: switching to colour frame buffer device 160x45          
[    2.481689] regulator_init_complete: incomplete constraints, leaving VDAC on 
[    2.489410] Freeing init memory: 260K                                        
[    2.655426] udev: starting version 151                                       
[    2.914367] mmc0: new high speed SD card at address 0002                     
[    3.014892] mmcblk0: mmc0:0002 FLASH 1.87 GiB                                
[    3.050872]  mmcblk0: p1 p2                                                  
[    4.208892] EXT4-fs (mmcblk0p2): INFO: recovery required on readonly filesysm
[    4.216674] EXT4-fs (mmcblk0p2): write access will be enabled during recovery
[    5.523803] EXT4-fs (mmcblk0p2): recovery complete                           
[    5.923248] EXT4-fs (mmcblk0p2): mounted filesystem with ordered data mode. )

nothing after this, it just hangs... there are some leds blinking on the board though, but nothing else.

---

### Post by Zookalicious on 2010-11-19
Sorry I would love to help but I have absolutely no idea what a Beagleboard is :p, is there any more information you can give us about your hardware? What exactly is it you installed Ubuntu on? 

At the very least if I can't help, I can welcome you to the forums! Welcome and I hope this issue gets solved :D

---

### Post by wkulecz on 2010-11-19
This is something I'd like to do.  Where did you get the Ubuntu you installed on your Beagleboard?

If its not specific for the Beagleboard, it probably lacks an X server that will work.  Try one of the boot options to boot to a console (terminal).

---

