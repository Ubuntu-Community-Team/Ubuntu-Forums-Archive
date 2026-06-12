---
title: "Asus 780G MB audio oddity in hardy install"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by iduriduridur on 2008-04-28
I have a working ASUS M3A78-EMH HDMI MB attached to an
Olevia LCD 237 HDTV via an HDMI cable. I have a 3.5mm Mini Jack To 2-RCA "Y" Cable  to the back of the TV for analog audio. 

Booting from live CD the audio works fine a little low as far as the volume but it works. Then I install hardy heron, updated and installed the ATI driver 3d driver, and dvd "stuff". the video resolution goes in 720p mode and then the audio stops working and then try to play a movie and no audio?????  No sound effects.. nothing. Is the audio trying to go through the HDMI maybe? Can I turn off hdmi audio via a config file. 

My TV has HDMI input and analog input right next to the HDMI in. 


running aplay -l under live CD looks something like this. This text was taken from a different thread, so it is not exact.  I noticed the subdevices were different in live cd vs installed. I don't know if this is something?

aplay --list-devices

card 0: ATI [HDA ATI], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: **0/1**
  Subdevice #0: subdevice #0
card 0: ATI [HDA ATI], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



Then running aplay under installed hardy x86_64. No audio. 

aplay --list-devices

card 0: ATI [HDA ATI], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: **1/1**
  Subdevice #0: subdevice #0
card 0: ATI [HDA ATI], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by iduriduridur on 2008-05-03
i fixed it by enabling hdmi sound in the bios. installing the ati hardware dmi to get it to do HDMI then selecting the HDA ATI ALSAMIXER device and

clicking the IEC958 checkbox and setting my volume. 

Now to get hardware rendering for my DVDs woohoo. 


I LOVE UBUNTU!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!:guitar:

---

### Post by SebMKd on 2008-05-10
Hi there,
Same situation, no Audio through HDMI (Gigabyte 780G: GA-MA78GM-S2H). 
Could you post a more step-by-step howto?
What do you call ""ATI DMI"?
What is the HDA ATI ALSAMIXER? (I know I've played with ALSA before, but only following strict guidelines)
Thanks for your help!

---

### Post by iduriduridur on 2008-05-12
I did a plain jane amd64 8.04 install
then run 
aplay -l
It should show an hdmi device in there, including some other ones. 
Select HDMI for all your sounds under preferences Sounds. 
double click on the volume on the top right of your desktop. Under there under preferences it should say iec958. Enable it and set your volume to 0. 

My sound works fine under dvd movies. I have not figured out why all audio does not work, like the login sound does not work. 

I just enabled proposed updates and got a kernel update but that didn't fix the audio through hdmi. Maybe i have to wait for some kind of ALSA patch or update? I don't want to have to patch ALSA hopefully just an update.

---

### Post by iduriduridur on 2008-05-12
dmesg 

es: 965496
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=e2b6340a-a1d1-4997-ae1d-9a5327dc4555 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   25.430337] Marking TSC unstable due to TSCs unsynchronized
[   25.430339] time.c: Detected 1900.776 MHz processor.
[   25.431708] Console: colour VGA+ 80x25
[   25.431711] console [tty0] enabled
[   25.431729] Checking aperture...
[   25.431732] CPU 0: aperture @ d48a000000 size 32 MB
[   25.431733] Aperture too small (32 MB)
[   25.442417] No AGP bridge found
[   25.442419] Your BIOS doesn't leave a aperture memory hole
[   25.442420] Please enable the IOMMU option in the BIOS setup
[   25.442422] This costs you 64 MB of RAM
[   25.467474] Mapping aperture over 65536 KB of RAM @ 4000000
[   25.498618] Memory: 3788616k/4718592k available (2488k kernel code, 142768k reserved, 1319k data, 320k init)
[   25.498649] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   25.576123] Calibrating delay using timer specific routine.. 3804.66 BogoMIPS (lpj=7609338)
[   25.576151] Security Framework initialized
[   25.576156] SELinux:  Disabled at boot.
[   25.576169] AppArmor: AppArmor initialized
[   25.576172] Failure registering capabilities with primary security module.
[   25.576520] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   25.578600] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   25.579585] Mount-cache hash table entries: 256
[   25.579698] Initializing cgroup subsys ns
[   25.579702] Initializing cgroup subsys cpuacct
[   25.579713] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   25.579715] CPU: L2 Cache: 512K (64 bytes/line)
[   25.579717] CPU 0/0 -> Node 0
[   25.579719] CPU: Physical Processor ID: 0
[   25.579721] CPU: Processor Core ID: 0
[   25.579743] SMP alternatives: switching to UP code
[   25.580302] Early unpacking initramfs... done
[   25.903956] ACPI: Core revision 20070126
[   25.904014] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   25.947418] Using local APIC timer interrupts.
[   25.999962] APIC timer calibration result 12505106
[   25.999964] Detected 12.505 MHz APIC timer.
[   26.000051] SMP alternatives: switching to SMP code
[   26.000508] Booting processor 1/2 APIC 0x1
[   26.010911] Initializing CPU#1
[   26.088176] Calibrating delay using timer specific routine.. 3801.58 BogoMIPS (lpj=7603170)
[   26.088182] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   26.088184] CPU: L2 Cache: 512K (64 bytes/line)
[   26.088186] CPU 1/1 -> Node 0
[   26.088188] CPU: Physical Processor ID: 0
[   26.088189] CPU: Processor Core ID: 1
[   26.088290] AMD Athlon(tm) X2 Dual Core Processor BE-2300 stepping 01
[   26.087996] Brought up 2 CPUs
[   26.088073] CPU0 attaching sched-domain:
[   26.088076]  domain 0: span 03
[   26.088078]   groups: 01 02
[   26.088080]   domain 1: span 03
[   26.088082]    groups: 03
[   26.088084] CPU1 attaching sched-domain:
[   26.088086]  domain 0: span 03
[   26.088087]   groups: 02 01
[   26.088089]   domain 1: span 03
[   26.088091]    groups: 03
[   26.088305] net_namespace: 120 bytes
[   26.088708] Time:  2:47:59  Date: 05/13/08
[   26.088738] NET: Registered protocol family 16
[   26.088929] ACPI: bus type pci registered
[   26.089000] PCI: Using configuration type 1
[   26.093065] ACPI: EC: Look up EC in DSDT
[   26.099980] ACPI: Interpreter enabled
[   26.099983] ACPI: (supports S0 S1 S3 S4 S5)
[   26.100002] ACPI: Using IOAPIC for interrupt routing
[   26.100336] Error attaching device data
[   26.100341] Error attaching device data
[   26.100345] Error attaching device data
[   26.100350] Error attaching device data
[   26.110494] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.110724] pci 0000:00:11.0: set SATA to AHCI mode
[   26.111838] PCI: Transparent bridge - 0000:00:14.4
[   26.111865] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.112181] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   26.112330] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[   26.115901] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 12 14 15)
[   26.116040] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
[   26.116180] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[   26.116316] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[   26.116452] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 *10 11 12 14 15)
[   26.116587] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[   26.116723] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 *11 12 14 15)
[   26.116858] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[   26.116995] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  45, should be 38 [20070126]
[   26.117003] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.117031] pnp: PnP ACPI init
[   26.117038] ACPI: bus type pnp registered
[   26.128640] pnp: PnP ACPI: found 15 devices
[   26.128642] ACPI: ACPI bus type pnp unregistered
[   26.128873] PCI: Using ACPI for IRQ routing
[   26.128875] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.139815] NET: Registered protocol family 8
[   26.139817] NET: Registered protocol family 20
[   26.139896] PCI-DMA: Disabling AGP.
[   26.140151] PCI-DMA: aperture base @ 4000000 size 65536 KB
[   26.140155] PCI-DMA: using GART IOMMU.
[   26.140162] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[   26.140361] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   26.140366] hpet0: 4 32-bit timers, 14318180 Hz
[   26.141417] AppArmor: AppArmor Filesystem Enabled
[   26.143779] Time: hpet clocksource has been installed.
[   26.143795] Switched to high resolution mode on CPU 0
[   26.144242] Switched to high resolution mode on CPU 1
[   26.151818] system 00:01: iomem range 0x0-0x0 could not be reserved
[   26.151822] system 00:01: iomem range 0x0-0x0 could not be reserved
[   26.151835] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   26.151838] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   26.151846] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[   26.151849] system 00:0b: ioport range 0x40b-0x40b has been reserved
[   26.151852] system 00:0b: ioport range 0x4d6-0x4d6 has been reserved
[   26.151855] system 00:0b: ioport range 0xc00-0xc01 has been reserved
[   26.151858] system 00:0b: ioport range 0xc14-0xc14 has been reserved
[   26.151861] system 00:0b: ioport range 0xc50-0xc51 has been reserved
[   26.151864] system 00:0b: ioport range 0xc52-0xc52 has been reserved
[   26.151867] system 00:0b: ioport range 0xc6c-0xc6c has been reserved
[   26.151869] system 00:0b: ioport range 0xc6f-0xc6f has been reserved
[   26.151872] system 00:0b: ioport range 0xcd0-0xcd1 has been reserved
[   26.151875] system 00:0b: ioport range 0xcd2-0xcd3 has been reserved
[   26.151878] system 00:0b: ioport range 0xcd4-0xcd5 has been reserved
[   26.151881] system 00:0b: ioport range 0xcd6-0xcd7 has been reserved
[   26.151884] system 00:0b: ioport range 0xcd8-0xcdf has been reserved
[   26.151887] system 00:0b: ioport range 0xb00-0xb3f has been reserved
[   26.151890] system 00:0b: ioport range 0x800-0x89f has been reserved
[   26.151893] system 00:0b: ioport range 0xb20-0xb2f has been reserved
[   26.151896] system 00:0b: ioport range 0x900-0x90f has been reserved
[   26.151899] system 00:0b: ioport range 0x910-0x91f has been reserved
[   26.151902] system 00:0b: ioport range 0xfe00-0xfefe has been reserved
[   26.151906] system 00:0b: iomem range 0xffb80000-0xffbfffff could not be reserved
[   26.151909] system 00:0b: iomem range 0xfec10000-0xfec1001f has been reserved
[   26.151915] system 00:0c: ioport range 0x230-0x23f has been reserved
[   26.151918] system 00:0c: ioport range 0x290-0x29f has been reserved
[   26.151921] system 00:0c: ioport range 0xa20-0xa2f has been reserved
[   26.151924] system 00:0c: ioport range 0xa30-0xa3f has been reserved
[   26.151932] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[   26.151939] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   26.151943] system 00:0e: iomem range 0xc0000-0xcffff has been reserved
[   26.151946] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   26.151949] system 00:0e: iomem range 0x100000-0xcfffffff could not be reserved
[   26.151952] system 00:0e: iomem range 0xfec00000-0xffffffff could not be reserved
[   26.152370] PCI: Bridge: 0000:00:01.0
[   26.152373]   IO window: e000-efff
[   26.152376]   MEM window: fbd00000-fbefffff
[   26.152379]   PREFETCH window: d0000000-dfffffff
[   26.152383] PCI: Bridge: 0000:00:14.4
[   26.152385]   IO window: disabled.
[   26.152390]   MEM window: fbf00000-fbffffff
[   26.152394]   PREFETCH window: disabled.
[   26.152423] NET: Registered protocol family 2
[   26.187835] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   26.189153] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   26.192997] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   26.193504] TCP: Hash tables configured (established 524288 bind 65536)
[   26.193507] TCP reno registered
[   26.203819] checking if image is initramfs... it is
[   26.828405] Freeing initrd memory: 7494k freed
[   26.833089] audit: initializing netlink socket (disabled)
[   26.833100] audit(1210646879.356:1): initialized
[   26.835137] VFS: Disk quotas dquot_6.5.1
[   26.835212] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   26.835340] io scheduler noop registered
[   26.835342] io scheduler anticipatory registered
[   26.835344] io scheduler deadline registered
[   26.835450] io scheduler cfq registered (default)
[   26.978780] Boot video device is 0000:01:05.0
[   27.007473] Real Time Clock Driver v1.12ac
[   27.007653] hpet_resources: 0xfed00000 is busy
[   27.007682] Linux agpgart interface v0.102
[   27.007684] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.007832] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.008417] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.009097] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.009159] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   27.009290] PNP: No PS/2 controller found. Probing ports directly.
[   27.009969] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.009983] serio: i8042 AUX port at 0x60,0x64 irq 12
[   27.023442] mice: PS/2 mouse device common for all mice
[   27.023486] cpuidle: using governor ladder
[   27.023488] cpuidle: using governor menu
[   27.023624] NET: Registered protocol family 1
[   27.023728] registered taskstats version 1
[   27.023834]   Magic number: 8:414:763
[   27.023837]   hash matches device serio1
[   27.023948] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   27.023952] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   27.023954] EDD information not available.
[   27.023965] Freeing unused kernel memory: 320k freed
[   28.236700] fuse init (API version 7.9)
[   28.264300] ACPI: Processor [P001] (supports 8 throttling states)
[   28.264559] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   28.264569] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   28.477334] usbcore: registered new interface driver usbfs
[   28.477356] usbcore: registered new interface driver hub
[   28.488697] SCSI subsystem initialized
[   28.495332] usbcore: registered new device driver usb
[   28.498153] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   28.498196] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.498380] ohci_hcd 0000:00:12.0: OHCI Host Controller
[   28.498598] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[   28.498629] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfbcfe000
[   28.499075] libata version 3.00 loaded.
[   28.556709] usb usb1: configuration #1 chosen from 1 choice
[   28.556734] hub 1-0:1.0: USB hub found
[   28.556745] hub 1-0:1.0: 3 ports detected
[   28.660355] ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 16 (level, low) -> IRQ 16
[   28.660540] ohci_hcd 0000:00:12.1: OHCI Host Controller
[   28.660597] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
[   28.660618] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfbcfd000
[   28.720295] usb usb2: configuration #1 chosen from 1 choice
[   28.720319] hub 2-0:1.0: USB hub found
[   28.720329] hub 2-0:1.0: 3 ports detected
[   28.725979] Floppy drive(s): fd0 is 1.44M
[   28.748159] FDC 0 is a post-1991 82077
[   28.824097] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 18
[   28.824282] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   28.824338] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
[   28.824363] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbcfc000
[   28.884028] usb usb3: configuration #1 chosen from 1 choice
[   28.884053] hub 3-0:1.0: USB hub found
[   28.884064] hub 3-0:1.0: 3 ports detected
[   28.987856] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 18 (level, low) -> IRQ 18
[   28.988042] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   28.988115] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
[   28.988133] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfbcfb000
[   29.047810] usb usb4: configuration #1 chosen from 1 choice
[   29.047833] hub 4-0:1.0: USB hub found
[   29.047843] hub 4-0:1.0: 3 ports detected
[   29.139554] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   29.151634] ACPI: PCI Interrupt 0000:00:14.5[C] -> GSI 18 (level, low) -> IRQ 18
[   29.151821] ohci_hcd 0000:00:14.5: OHCI Host Controller
[   29.151876] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 5
[   29.151894] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbcf9000
[   29.211569] usb usb5: configuration #1 chosen from 1 choice
[   29.211596] hub 5-0:1.0: USB hub found
[   29.211606] hub 5-0:1.0: 2 ports detected
[   29.315518] ahci 0000:00:11.0: version 3.0
[   29.315549] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 22 (level, low) -> IRQ 22
[   29.315777] ahci 0000:00:11.0: controller can't do PMP, turning off CAP_PMP
[   29.361121] usb 2-1: configuration #1 chosen from 1 choice
[   29.389365] usbcore: registered new interface driver hiddev
[   29.394092] input: 2.4G USB RF KeyBoard as /devices/pci0000:00/0000:00:12.1/usb2/2-1/2-1:1.0/input/input1
[   29.416021] input,hidraw0: USB HID v1.10 Keyboard [2.4G USB RF KeyBoard] on usb-0000:00:12.1-1
[   29.420930] input: 2.4G USB RF KeyBoard as /devices/pci0000:00/0000:00:12.1/usb2/2-1/2-1:1.1/input/input2
[   29.431990] input,hidraw1: USB HID v1.10 Mouse [2.4G USB RF KeyBoard] on usb-0000:00:12.1-1
[   29.443761] input: 2.4G USB RF KeyBoard as /devices/pci0000:00/0000:00:12.1/usb2/2-1/2-1:1.2/input/input3
[   29.456056] input,hiddev96,hidraw2: USB HID v1.10 Device [2.4G USB RF KeyBoard] on usb-0000:00:12.1-1
[   29.456072] usbcore: registered new interface driver usbhid
[   29.456075] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   30.317928] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   30.317933] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pio slum part 
[   30.318954] scsi0 : ahci
[   30.319257] scsi1 : ahci
[   30.319419] scsi2 : ahci
[   30.319573] scsi3 : ahci
[   30.319657] ata1: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcff900 irq 511
[   30.319661] ata2: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcff980 irq 511
[   30.319666] ata3: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcffa00 irq 511
[   30.319670] ata4: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcffa80 irq 511
[   30.793222] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   30.803318] ata1.00: ATA-8: WDC WD5000AAJS-22YFA0, 12.01C02, max UDMA/133
[   30.803322] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   30.804103] ata1.00: configured for UDMA/133
[   31.112772] ata2: SATA link down (SStatus 0 SControl 300)
[   31.424332] ata3: SATA link down (SStatus 0 SControl 300)
[   31.899666] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   32.056635] ata4.00: ATAPI: TSSTcorp CDDVDW SH-S203N, SB01, max UDMA/100, ATAPI AN
[   32.213857] ata4.00: configured for UDMA/100
[   32.213628] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAJS-2 12.0 PQ: 0 ANSI: 5
[   32.214638] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203N  SB01 PQ: 0 ANSI: 5
[   32.214612] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   32.214651] PCI: Setting latency timer of device 0000:00:14.1 to 64
[   32.214715] scsi4 : pata_atiixp
[   32.214888] scsi5 : pata_atiixp
[   32.216178] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[   32.216181] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[   32.222658] Driver 'sd' needs updating - please use bus_type methods
[   32.227663] Driver 'sr' needs updating - please use bus_type methods
[   32.227757] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   32.227770] sd 0:0:0:0: [sda] Write Protect is off
[   32.227773] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.227789] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.227841] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   32.227850] sd 0:0:0:0: [sda] Write Protect is off
[   32.227853] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.227867] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.227872]  sda: sda1 sda2 < sda5 >
[   32.262400] sd 0:0:0:0: [sda] Attached SCSI disk
[   32.266158] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   32.266175] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   32.268219] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
[   32.268223] Uniform CD-ROM driver Revision: 3.20
[   32.268263] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   32.407364] Attempting manual resume
[   32.407368] swsusp: Resume From Partition 8:5
[   32.407369] PM: Checking swsusp image.
[   32.407523] PM: Resume from disk failed.
[   32.457859] kjournald starting.  Commit interval 5 seconds
[   32.457876] EXT3-fs: mounted filesystem with ordered data mode.
[   32.546486] ACPI: PCI Interrupt 0000:00:12.2[B] -> GSI 17 (level, low) -> IRQ 17
[   32.546677] ehci_hcd 0000:00:12.2: EHCI Host Controller
[   32.546732] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 6
[   32.546775] ehci_hcd 0000:00:12.2: debug port 1
[   32.546789] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbcff000
[   32.550010] usb 2-1: USB disconnect, address 2
[   32.555559] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.555672] usb usb6: configuration #1 chosen from 1 choice
[   32.555699] hub 6-0:1.0: USB hub found
[   32.555706] hub 6-0:1.0: 6 ports detected
[   32.659001] ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 19
[   32.659194] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   32.659248] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 7
[   32.659290] ehci_hcd 0000:00:13.2: debug port 1
[   32.659302] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbcfa800
[   32.671394] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.671487] usb usb7: configuration #1 chosen from 1 choice
[   32.671509] hub 7-0:1.0: USB hub found
[   32.671515] hub 7-0:1.0: 6 ports detected
[   33.370413] usb 2-1: new low speed USB device using ohci_hcd and address 3
[   33.591618] usb 2-1: configuration #1 chosen from 1 choice
[   33.602678] input: 2.4G USB RF KeyBoard as /devices/pci0000:00/0000:00:12.1/usb2/2-1/2-1:1.0/input/input4
[   33.614090] input,hidraw0: USB HID v1.10 Keyboard [2.4G USB RF KeyBoard] on usb-0000:00:12.1-1
[   33.619561] input: 2.4G USB RF KeyBoard as /devices/pci0000:00/0000:00:12.1/usb2/2-1/2-1:1.1/input/input5
[   33.630064] input,hidraw1: USB HID v1.10 Mouse [2.4G USB RF KeyBoard] on usb-0000:00:12.1-1
[   33.642383] input: 2.4G USB RF KeyBoard as /devices/pci0000:00/0000:00:12.1/usb2/2-1/2-1:1.2/input/input6
[   33.654044] input,hiddev96,hidraw2: USB HID v1.10 Device [2.4G USB RF KeyBoard] on usb-0000:00:12.1-1
[   39.149504] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.181696] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.359574] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   39.359580] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   39.510872] input: Power Button (FF) as /devices/virtual/input/input7
[   39.519382] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   39.532939] ACPI: Power Button (FF) [PWRF]
[   39.533033] input: Power Button (CM) as /devices/virtual/input/input8
[   39.564882] ACPI: Power Button (CM) [PWRB]
[   40.025705] ath_hal: module license 'Proprietary' taints kernel.
[   40.049409] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   40.126550] wlan: 0.9.4
[   40.153922] ath_pci: 0.9.4
[   40.153993] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 20 (level, low) -> IRQ 20
[   40.737414] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   40.769050] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   40.944502] [fglrx] Maximum main memory to use for locked dma buffers: 3549 MBytes.
[   40.944533] [fglrx] ASYNCIO init succeed!
[   40.944829] [fglrx] PAT is enabled successfully!
[   40.944853] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   41.237390] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   41.315194] ath_rate_sample: 1.2 (0.9.4)
[   41.326627] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   41.326633] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   41.326642] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   41.326645] wifi0: mac 7.8 phy 4.5 radio 5.6
[   41.326649] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   41.326651] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   41.326652] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   41.326654] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   41.326656] wifi0: Use hw queue 8 for CAB traffic
[   41.326657] wifi0: Use hw queue 9 for beacons
[   41.415618] parport_pc 00:07: reported by Plug and Play ACPI
[   41.415678] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   41.423343] wifi0: Atheros 5212: mem=0xfbff0000, irq=20
[   41.423062] ACPI: PCI Interrupt 0000:01:05.1[B] -> GSI 19 (level, low) -> IRQ 19
[   41.423257] PCI: Setting latency timer of device 0000:01:05.1 to 64
[   43.706648] lp0: using parport0 (interrupt-driven).
[   43.784099] Adding 11116940k swap on /dev/sda5.  Priority:-1 extents:1 across:11116940k
[   44.327120] EXT3 FS on sda1, internal journal
[   45.531269] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.933342] No dock devices found.
[   46.229986] powernow-k8: Found 1 AMD Athlon(tm) X2 Dual Core Processor BE-2300 processors (2 cpu cores) (version 2.20.00)
[   46.229720] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0xe
[   46.229724] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xf
[   46.229727] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   47.114278] ppdev: user-space parallel port driver
[   47.224126] audit(1210646900.633:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5059 profile="/usr/sbin/cupsd" namespace="default"
[   48.832277] Clocksource tsc unstable (delta = -76858087 ns)
[   48.973306] Bluetooth: Core ver 2.11
[   48.973581] NET: Registered protocol family 31
[   48.973584] Bluetooth: HCI device and connection manager initialized
[   48.973588] Bluetooth: HCI socket layer initialized
[   48.998714] Bluetooth: L2CAP ver 2.9
[   48.998719] Bluetooth: L2CAP socket layer initialized
[   49.045951] Bluetooth: RFCOMM socket layer initialized
[   49.045970] Bluetooth: RFCOMM TTY layer initialized
[   49.045972] Bluetooth: RFCOMM ver 1.8
[   50.647987] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 18
[   51.824649] [fglrx] GART Table is not in FRAME_BUFFER range 
[   51.824659] [fglrx] Reserve Block - 0 offset =  0Xfffc000 length = 0X4000
[   51.824662] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   52.064244] [fglrx] interrupt source ff000034 successfully enabled
[   52.064251] [fglrx] enable ID = 0x00000006
[   52.064260] [fglrx] Receive enable interrupt message with irqEnableMask: ff000034
[   52.064324] [fglrx] interrupt source a0000400 successfully enabled
[   52.064326] [fglrx] enable ID = 0x00000007
[   52.064331] [fglrx] Receive enable interrupt message with irqEnableMask: a0000400
[   52.064378] [fglrx] interrupt source ff00002f successfully enabled
[   52.064381] [fglrx] enable ID = 0x00000008
[   52.064386] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002f
[   56.015278] NET: Registered protocol family 10
[   56.015756] lo: Disabled Privacy Extensions
[   56.278124] hda-intel: Invalid position buffer, using LPIB read method instead.
[   59.593209] cdrom: sr0: mrw address space DMA selected
[   59.759321] cdrom: sr0: mrw address space DMA selected
[   59.907636] UDF-fs: Partition marked readonly; forcing readonly mount
[   59.929998] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'OFFICESPACE_4X3', timestamp 2002/04/29 17:41 (1ed4)
[   60.799669] NET: Registered protocol family 17
[   63.972962] ath0: no IPv6 routers present
[   72.040748] ath0: no IPv6 routers present
user@tv1:~$ 

user@tv1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by SebMKd on 2008-05-13
Hey, thanks for the instructions ;). My playback hardware device list looks the same. I've set "ATI HDMI" in all Sound preferences. Then enabled IEC958 in the Sound propriety. However, once I do that I no longer see the volume slider. 
In any event, this gave me hope: movies have now sound (I tested a few trailers). However, like you, no system sounds. Even though I can hear the audio feedback when I click the test button in system sound preference! So I don't know what's the matter here. Same for youtube, no audio. I haven't played any mp3s yet. I'll try; however, I'm almost certain it will not work. 
It's not too bad as I'm building an HTPC on which I'll primarily watch movies and photos.

I have a daily notification for posts on this thread and will wait to read more hopefully.

---

### Post by Trollslayer on 2008-05-22
> **SebMKd said:**
> Hey, thanks for the instructions ;). My playback hardware device list looks the same. I've set "ATI HDMI" in all Sound preferences. Then enabled IEC958 in the Sound propriety. However, once I do that I no longer see the volume slider. 
In any event, this gave me hope: movies have now sound (I tested a few trailers). However, like you, no system sounds. Even though I can hear the audio feedback when I click the test button in system sound preference! So I don't know what's the matter here. Same for youtube, no audio. I haven't played any mp3s yet. I'll try; however, I'm almost certain it will not work. 
It's not too bad as I'm building an HTPC on which I'll primarily watch movies and photos.

I have a daily notification for posts on this thread and will wait to read more hopefully.

I get the same device list but cannot get audio to work (it's fine under windwos and analogue + SPDIF work).
This is an Abit motherobard but withthe same Realtek chip and ATI SB600.
Any suggestions?
[Resolution] - isntalled a package to change the default sound card to HDMI!

---

### Post by SebMKd on 2008-05-23
Hey Trollslayer, what package did you install?

---

### Post by Trollslayer on 2008-05-23
> **SebMKd said:**
> Hey Trollslayer, what package did you install?

I'm on Mythbuntu 8.04 which contains:
Ubuntu 8.04
MythTV 0.21
ALSA 1.0.15
Additional - asoundconf-gtk 1.6-0 which is the default output selector.

---

### Post by Electric Bill on 2009-03-31
> **iduriduridur said:**
> i fixed it by enabling hdmi sound in the bios. installing the ati hardware dmi to get it to do HDMI then selecting the HDA ATI ALSAMIXER device and

clicking the IEC958 checkbox and setting my volume. 

Now to get hardware rendering for my DVDs woohoo. 


I LOVE UBUNTU!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!:guitar:
Thanks iduriduridur.
That did the trick.
Btw this is not the rig in my sig - I'm using an Abit AX78 motherboard with Sapphire HD 3850 and 4GB G.Skill F2-6400CL4D RAM.
OS is Ubuntu Intrepid 64.

Bill

---

### Post by koax95 on 2009-03-31
hello...i just install ubuntu for 30 minutes ago..

can someone teach me how to install atihd3200 driver?i tried dl linux version on ati website,but cant install..using 8.10..

very noob here..

---

### Post by Electric Bill on 2009-03-31
In the top panel go to System>Administration>Hardware Drivers and let it search for available drivers.
There is only one proprietary driver for ATI so just click the activation button and the driver should install.

You can download drivers from ATI but it's a lot more difficult to install them and unless you are having problems with the Ubuntu ATI driver it won't be necessary.

Bill

---

### Post by Bloemetjesgordijn on 2009-04-01
> **koax95 said:**
> hello...i just install ubuntu for 30 minutes ago..

can someone teach me how to install atihd3200 driver?i tried dl linux version on ati website,but cant install..using 8.10..

very noob here..

You can try to use the following [thread]("http://ubuntuforums.org/showthread.php?t=1028151&page=3") if you are using Crossfire (780G with an add ati card)

It works with ATI 9.1 and 9.2 on 8.04

Cheerz

Bloemetjesgordijn

---

