---
title: "Installation @ NXP imx6"
date: 2016-11-04
forum: Installation &amp; Upgrades
---

### Post by erik013 on 2016-11-04
Dears,

I'm trying to install Ubuntu core ([http://cdimage.ubuntu.com/ubuntu-base/releases/14.04/release/ubuntu-base-14.04.4-core-armhf.tar.gz](http://cdimage.ubuntu.com/ubuntu-base/releases/14.04/release/ubuntu-base-14.04.4-core-armhf.tar.gz) ) onto imx6qp microprocessor and I'm following this procedure [https://community.nxp.com/docs/DOC-330147](https://community.nxp.com/docs/DOC-330147). The system can start booting but it hangs on 

         * Stopping save kernel messages [ OK ]

and unfortunately it can't have HDMI display output (mxc_hdmi 20e0000.hdmi_video: Error only one HDMI output support now!). 
Here is my console log: I would very appreciate if can help me to get Ubuntu core running ... 

```
U-Boot 2016.03 (Nov 03 2016 - 21:38:02 +0100)
CPU: Freescale i.MX6QP rev1.0 996 MHz (running at 792 MHz)
CPU: Automotive temperature grade (-40C to 125C) at 36C
Reset cause: POR
Board: MX6Q-Sabreauto revA
I2C: ready
DRAM: 2 GiB
PMIC: PFUZE100 ID=0x10
NAND: 0 MiB
MMC: FSL_SDHC: 0, FSL_SDHC: 1
No panel detected: default to Hannstar-XGA
Display: Hannstar-XGA (1024x768)
In: serial
Out: serial
Err: serial
switch to partitions #0, OK
mmc1 is current device
Net: FEC [PRIME]
Normal Boot
Hit any key to stop autoboot: 0
=> setenv mmcargs $mmcargs video=mxcfb0:dev=hdmi,1920x1080M@60,if=RGB24
=> saveenv
Saving Environment to MMC...
Writing to MMC(1)... done
=> boot
switch to partitions #0, OK
mmc1 is current device
reading boot.scr
** Unable to read file boot.scr **
reading zImage
6637656 bytes read in 328 ms (19.3 MiB/s)
Booting from mmc ...
reading imx6qp-sabreauto.dtb
48853 bytes read in 21 ms (2.2 MiB/s)
Kernel image @ 0x12000000 [ 0x000000 - 0x654858 ]
## Flattened Device Tree blob at 18000000
 Booting using the fdt blob at 0x18000000
 Using Device Tree in place at 18000000, end 1800eed4
Starting kernel ...
Booting Linux on physical CPU 0x0
Linux version 4.1.15 (r59400@Latitude) (gcc version 4.8.5 (Linaro GCC 4.8-2015.06) ) #1 SMP PREEMPT Thu Nov 3 21:51:32 CET 2016
CPU: ARMv7 Processor [412fc09a] revision 10 (ARMv7), cr=10c53c7d
CPU: PIPT / VIPT nonaliasing data cache, VIPT aliasing instruction cache
Machine model: Freescale i.MX6 Quad Plus SABRE Automotive Board
Reserved memory: created CMA memory pool at 0x6a000000, size 320 MiB
Reserved memory: initialized node linux,cma, compatible id shared-dma-pool
Memory policy: Data cache writealloc
PERCPU: Embedded 12 pages/cpu @ee6fe000 s16960 r8192 d24000 u49152
Built 1 zonelists in Zone order, mobility grouping on. Total pages: 520720
Kernel command line: console=ttymxc3,115200 root=/dev/mmcblk2p2 rootwait rw video=mxcfb0:dev=hdmi,1920x1080M@60,if=RGB24
PID hash table entries: 4096 (order: 2, 16384 bytes)
Dentry cache hash table entries: 262144 (order: 8, 1048576 bytes)
Inode-cache hash table entries: 131072 (order: 7, 524288 bytes)
Memory:  1737928K/2097152K available (8295K kernel code, 435K rwdata, 2892K  rodata, 432K init, 450K bss, 31544K reserved, 327680K cma-reserved,  270336K highmem)
Virtual kernel memory layout:
 vector : 0xffff0000 - 0xffff1000 ( 4 kB)
 fixmap : 0xffc00000 - 0xfff00000 (3072 kB)
 vmalloc : 0xf0000000 - 0xff000000 ( 240 MB)
 lowmem : 0x80000000 - 0xef800000 (1784 MB)
 pkmap : 0x7fe00000 - 0x80000000 ( 2 MB)
 modules : 0x7f000000 - 0x7fe00000 ( 14 MB)
 .text : 0x80008000 - 0x80af51c8 (11189 kB)
 .init : 0x80af6000 - 0x80b62000 ( 432 kB)
 .data : 0x80b62000 - 0x80bcec40 ( 436 kB)
 .bss : 0x80bd1000 - 0x80c41a5c ( 451 kB)
SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Preemptible hierarchical RCU implementation.
 Additional per-CPU info printed with stalls.
NR_IRQS:16 nr_irqs:16 16
L2C-310 erratum 769419 enabled
L2C-310 enabling early BRESP for Cortex-A9
L2C-310 full line of zeros enabled for Cortex-A9
L2C-310 ID prefetch enabled, offset 16 lines
L2C-310 dynamic clock gating enabled, standby mode enabled
L2C-310 cache controller enabled, 16 ways, 1024 kB
L2C-310: CACHE_ID 0x410000c8, AUX_CTRL 0x76470001
mxc_clocksource_init 3000000
Switching to timer-based delay loop, resolution 333ns
sched_clock: 32 bits at 3000kHz, resolution 333ns, wraps every 715827882841ns
clocksource mxc_timer1: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 637086815595 ns
Console: colour dummy device 80x30
Calibrating delay loop (skipped), value calculated using timer frequency.. 6.00 BogoMIPS (lpj=30000)
pid_max: default: 32768 minimum: 301
Mount-cache hash table entries: 4096 (order: 2, 16384 bytes)
Mountpoint-cache hash table entries: 4096 (order: 2, 16384 bytes)
CPU: Testing write buffer coherency: ok
CPU0: thread -1, cpu 0, socket 0, mpidr 80000000
Setting up static identity map for 0x10008280 - 0x100082d8
CPU1: thread -1, cpu 1, socket 0, mpidr 80000001
CPU2: thread -1, cpu 2, socket 0, mpidr 80000002
CPU3: thread -1, cpu 3, socket 0, mpidr 80000003
Brought up 4 CPUs
SMP: Total of 4 processors activated (24.00 BogoMIPS).
CPU: All CPU(s) started in SVC mode.
devtmpfs: initialized
VFP support v0.3: implementor 41 architecture 3 part 30 variant 9 rev 4
clocksource jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 19112604462750000 ns
pinctrl core: initialized pinctrl subsystem
NET: Registered protocol family 16
DMA: preallocated 256 KiB pool for atomic coherent allocations
cpuidle: using governor ladder
cpuidle: using governor menu
CPU identified as i.MX6QP, silicon rev 1.0
hw-breakpoint: found 5 (+1 reserved) breakpoint and 1 watchpoint registers.
hw-breakpoint: maximum watchpoint size is 4 bytes.
imx6q-pinctrl 20e0000.iomuxc: no groups defined in /soc/aips-bus@02000000/iomuxc@020e0000/hdmicecgrp
imx6q-pinctrl 20e0000.iomuxc: initialized IMX pinctrl driver
imx-gpc 20dc000.gpc: no fsl,ldo-bypass found!
mxs-dma 110000.dma-apbh: initialized
SCSI subsystem initialized
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
2000000.aips-bus:usbphy_nop1 supply vcc not found, using dummy regulator
2000000.aips-bus:usbphy_nop2 supply vcc not found, using dummy regulator
i2c i2c-1: IMX I2C adapter registered
i2c i2c-1: can't use DMA
i2c i2c-2: IMX I2C adapter registered
i2c i2c-2: can't use DMA
Linux video capture interface: v2.00
pps_core: LinuxPPS API ver. 1 registered
pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <[EMAIL="giometti@linux.it"]giometti@linux.it[/EMAIL]>
PTP clock support registered
imx-ipuv3 2400000.ipu: IPU DMFC NORMAL mode: 1(0~1), 5B(4,5), 5F(6,7)
imx-ipuv3 2800000.ipu: IPU DMFC NORMAL mode: 1(0~1), 5B(4,5), 5F(6,7)
imx-prg 21cc000.prg: driver probed
imx-prg 21cd000.prg: driver probed
imx-pre 21c8000.pre: driver probed
imx-pre 21c9000.pre: driver probed
imx-pre 21ca000.pre: driver probed
imx-pre 21cb000.pre: driver probed
MIPI CSI2 driver module loaded
Advanced Linux Sound Architecture Driver Initialized.
Bluetooth: Core ver 2.20
NET: Registered protocol family 31
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
Bluetooth: L2CAP socket layer initialized
Bluetooth: SCO socket layer initialized
Switched to clocksource mxc_timer1
NET: Registered protocol family 2
TCP established hash table entries: 16384 (order: 4, 65536 bytes)
TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
TCP: Hash tables configured (established 16384 bind 16384)
UDP hash table entries: 1024 (order: 3, 32768 bytes)
UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
NET: Registered protocol family 1
RPC: Registered named UNIX socket transport module.
RPC: Registered udp transport module.
RPC: Registered tcp transport module.
RPC: Registered tcp NFSv4.1 backchannel transport module.
CPU PMU: Failed to parse /soc/pmu/interrupt-affinity[0]
hw perfevents: enabled with armv7_cortex_a9 PMU driver, 7 counters available
imx rpmsg driver is registered.
Bus freq driver module loaded
futex hash table entries: 1024 (order: 4, 65536 bytes)
VFS: Disk quotas dquot_6.6.0
VFS: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
NFS: Registering the id_resolver key type
Key type id_resolver registered
Key type id_legacy registered
jffs2: version 2.2. (NAND) © 2001-2006 Red Hat, Inc.
fuse init (API version 7.23)
bounce: pool size: 64 pages
io scheduler noop registered
io scheduler deadline registered
io scheduler cfq registered (default)
backlight supply power not found, using dummy regulator
MIPI DSI driver module loaded
MIPI DSI driver module loaded
mxc_hdmi 20e0000.hdmi_video: Detected HDMI controller 0x13:0xa:0xa0:0xc1
fbcvt: 1920x1080@60: CVT Name - 2.073M9
mxc_sdc_fb fb@0: registered mxc display driver hdmi
imx-ipuv3 2400000.ipu: IPU DMFC DP HIGH RESOLUTION: 1(0,1), 5B(2~5), 5F(6,7)
Console: switching to colour frame buffer device 240x67
mxc_hdmi 20e0000.hdmi_video: Error only one HDMI output support now!
mxc_sdc_fb fb@1: NO mxc display driver found!
mxc_sdc_fb fb@2: NO mxc display driver found!
mxc_sdc_fb fb@3: registered mxc display driver ldb
mxc_hdmi 20e0000.hdmi_video: Read EDID again
imx-sdma 20ec000.sdma: no iram assigned, using external mem
imx-sdma 20ec000.sdma: no event needs to be remapped
imx-sdma 20ec000.sdma: loaded firmware 3.3
imx-sdma 20ec000.sdma: initialized
pfuze100-regulator 1-0008: Full layer: 2, Metal layer: 1
pfuze100-regulator 1-0008: FAB: 0, FIN: 0
pfuze100-regulator 1-0008: pfuze100 found.
21ec000.serial: ttymxc2 at MMIO 0x21ec000 (irq = 298, base_baud = 5000000) is a IMX
21f0000.serial: ttymxc3 at MMIO 0x21f0000 (irq = 299, base_baud = 5000000) is a IMX
mxc_hdmi 20e0000.hdmi_video: create default modelist
console [ttymxc3] enabled
imx sema4 driver is registered.
[drm] Initialized drm 1.1.0 20060810
[drm] Initialized vivante 1.0.0 20120216 on minor 0
brd: module loaded
loop: module loaded
si476x-core 1-0063: Using default platform data.
si476x-core 1-0063: No IRQ number specified, will use polling
si476x-core 1-0063: Error while sending command 0x11
si476x-core 1-0063: The device in inconsistent power state
ahci-imx 2200000.sata: fsl,transmit-level-mV not specified, using 00000024
ahci-imx 2200000.sata: fsl,transmit-boost-mdB not specified, using 00000480
ahci-imx 2200000.sata: fsl,transmit-atten-16ths not specified, using 00002000
ahci-imx 2200000.sata: fsl,receive-eq-mdB not specified, using 05000000
ahci-imx 2200000.sata: SSS flag set, parallel bus scan disabled
ahci-imx 2200000.sata: AHCI 0001.0300 32 slots 1 ports 3 Gbps 0x1 impl platform mode
ahci-imx 2200000.sata: flags: ncq sntf stag pm led clo only pmp pio slum part ccc apst
scsi host0: ahci-imx
ata1: SATA max UDMA/133 mmio [mem 0x02200000-0x02203fff] port 0x100 irq 313
CAN device driver interface
2188000.ethernet supply phy not found, using dummy regulator
pps pps0: new PPS source ptp0
libphy: fec_enet_mii_bus: probed
fec 2188000.ethernet eth0: registered PHC device 0
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
ehci-mxc: Freescale On-Chip EHCI Host driver
usbcore: registered new interface driver usb-storage
usbcore: registered new interface driver usb_ehset_test
2184800.usbmisc supply vbus-wakeup not found, using dummy regulator
imx_usb 2184000.usb: Can't register ci_hdrc platform device, err=-517
imx_usb 2184200.usb: Can't register ci_hdrc platform device, err=-517
mousedev: PS/2 mouse device common for all mice
egalax_ts 1-0004: Failed to read firmware version
egalax_ts: probe of 1-0004 failed with error -5
2-0044 supply vdd not found, using dummy regulator
input: isl29023 light sensor as /devices/virtual/input/input1
isl29023 2-0044: driver version 1.0 enabled
snvs_rtc 20cc000.snvs:snvs-rtc-lp: rtc core: registered 20cc000.snvs:snvs-r as rtc0
i2c /dev entries driver
IR NEC protocol handler initialized
IR RC5(x/sz) protocol handler initialized
IR RC6 protocol handler initialized
IR JVC protocol handler initialized
IR Sony protocol handler initialized
IR SANYO protocol handler initialized
IR Sharp protocol handler initialized
IR MCE Keyboard/mouse protocol handler initialized
IR XMP protocol handler initialized
mxc_v4l2_output v4l2_out: V4L2 device registered as video16
mxc_v4l2_output v4l2_out: V4L2 device registered as video17
mxc_v4l2_output v4l2_out: V4L2 device registered as video18
mxc_v4l2_output v4l2_out: V4L2 device registered as video19
2-000e supply vdd not found, using dummy regulator
2-000e supply vddio not found, using dummy regulator
mag3110 2-000e: check mag3110 chip ID
input: mag3110 as /devices/virtual/input/input2
mag3110 2-000e: mag3110 is probed
2-001c supply vdd not found, using dummy regulator
2-001c supply vddio not found, using dummy regulator
input: mma845x as /devices/virtual/input/input3
imx2-wdt 20bc000.wdog: timeout 60 sec (nowayout=0)
Bluetooth: HCI UART driver ver 2.3
Bluetooth: HCI UART protocol H4 registered
Bluetooth: HCI UART protocol BCSP registered
Bluetooth: HCI UART protocol ATH3K registered
usbcore: registered new interface driver bcm203x
usbcore: registered new interface driver btusb
usbcore: registered new interface driver ath3k
sdhci: Secure Digital Host Controller Interface driver
sdhci: Copyright(c) Pierre Ossman
sdhci-pltfm: SDHCI platform and OF driver helper
/soc/aips-bus@02100000/usdhc@02190000: voltage-ranges unspecified
sdhci-esdhc-imx 2190000.usdhc: Got CD GPIO
sdhci-esdhc-imx 2190000.usdhc: No vmmc regulator found
sdhci-esdhc-imx 2190000.usdhc: No vqmmc regulator found
mmc0: SDHCI controller on 2190000.usdhc [2190000.usdhc] using ADMA
/soc/aips-bus@02100000/usdhc@02198000: voltage-ranges unspecified
sdhci-esdhc-imx 2198000.usdhc: Got CD GPIO
sdhci-esdhc-imx 2198000.usdhc: Got WP GPIO
sdhci-esdhc-imx 2198000.usdhc: No vqmmc regulator found
mmc2: SDHCI controller on 2198000.usdhc [2198000.usdhc] using ADMA
218c000.mlb supply reg_nvcc not found, using dummy regulator
mxc_mlb150 218c000.mlb: enalbe regulator
mxc_vpu 2040000.vpu_fsl: VPU initialized
mxc_vdoa 21e4000.vdoa: i.MX Video Data Order Adapter(VDOA) driver probed
imx6q-pinctrl 20e0000.iomuxc: unable to find group for node hdmicecgrp
imx6q-pinctrl 20e0000.iomuxc: unable to find group for node hdmicecgrp
mxc_hdmi_cec soc:hdmi_cec@00120000: can't get/select CEC pinctrl
Galcore version 5.0.11.41671
ata1: SATA link down (SStatus 0 SControl 300)
ahci-imx 2200000.sata: no device found, disabling link.
ahci-imx 2200000.sata: pass ahci_imx..hotplug=1 to enable hotplug
mmc2: new ultra high speed SDR104 SDHC card at address 0007
mmcblk2: mmc2:0007 SD32G 28.9 GiB
 mmcblk2: p1 p2
caam 2100000.caam: Entropy delay = 3200
caam 2100000.caam: Instantiated RNG4 SH0
caam 2100000.caam: Instantiated RNG4 SH1
caam 2100000.caam: device ID = 0x0a16010000000000 (Era -524)
caam 2100000.caam: job rings = 2, qi = 0
caam algorithms registered in /proc/crypto
caam_jr 2101000.jr0: registering rng-caam
platform caam_sm: blkkey_ex: 4 keystore units available
platform caam_sm: 64-bit clear key:
platform caam_sm: [0000] 00 01 02 03 04 0f 06 07
platform caam_sm: 64-bit black key:
platform caam_sm: [0000] 9f 9f b0 4c 0b 81 7d f4
platform caam_sm: [0008] 62 ad d4 74 25 ff 30 d0
platform caam_sm: 128-bit clear key:
platform caam_sm: [0000] 00 01 02 03 04 0f 06 07
platform caam_sm: [0008] 08 09 0a 0b 0c 0d 0e 0f
platform caam_sm: 128-bit black key:
platform caam_sm: [0000] b0 3f ee ef 84 13 ed f4
platform caam_sm: [0008] d4 87 15 b2 f7 30 ba 62
platform caam_sm: 192-bit clear key:
platform caam_sm: [0000] 00 01 02 03 04 0f 06 07
platform caam_sm: [0008] 08 09 0a 0b 0c 0d 0e 0f
platform caam_sm: [0016] 10 11 12 13 14 15 16 17
platform caam_sm: 192-bit black key:
platform caam_sm: [0000] 0b 3b 69 19 1a 3c 49 46
platform caam_sm: [0008] 23 cc dd 13 60 46 99 96
platform caam_sm: [0016] f8 ec 85 17 f2 0e 63 67
platform caam_sm: [0024] fe 63 28 f9 77 b4 f9 e0
platform caam_sm: 256-bit clear key:
platform caam_sm: [0000] 00 01 02 03 04 0f 06 07
platform caam_sm: [0008] 08 09 0a 0b 0c 0d 0e 0f
platform caam_sm: [0016] 10 11 12 13 14 15 16 17
platform caam_sm: [0024] 18 19 1a 1b 1c 1d 1e 1f
platform caam_sm: 256-bit black key:
platform caam_sm: [0000] 5b 8c 4c 3b 3b 9a 54 8a
platform caam_sm: [0008] 11 c3 70 e2 9c d6 3a 79
platform caam_sm: [0016] 6b e5 66 32 03 87 32 96
platform caam_sm: [0024] b6 9c 58 f1 0e 34 e3 62
platform caam_sm: 64-bit unwritten blob:
platform caam_sm: [0000] 00 00 00 00 00 00 00 00
platform caam_sm: [0008] 00 00 00 00 00 00 00 00
platform caam_sm: [0016] 00 00 00 00 00 00 00 00
platform caam_sm: [0024] 00 00 00 00 00 00 00 00
platform caam_sm: [0032] 00 00 00 00 00 00 00 00
platform caam_sm: [0040] 00 00 00 00 00 00 00 00
platform caam_sm: [0048] 00 00 00 00 00 00 00 00
platform caam_sm: [0056] 00 00 00 00 00 00 00 00
platform caam_sm: [0064] 00 00 00 00 00 00 00 00
platform caam_sm: [0072] 00 00 00 00 00 00 00 00
platform caam_sm: [0080] 00 00 00 00 00 00 00 00
platform caam_sm: [0088] 00 00 00 00 00 00 00 00
platform caam_sm: 128-bit unwritten blob:
platform caam_sm: [0000] 00 00 00 00 00 00 00 00
platform caam_sm: [0008] 00 00 00 00 00 00 00 00
platform caam_sm: [0016] 00 00 00 00 00 00 00 00
platform caam_sm: [0024] 00 00 00 00 00 00 00 00
platform caam_sm: [0032] 00 00 00 00 00 00 00 00
platform caam_sm: [0040] 00 00 00 00 00 00 00 00
platform caam_sm: [0048] 00 00 00 00 00 00 00 00
platform caam_sm: [0056] 00 00 00 00 00 00 00 00
platform caam_sm: [0064] 00 00 00 00 00 00 00 00
platform caam_sm: [0072] 00 00 00 00 00 00 00 00
platform caam_sm: [0080] 00 00 00 00 00 00 00 00
platform caam_sm: [0088] 00 00 00 00 00 00 00 00
platform caam_sm: 196-bit unwritten blob:
platform caam_sm: [0000] 00 00 00 00 00 00 00 00
platform caam_sm: [0008] 00 00 00 00 00 00 00 00
platform caam_sm: [0016] 00 00 00 00 00 00 00 00
platform caam_sm: [0024] 00 00 00 00 00 00 00 00
platform caam_sm: [0032] 00 00 00 00 00 00 00 00
platform caam_sm: [0040] 00 00 00 00 00 00 00 00
platform caam_sm: [0048] 00 00 00 00 00 00 00 00
platform caam_sm: [0056] 00 00 00 00 00 00 00 00
platform caam_sm: [0064] 00 00 00 00 00 00 00 00
platform caam_sm: [0072] 00 00 00 00 00 00 00 00
platform caam_sm: [0080] 00 00 00 00 00 00 00 00
platform caam_sm: [0088] 00 00 00 00 00 00 00 00
platform caam_sm: 256-bit unwritten blob:
platform caam_sm: [0000] 00 00 00 00 00 00 00 00
platform caam_sm: [0008] 00 00 00 00 00 00 00 00
platform caam_sm: [0016] 00 00 00 00 00 00 00 00
platform caam_sm: [0024] 00 00 00 00 00 00 00 00
platform caam_sm: [0032] 00 00 00 00 00 00 00 00
platform caam_sm: [0040] 00 00 00 00 00 00 00 00
platform caam_sm: [0048] 00 00 00 00 00 00 00 00
platform caam_sm: [0056] 00 00 00 00 00 00 00 00
platform caam_sm: [0064] 00 00 00 00 00 00 00 00
platform caam_sm: [0072] 00 00 00 00 00 00 00 00
platform caam_sm: [0080] 00 00 00 00 00 00 00 00
platform caam_sm: [0088] 00 00 00 00 00 00 00 00
platform caam_sm: 64-bit black key in blob:
platform caam_sm: [0000] d9 e8 1d 1e af c8 e0 55
platform caam_sm: [0008] 11 3d 1d 77 b7 b6 4b 2e
platform caam_sm: [0016] d3 96 2a 39 99 9c e3 9c
platform caam_sm: [0024] 5f 96 ea ad 56 eb fc c4
platform caam_sm: [0032] 60 fe ab 71 b8 1a 36 0b
platform caam_sm: [0040] fa 25 79 2f 66 39 76 c5
platform caam_sm: [0048] d8 07 26 62 64 1d d7 99
platform caam_sm: [0056] 00 00 00 00 00 00 00 00
platform caam_sm: [0064] 00 00 00 00 00 00 00 00
platform caam_sm: [0072] 00 00 00 00 00 00 00 00
platform caam_sm: [0080] 00 00 00 00 00 00 00 00
platform caam_sm: [0088] 00 00 00 00 00 00 00 00
platform caam_sm: 128-bit black key in blob:
platform caam_sm: [0000] f7 88 5d 9f 03 77 6b 23
platform caam_sm: [0008] c4 e2 39 5b b0 28 6e 77
platform caam_sm: [0016] 03 1d e3 a4 8c 05 8c ed
platform caam_sm: [0024] a5 e5 fc 87 93 98 04 b6
platform caam_sm: [0032] 88 64 95 a1 9e 7e 5d 40
platform caam_sm: [0040] 54 40 fb 7e b6 f3 bc dc
platform caam_sm: [0048] 58 55 41 f9 df 66 be 10
platform caam_sm: [0056] 2f e5 75 a8 a3 d3 50 b8
platform caam_sm: [0064] 00 00 00 00 00 00 00 00
platform caam_sm: [0072] 00 00 00 00 00 00 00 00
platform caam_sm: [0080] 00 00 00 00 00 00 00 00
platform caam_sm: [0088] 00 00 00 00 00 00 00 00
platform caam_sm: 192-bit black key in blob:
platform caam_sm: [0000] 7c 89 0f 97 c6 a2 29 8d
platform caam_sm: [0008] 43 49 b7 57 eb 36 02 ba
platform caam_sm: [0016] b7 81 f3 69 de ab f4 55
platform caam_sm: [0024] 34 13 3c 6c 77 0e 38 66
platform caam_sm: [0032] 2b 89 e6 5f 05 1d c9 43
platform caam_sm: [0040] 5b 27 8b fc 90 3b 5d 8e
platform caam_sm: [0048] a9 f7 ac 2f c0 2b f2 6f
platform caam_sm: [0056] ac d6 8c b2 88 52 8c 97
platform caam_sm: [0064] 66 f5 71 c1 94 38 3c 16
platform caam_sm: [0072] 00 00 00 00 00 00 00 00
platform caam_sm: [0080] 00 00 00 00 00 00 00 00
platform caam_sm: [0088] 00 00 00 00 00 00 00 00
platform caam_sm: 256-bit black key in blob:
platform caam_sm: [0000] 07 75 08 be 2b f6 c5 f3
platform caam_sm: [0008] fd ae a9 4f ea 12 7b 4b
platform caam_sm: [0016] 41 c4 43 d7 79 24 af 83
platform caam_sm: [0024] 49 6a 39 2d 94 7d 92 3d
platform caam_sm: [0032] aa 09 f6 1b a2 50 d1 c0
platform caam_sm: [0040] 2d 03 da b6 9f 76 e3 cf
platform caam_sm: [0048] 21 a9 98 b6 07 1b 18 3c
platform caam_sm: [0056] d9 63 78 7d 49 92 c2 b8
platform caam_sm: [0064] c9 85 72 fd ee 7a bc 6b
platform caam_sm: [0072] 57 94 0f 02 7a fc b5 aa
platform caam_sm: [0080] 00 00 00 00 00 00 00 00
platform caam_sm: [0088] 00 00 00 00 00 00 00 00
platform caam_sm: restored 64-bit black key:
platform caam_sm: [0000] 31 de 55 ff 66 b7 fa 28
platform caam_sm: [0008] 22 ee d1 9b 6f 28 ef fa
platform caam_sm: restored 128-bit black key:
platform caam_sm: [0000] b0 3f ee ef 84 13 ed f4
platform caam_sm: [0008] d4 87 15 b2 f7 30 ba 62
platform caam_sm: restored 192-bit black key:
platform caam_sm: [0000] 0b 3b 69 19 1a 3c 49 46
platform caam_sm: [0008] 23 cc dd 13 60 46 99 96
platform caam_sm: [0016] 43 5c 93 02 7c 6b fa b5
platform caam_sm: [0024] cb 79 c0 76 7b 3f f1 bf
platform caam_sm: restored 256-bit black key:
platform caam_sm: [0000] 5b 8c 4c 3b 3b 9a 54 8a
platform caam_sm: [0008] 11 c3 70 e2 9c d6 3a 79
platform caam_sm: [0016] 6b e5 66 32 03 87 32 96
platform caam_sm: [0024] b6 9c 58 f1 0e 34 e3 62
snvs-secvio 20cc000.caam-snvs: can't get snvs clock
snvs-secvio 20cc000.caam-snvs: violation handlers armed - non-secure state
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
cs42xx8 1-0048: found device, revision 4
fsl-asrc 2034000.asrc: driver registered
imx-cs42888 sound-cs42888: cs42888 <-> 2024000.esai mapping ok
imx-cs42888 sound-cs42888: snd-soc-dummy-dai <-> 2034000.asrc mapping ok
imx-cs42888 sound-cs42888: cs42888 <-> 2024000.esai mapping ok
imx-spdif sound-spdif: snd-soc-dummy-dai <-> 2004000.spdif mapping ok
imx-tuner-si476x sound-fm: failed to find FM platform device
imx-tuner-si476x: probe of sound-fm failed with error -22
imx-audio-hdmi sound-hdmi: hdmi-hifi <-> soc:hdmi_audio@00120000 mapping ok
NET: Registered protocol family 26
NET: Registered protocol family 10
sit: IPv6 over IPv4 tunneling driver
NET: Registered protocol family 17
can: controller area network core (rev 20120528 abi 9)
NET: Registered protocol family 29
can: raw protocol (rev 20120528)
can: broadcast manager protocol (rev 20120528 t)
can: netlink gateway (rev 20130117) max_hops=1
Bluetooth: RFCOMM TTY layer initialized
Bluetooth: RFCOMM socket layer initialized
Bluetooth: RFCOMM ver 1.11
Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Bluetooth: BNEP filters: protocol multicast
Bluetooth: BNEP socket layer initialized
Bluetooth: HIDP (Human Interface Emulation) ver 1.2
Bluetooth: HIDP socket layer initialized
8021q: 802.1Q VLAN Support v1.8
Key type dns_resolver registered
can-stby: supplied by can-en
flexcan 2094000.flexcan: device registered (reg_base=f0648000, irq=31)
ci_hdrc ci_hdrc.0: EHCI Host Controller
ci_hdrc ci_hdrc.0: new USB bus registered, assigned bus number 1
ci_hdrc ci_hdrc.0: USB 2.0 started, EHCI 1.00
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 1 port detected
ci_hdrc ci_hdrc.1: EHCI Host Controller
ci_hdrc ci_hdrc.1: new USB bus registered, assigned bus number 2
ci_hdrc ci_hdrc.1: USB 2.0 started, EHCI 1.00
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 1 port detected
dhd_module_init in
input: gpio-keys as /devices/soc0/gpio-keys/input/input4
snvs_rtc 20cc000.snvs:snvs-rtc-lp: setting system clock to 1970-01-01 00:00:02 UTC (2)
can-stby: disabling
can-en: disabling
VGEN2: disabling
SWBST: disabling
SW4: disabling
ALSA device list:
 #0: cs42888-audio
 #1: imx-spdif
 #2: imx-hdmi-soc
usb 1-1: new high-speed USB device number 2 using ci_hdrc
hub 1-1:1.0: USB hub found
hub 1-1:1.0: 4 ports detected
usb 1-1.2: new low-speed USB device number 3 using ci_hdrc
input:  DELL DELL USB Laser Mouse as  /devices/soc0/soc/2100000.aips-bus/2184000.usb/ci_hdrc.0/usb1/1-1/1-1.2/1-1.2:1.0/0003:046D:C063.0001/input/input5
hid-generic 0003:046D:C063.0001: input: USB HID v1.10 Mouse [DELL DELL USB Laser Mouse] on usb-ci_hdrc.0-1.2/input0
usb 1-1.3: new low-speed USB device number 4 using ci_hdrc
input:  Dell Dell QuietKey Keyboard as  /devices/soc0/soc/2100000.aips-bus/2184000.usb/ci_hdrc.0/usb1/1-1/1-1.3/1-1.3:1.0/0003:413C:2106.0002/input/input6
hid-generic 0003:413C:2106.0002: input: USB HID v1.10 Keyboard [Dell Dell QuietKey Keyboard] on usb-ci_hdrc.0-1.3/input0
kjournald starting. Commit interval 5 seconds
EXT3-fs (mmcblk2p2): using internal journal
EXT3-fs (mmcblk2p2): recovery complete
EXT3-fs (mmcblk2p2): mounted filesystem with ordered data mode
VFS: Mounted root (ext3 filesystem) on device 179:2.
devtmpfs: mounted
Freeing unused kernel memory: 432K (80af6000 - 80b62000)
Mount failed for selinuxfs on /sys/fs/selinux: No such file or directory
random: init urandom read with 29 bits of entropy available
init: plymouth-upstart-bridge main process (178) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
init: plymouth-upstart-bridge main process (188) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
init: ureadahead main process (181) terminated with status 5
init: mounted-proc main process (204) terminated with status 1
DBG sensor data is at 7f015188
 * Starting Mount filesystems on boot [ OK ]
 * Stopping Send an event to indicate plymouth is up [ OK ]
 * Starting Signal sysvinit that the rootfs is mounted [ OK ]
 * Starting Clean /tmp directory [ OK ]
 * Starting Populate and link to /run filesystem [ OK ]
 * Stopping Populate and link to /run filesystem [ OK ]
 * Stopping Clean /tmp directory [ OK ]
 * Stopping Track if upstart is running in a container [ OK ]
 * Starting Initialize or finalize resolvconf [ OK ]
 * Starting set console keymap [ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted [ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted [ OK ]
 * Starting Bridge udev events into upstart [ OK ]
 * Stopping set console keymap [ OK ]
 * Starting Signal sysvinit that local filesystems are mounted [ OK ]
 * Starting Signal sysvinit that remote filesystems are mounted [ OK ]
 * Starting device node and kernel event manager [ OK ]
 * Starting flush early job output to logs [ OK ]
 * Stopping Mount filesystems on boot [ OK ]
 * Starting load modules from /etc/modules [ OK ]
 * Starting cold plug devices [ OK ]
 * Starting log initial device creation [ OK ]
 * Stopping flush early job output to logs [ OK ]
 * Stopping load modules from /etc/modules [ OK ]
 * Starting set console font [ OK ]
 * Starting system logging daemon [ OK ]
 * Stopping set console font [ OK ]
 * Starting userspace bootsplash [ OK ]
 * Stopping userspace bootsplash [ OK ]
 * Starting Send an event to indicate plymouth is up [ OK ]
 * Stopping Send an event to indicate plymouth is up [ OK ]
 * Starting configure network device security [ OK ]
 * Starting configure network device [ OK ]
 * Starting configure network device security [ OK ]
 * Starting configure network device security [ OK ]
 * Starting configure network device security [ OK ]
 * Starting configure network device [ OK ]
 * Starting Mount network filesystems [ OK ]
 * Starting Failsafe Boot Delay [ OK ]
 * Stopping Mount network filesystems [ OK ]
 * Starting configure network device [ OK ]
 * Starting Bridge socket events into upstart [ OK ]
 * Starting Bridge file events into upstart [ OK ]
 * Starting Mount network filesystems [ OK ]
 * Starting configure network device [ OK ]
 * Stopping Failsafe Boot Delay [ OK ]
 * Starting System V initialisation compatibility [ OK ]
 * Stopping Mount network filesystems [ OK ]
 * Stopping System V initialisation compatibility [ OK ]
 * Starting System V runlevel compatibility [ OK ]
 * Starting save kernel messages [ OK ]
 * Starting configure network device security [ OK ]
 * Starting regular background program processing daemon [ OK ]
Fri Apr 1 00:00:00 UTC 2016
 * Stopping System V runlevel compatibility [ OK ]
 * Stopping save kernel messages [ OK ]

```

---

