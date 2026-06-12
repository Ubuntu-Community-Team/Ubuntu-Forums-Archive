---
title: "Installation hung up, now I'm screwed"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by whyme2009 on 2008-11-19
I am running Ibex on my macbook right now and tried to download xubuntu-desktop, but during the download the system froze and now when I try to do anything in terminal, i get this

brent@SuperMac:~$ sudo apt-get install xubuntu-desktop
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
brent@SuperMac:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0159' near line 1:
 EOF after field name `'

---

### Post by Partyboi2 on 2008-11-20
Try removing the update
```
sudo  rm /var/lib/dpkg/updates/0159
``` then
```
 sudo dpkg --configure -a
``` then
```
sudo apt-get update 
sudo apt-get upgrade
```

---

### Post by whyme2009 on 2008-11-21
That seemed to work, but now I get this:

brent@SuperMac:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
50 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: fgets gave an empty string from `/var/lib/dpkg/triggers//File'
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by whyme2009 on 2008-11-21
I'm not too invested in this, so I will just reinstall it.  Some of the problem is probably me running it in a VM, but I can't fix that until I get a new computer...maybe soon.

---

### Post by Scelestus on 2008-12-28
Ok i am having similar problems as you. Mine started when I tried to set up grub to dual boot windows. Some how I ended up trashing my mbr. I ended up having to delete my partitions use parted to rescue them and got linux to boot back up. I don't have sound or anything. so i tried reinstalling gstreamer and I get this error 


dpkg: fgets gave an empty string from `/var/lib/dpkg/triggers//File'
E: Sub-process /usr/bin/dpkg returned an error code (2)

ive tried apt-get update
          apt-get upgrade

same error it downloaded everything i needed but when it comes to installing get the error. 

Seen in a older post to do ls -la to check triggers. this is what it shows

debian:/home/jon# ls -la /var/lib/dpkg/triggers
total 20
drwxr-xr-x 2 root root 4096 2008-12-24 23:22 .
drwxr-xr-x 7 root root 4096 2008-12-24 23:22 ..
-rw-r--r-- 1 root root  260 2008-11-26 09:32 File
-rw------- 1 root root    0 2008-12-24 23:22 Lock
-rw-r--r-- 1 root root   15 2008-11-05 15:37 pysupport
-rw-r--r-- 1 root root    0 2008-12-24 23:22 Unincorp
-rw-r--r-- 1 root root   16 2008-11-05 14:51 update-initramfs

(My Kernel)
Linux debian 2.6.26-1-686 #1 SMP Sat Nov 8 19:00:26 UTC 2008 i686 GNU/Linux

```
debian:/home/jon# dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.26-1-686 (Debian 2.6.26-10) (waldi@debian.org) (gcc version 4.1.3 20080623 (prerelease) (Debian 4.1.2-23)) #1 SMP Sat Nov 8 19:00:26 UTC 2008
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fec0000 (usable)
[    0.000000]  BIOS-e820: 000000000fec0000 - 000000000fef8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000fef8000 - 000000000ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 254MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65216) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65216
[    0.000000]   HighMem     65216 ->    65216
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65216
[    0.000000] On node 0 totalpages: 65216
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 478 pages used for memmap
[    0.000000]   Normal zone: 60642 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000FF980, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 0FEF0000, 002C (r1 GATEWA D815EPFV 20010919 MSFT     1011)
[    0.000000] ACPI: FACP 0FEF1000, 0074 (r1 GATEWA EA81510A 20010919 MSFT     1011)
[    0.000000] ACPI: DSDT 0FEE0000, 3379 (r1 GATEWA N0CPP000       22 MSFT  100000B)
[    0.000000] ACPI: FACS 0FEF8000, 0040
[    0.000000] ACPI: APIC 0FEE3379, 005A (r1 GATEWA EA81510A 20010919 MSFT     1011)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 0ff00000:efc80000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 37960 bytes of per cpu data
[    0.000000] NR_CPUS: 8, nr_cpu_ids: 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64706
[    0.000000] Kernel command line: root=/dev/hda1 ro 
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 1195.604 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] Memory: 249028k/260864k available (1768k kernel code, 11364k reserved, 752k data, 244k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
[    0.004000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.004000]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcfec0000   ( 254 MB)
[    0.004000]       .init : 0xc037f000 - 0xc03bc000   ( 244 kB)
[    0.004000]       .data : 0xc02ba30b - 0xc0376620   ( 752 kB)
[    0.004000]       .text : 0xc0100000 - 0xc02ba30b   (1768 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.084241] Calibrating delay using timer specific routine.. 2393.61 BogoMIPS (lpj=4787223)
[    0.084419] Security Framework initialized
[    0.084483] SELinux:  Disabled at boot.
[    0.084541] Capability LSM initialized
[    0.084622] Mount-cache hash table entries: 512
[    0.084970] Initializing cgroup subsys ns
[    0.085030] Initializing cgroup subsys cpuacct
[    0.085086] Initializing cgroup subsys devices
[    0.085178] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.085270] CPU: L2 cache: 256K
[    0.085327] Intel machine check architecture supported.
[    0.085385] Intel machine check reporting enabled on CPU#0.
[    0.085463] Checking 'hlt' instruction... OK.
[    0.100642] SMP alternatives: switching to UP code
[    0.109012] Freeing SMP alternatives: 16k freed
[    0.109080] ACPI: Core revision 20080321
[    0.117559] ENABLING IO-APIC IRQs
[    0.117834] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.157592] CPU0: Intel(R) Celeron(TM) CPU                1200MHz stepping 01
[    0.160010] Brought up 1 CPUs
[    0.160010] Total of 1 processors activated (2393.61 BogoMIPS).
[    0.160010] CPU0 attaching sched-domain:
[    0.160010]  domain 0: span 0
[    0.160010]   groups: 0
[    0.160010] net_namespace: 660 bytes
[    0.160010] Booting paravirtualized kernel on bare hardware
[    0.160010] NET: Registered protocol family 16
[    0.160010] ACPI: bus type pci registered
[    0.160010] PCI: PCI BIOS revision 2.10 entry at 0xfda95, last bus=1
[    0.160010] PCI: Using configuration type 1 for base access
[    0.160010] Setting up standard PCI resources
[    0.162233] ACPI: EC: Look up EC in DSDT
[    0.171157] ACPI: Interpreter enabled
[    0.171225] ACPI: (supports S0 S1 S4 S5)
[    0.171446] ACPI: Using IOAPIC for interrupt routing
[    0.179603] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.180000] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.180098] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH4 GPIO
[    0.180606] PCI: Transparent bridge - 0000:00:1e.0
[    0.180697] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.180977] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.184384] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12)
[    0.185024] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12)
[    0.185648] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[    0.186355] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12)
[    0.186980] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12)
[    0.187606] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12)
[    0.188244] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[    0.188952] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12)
[    0.189631] ACPI: Power Resource [FDDP] (off)
[    0.189742] ACPI: Power Resource [URP1] (off)
[    0.189850] ACPI: Power Resource [LPTP] (off)
[    0.190044] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.190164] pnp: PnP ACPI init
[    0.190234] ACPI: bus type pnp registered
[    0.197684] pnp: PnP ACPI: found 12 devices
[    0.197752] ACPI: ACPI bus type pnp unregistered
[    0.197812] PnPBIOS: Disabled by ACPI PNP
[    0.198440] PCI: Using ACPI for IRQ routing
[    0.198888] ACPI: RTC can wake from S4
[    0.199024] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.199086] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.199146] system 00:0b: iomem range 0x100000-0xfefffff could not be reserved
[    0.199215] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.199275] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.230215] PCI: Bridge: 0000:00:1e.0
[    0.230275]   IO window: d000-dfff
[    0.230332]   MEM window: 0xfa900000-0xfe9fffff
[    0.230389]   PREFETCH window: 0x00000000ee700000-0x00000000f27fffff
[    0.230464] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.230526] NET: Registered protocol family 2
[    0.230774] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.231272] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.231515] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.231754] TCP: Hash tables configured (established 8192 bind 8192)
[    0.231813] TCP reno registered
[    0.232143] NET: Registered protocol family 1
[    0.232463] checking if image is initramfs... it is
[    0.732106] Switched to high resolution mode on CPU 0
[    1.270425] Freeing initrd memory: 5809k freed
[    1.272216] audit: initializing netlink socket (disabled)
[    1.272317] type=2000 audit(1230513830.272:1): initialized
[    1.272630] Total HugeTLB memory allocated, 0
[    1.272866] VFS: Disk quotas dquot_6.5.1
[    1.272986] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.273138] msgmni has been set to 497
[    1.273508] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.273581] io scheduler noop registered
[    1.273634] io scheduler anticipatory registered
[    1.273688] io scheduler deadline registered
[    1.273768] io scheduler cfq registered (default)
[    1.273923] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[    1.274002] pci 0000:01:09.0: Boot video device
[    1.274721] isapnp: Scanning for PnP cards...
[    1.631978] isapnp: No Plug & Play device found
[    1.637693] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.637965] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.638834] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.642114] brd: module loaded
[    1.642412] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.645517] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.645587] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.645972] mice: PS/2 mouse device common for all mice
[    1.646300] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.646381] rtc0: alarms up to one month
[    1.646511] cpuidle: using governor ladder
[    1.646566] cpuidle: using governor menu
[    1.646625] No iBFT detected.
[    1.647605] TCP cubic registered
[    1.647662] NET: Registered protocol family 17
[    1.647726] Using IPI No-Shortcut mode
[    1.648165] registered taskstats version 1
[    1.648459] rtc_cmos 00:02: setting system clock to 2008-12-29 01:23:51 UTC (1230513831)
[    1.649194] Freeing unused kernel memory: 244k freed
[    1.673354] input: AT Translated Set 2 keyboard as /class/input/input0
[    1.867464] ACPI: ACPI0007:00 is registered as cooling_device0
[    2.975883] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    2.975956] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.976126] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[    2.999971] e100: eth0: e100_probe: addr 0xfe9ef000, irq 20, MAC addr 00:03:47:d2:3e:1e
[    3.050939] No dock devices found.
[    3.168584] SCSI subsystem initialized
[    3.187127] usbcore: registered new interface driver usbfs
[    3.187251] usbcore: registered new interface driver hub
[    3.187368] usbcore: registered new device driver usb
[    3.195365] USB Universal Host Controller Interface driver v3.0
[    3.195548] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 19
[    3.195669] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.195677] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    3.195946] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    3.196106] uhci_hcd 0000:00:1f.2: irq 19, io base 0x0000ef40
[    3.196360] usb usb1: configuration #1 chosen from 1 choice
[    3.196473] hub 1-0:1.0: USB hub found
[    3.196543] hub 1-0:1.0: 2 ports detected
[    3.300330] usb usb1: New USB device found, idVendor=1d6b, idProduct=0001
[    3.300403] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.300471] usb usb1: Product: UHCI Host Controller
[    3.300526] usb usb1: Manufacturer: Linux 2.6.26-1-686 uhci_hcd
[    3.300582] usb usb1: SerialNumber: 0000:00:1f.2
[    3.300693] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 23
[    3.300813] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[    3.300820] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[    3.300918] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[    3.301032] uhci_hcd 0000:00:1f.4: irq 23, io base 0x0000ef80
[    3.301266] usb usb2: configuration #1 chosen from 1 choice
[    3.301381] hub 2-0:1.0: USB hub found
[    3.301450] hub 2-0:1.0: 2 ports detected
[    3.328438] libata version 3.00 loaded.
[    3.371443] Floppy drive(s): fd0 is 1.44M
[    3.392975] FDC 0 is a post-1991 82077
[    3.404498] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    3.404571] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.404638] usb usb2: Product: UHCI Host Controller
[    3.404693] usb usb2: Manufacturer: Linux 2.6.26-1-686 uhci_hcd
[    3.404750] usb usb2: SerialNumber: 0000:00:1f.4
[    3.423712] Uniform Multi-Platform E-IDE driver
[    3.423787] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    3.425659] ICH2: IDE controller (0x8086:0x244b rev 0x05) at  PCI slot 0000:00:1f.1
[    3.425765] ICH2: not 100% native mode: will probe irqs later
[    3.425839]     ide0: BM-DMA at 0xffa0-0xffa7
[    3.425902]     ide1: BM-DMA at 0xffa8-0xffaf
[    3.425961] Probing IDE interface ide0...
[    3.644114] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    3.712159] hda: ST3120026A, ATA DISK drive
[    3.792004] usb 2-2: configuration #1 chosen from 1 choice
[    3.801210] hub 2-2:1.0: USB hub found
[    3.803097] hub 2-2:1.0: 4 ports detected
[    3.912270] usb 2-2: New USB device found, idVendor=8086, idProduct=1121
[    3.912342] usb 2-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    4.384120] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    4.384377] hda: UDMA/100 mode selected
[    4.384693] Probing IDE interface ide1...
[    5.120148] hdc: HP DVD Writer 840x, ATAPI CD/DVD-ROM drive
[    5.904144] hdd: HL-DT-ST GCE-8160B, ATAPI CD/DVD-ROM drive
[    5.960102] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    5.960353] hdc: UDMA/33 mode selected
[    5.960655] hdd: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    5.980361] hdd: MWDMA2 mode selected
[    6.000185] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    6.003995] ide1 at 0x170-0x177,0x376 on irq 15
[    6.096361] hda: max request size: 512KiB
[    6.099673] hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63
[    6.100546] hda: cache flushes supported
[    6.100704]  hda: hda1
[    6.128466] hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[    6.128761] Uniform CD-ROM driver Revision: 3.20
[    6.132927] hdd: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache
[    6.349913] kjournald starting.  Commit interval 5 seconds
[    6.349913] EXT3-fs: mounted filesystem with ordered data mode.
[    8.340711] udevd version 125 started
[   10.143328] Linux agpgart interface v0.103
[   10.180853] agpgart: Detected an Intel i815 Chipset.
[   10.185814] agpgart: detected 4MB dedicated video ram.
[   10.200869] agpgart: AGP aperture is 64M @ 0xf4000000
[   10.277934] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.285865] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.309228] intel_rng: Firmware space is locked read-only. If you can't or
[   10.309233] intel_rng: don't want to disable this in firmware setup, and if
[   10.309237] intel_rng: you are certain that your system has a functional
[   10.309240] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   10.370198] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   10.370376] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   10.370456] iTCO_wdt: No card detected
[   10.478382] input: Power Button (FF) as /class/input/input1
[   10.504189] ACPI: Power Button (FF) [PWRF]
[   10.504390] input: Power Button (CM) as /class/input/input2
[   10.536207] ACPI: Power Button (CM) [PBTN]
[   10.545750] ACPI: PCI Interrupt 0000:00:1f.3[B] -> GSI 17 (level, low) -> IRQ 17
[   11.737790] input: PC Speaker as /class/input/input3
[   12.452022] input: ImPS/2 Generic Wheel Mouse as /class/input/input4
[   12.478300] parport_pc 00:09: reported by Plug and Play ACPI
[   12.478418] parport0: PC-style at 0x378 (0x778), irq 7 [PCSPP,TRISTATE]
[   14.014612] EXT3 FS on hda1, internal journal
[   14.482651] loop: module loaded
[   14.768149] smsc47m1: Found SMSC LPC47M14x
[   17.056140] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   19.901072] lp0: using parport0 (interrupt-driven).
[   19.926399] ppdev: user-space parallel port driver
[   23.602094] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   23.929826] NET: Registered protocol family 10
[   23.930818] lo: Disabled Privacy Extensions
[   28.204004] [drm] Initialized drm 1.1.0 20060810
[   28.212968] ACPI: PCI Interrupt 0000:01:09.0[A] -> GSI 21 (level, low) -> IRQ 21
[   28.212968] PCI: Setting latency timer of device 0000:01:09.0 to 64
[   28.212968] [drm] Initialized tdfx 1.0.0 20010216 on minor 0
[   41.508024] eth0: no IPv6 routers present


and lsmod

debian:/home/jon# lsmod
Module                  Size  Used by
tdfx                    2240  2 
drm                    65256  3 tdfx
ipv6                  235300  12 
ppdev                   6468  0 
lp                      8164  0 
cpufreq_ondemand        6476  0 
cpufreq_powersave       1856  0 
cpufreq_userspace       3172  0 
cpufreq_conservative     5960  0 
cpufreq_stats           3776  0 
freq_table              4224  2 cpufreq_ondemand,cpufreq_stats
smsc47m1                8168  0 
adm1025                10292  0 
hwmon_vid               2720  1 adm1025
loop                   12748  0 
parport_pc             22500  1 
parport                30988  3 ppdev,lp,parport_pc
serio_raw               4740  0 
psmouse                32336  0 
pcspkr                  2432  0 
i2c_i801                7920  0 
i2c_core               19828  2 adm1025,i2c_i801
button                  6064  0 
iTCO_wdt                9508  0 
rng_core                3940  0 
shpchp                 25528  0 
pci_hotplug            23460  1 shpchp
intel_agp              22332  1 
agpgart                28776  2 drm,intel_agp
evdev                   8000  3 
ext3                  105416  1 
jbd                    39444  1 ext3
mbcache                 7108  1 ext3
ide_cd_mod             27652  0 
cdrom                  30176  1 ide_cd_mod
ide_disk               10496  2 
ide_pci_generic         3908  0 [permanent]
piix                    6568  0 [permanent]
ide_core               96168  4 ide_cd_mod,ide_disk,ide_pci_generic,piix
floppy                 47716  0 
ata_generic             4676  0 
libata                140384  1 ata_generic
uhci_hcd               18672  0 
usbcore               118160  2 uhci_hcd
scsi_mod              129356  1 libata
dock                    8272  1 libata
e100                   28908  0 
mii                     4896  1 e100
thermal                15228  0 
processor              32576  1 thermal
fan                     4164  0 
thermal_sys            10856  3 thermal,processor,fan
debian:/home/jon# 

```


Any help on how to fix this would be appreciated. I have googled myself to death.

---

### Post by Scelestus on 2008-12-29
bump

---

