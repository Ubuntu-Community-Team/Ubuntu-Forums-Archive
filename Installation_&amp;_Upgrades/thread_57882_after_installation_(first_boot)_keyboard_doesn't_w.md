---
title: "after installation (first boot) keyboard doesn't work"
date: 2005-08-18
forum: Installation &amp; Upgrades
---

### Post by qpid on 2005-08-18
Hello guys,

after the normal Installation of Ubnuntu the keyboard doesen't work. I think the problem occurs after the boot message "Loding Modules" or rather "... Device Mapper". I find it out of typeing the num-key while the booting and at this point the num led gives no response.

I have to reinstall Ubuntu because my linux partition was broken so ubuntu worked until that time fine and of course my keyboard, too. Also the keyboard works fine under windows, Ubuntu Live CD and the complete installation before reboot.

For more details i post the /var/log/messages of one boot sequence:
```

Aug  8 12:38:02 localhost syslogd 1.4.1#16ubuntu6: restart.
Inspecting /boot/System.map-2.6.10-5-386
Loaded 27514 symbols from /boot/System.map-2.6.10-5-386.
Symbols match kernel version 2.6.10.
No module symbols loaded - kernel modules not enabled.
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000d0000 - 00000000000d4000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
 BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
 BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
511MB LOWMEM available.
found SMP MP-table at 000fb920
DMI 2.3 present.
ACPI: PM-Timer IO Port: 0x808
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Processor #0 6:8 APIC version 16
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 2, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: root=/dev/hda9 ro quiet splash
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 1800.924 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 511772k/524224k available (1436k kernel code, 11808k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 256K (64 bytes/line)
CPU: AMD Athlon(tm) XP 2200+ stepping 00
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4248k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfdaf1, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Via IRQ fixup
ACPI: Power Resource [URP1] (off)
ACPI: Power Resource [URP2] (off)
ACPI: Power Resource [FDDP] (off)
ACPI: Power Resource [LPTP] (off)
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 9 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
audit: initializing netlink socket (disabled)
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
PCI0 UAR1  USB USB1  AC9  MC9 SLPB
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4248KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: Processor [CPU1] (supports 16 throttling states)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
VP_IDE: IDE controller at PCI slot 0000:00:11.1
ACPI: PCI interrupt 0000:00:11.1[A]: no GSI
VP_IDE: chipset revision 6
VP_IDE: not 100%% native mode: will probe irqs later
VP_IDE: VIA vt8233a (rev 00) IDE UDMA133 controller on pci0000:00:11.1
    ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
hda: IC35L060AVVA07-0, ATA DISK drive
hdb: QUANTUM FIREBALLlct20 20, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 120103200 sectors (61492 MB) w/1863KiB Cache, CHS=65535/16/63, UDMA(100)
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 p7 p8 p9 p10 >
hdb: max request size: 128KiB
hdb: 39876480 sectors (20416 MB) w/418KiB Cache, CHS=39560/16/63
 /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 >
hdc: SAMSUNG DVD-ROM SD-616T, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Stopping tasks: ==|
Freeing memory...  ^H-^H\^H|^H/^Hdone (455 pages freed)
Restarting tasks... done
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
EXT3-fs: recovery complete.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 947792k swap on /dev/hda8.  Priority:-1 extents:1
EXT3 FS on hda9, internal journal
hdc: ATAPI 48X DVD-ROM drive, 512kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: PS/2 Logitech Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda10, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Real Time Clock Driver v1.12
input: PC Speaker
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected VIA KT266/KY266x/KT333 chipset
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 64M @ 0xe0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
ACPI: PCI interrupt 0000:00:06.0[A] -> GSI 17 (level, low) -> IRQ 17
gameport: pci0000:00:06.1 speed 1217 kHz
Linux video capture interface: v1.00
bttv: driver version 0.9.15 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0).
ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 19 (level, low) -> IRQ 19
bttv0: Bt878 (rev 17) at 0000:00:08.0, irq: 19, latency: 32, mmio: 0xdddfe000
bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
bttv0: using: Hauppauge (bt878) [card=10,autodetected]
bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
bttv0: Hauppauge eeprom: model=44354, tuner=Philips FM1216 (5), radio=yes
bttv0: i2c: checking for MSP34xx @ 0x80... found
msp34xx: init: chip=MSP3415D-B3 +nicam +simple mode=simple
bttv0: i2c: checking for TDA9875 @ 0xb0... not found
bttv0: i2c: checking for TDA7432 @ 0x8a... not found
tvaudio: TV audio decoder + audio/video mux driver
tvaudio: known chips: tda9840,tda9873h,tda9874h/a,tda9850,tda9855,tea6300,tea6420,tda8425,pic16c54 (PV951),ta8874z
bttv0: i2c: checking for TDA9887 @ 0x86... not found
bttv0: registered device video0
bttv0: registered device vbi0
bttv0: registered device radio0
bttv0: PLL: 28636363 => 35468950 .. ok
ACPI: PCI interrupt 0000:00:08.1[A] -> GSI 19 (level, low) -> IRQ 19
Linux Tulip driver version 1.1.13 (May 11, 2002)
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 17
tulip0:  MII transceiver #1 config 1000 status 782d advertising 01e1.
eth0: Lite-On 82c168 PNIC rev 33 at 0001e400, 00:A0:CC:3C:E9:36, IRQ 17.
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ACPI: PCI interrupt 0000:00:0b.0[A] -> GSI 18 (level, low) -> IRQ 18
ohci_hcd 0000:00:0b.0: NEC Corporation USB
ohci_hcd 0000:00:0b.0: irq 18, pci mem 0xdfffd000
ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI interrupt 0000:00:0b.1[B] -> GSI 19 (level, low) -> IRQ 19
ohci_hcd 0000:00:0b.1: NEC Corporation USB (#2)
ohci_hcd 0000:00:0b.1: irq 19, pci mem 0xdfffe000
NET: Registered protocol family 17
ohci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:0b.2[C] -> GSI 16 (level, low) -> IRQ 16
ehci_hcd 0000:00:0b.2: NEC Corporation USB 2.0
ehci_hcd 0000:00:0b.2: irq 16, pci mem 0xdffffe00
ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 3
ehci_hcd 0000:00:0b.2: USB 2.0 initialized, EHCI 0.95, driver 26 Oct 2004
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 5 ports detected
NET: Registered protocol family 23
eth0: Setting full-duplex based on MII#1 link partner capability of 05e1.
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:11.2[D] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:11.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:11.2: irq 21, io base 0xdc00
uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:11.3[D] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:11.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:11.3: irq 21, io base 0xe000
uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 5
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 2 ports detected
usb 4-1: new full speed USB device using uhci_hcd and address 2
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2D11
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
vga16fb: mapped to 0xc00a0000
Console: switching to colour frame buffer device 80x30
Aug  8 12:38:07 localhost kernel: fb0: VGA16 VGA frame buffer device
Aug  8 12:39:23 localhost kernel: usb 4-2: new low speed USB device using uhci_hcd and address 3
Aug  8 12:39:24 localhost usb.agent[8262]:      usbmouse: blacklisted
Aug  8 12:39:24 localhost kernel: usbcore: registered new driver hiddev
Aug  8 12:39:24 localhost usb.agent[8262]:      usbhid: loaded successfully
Aug  8 12:39:24 localhost kernel: input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:11.2-2
Aug  8 12:39:24 localhost kernel: usbcore: registered new driver usbhid
Aug  8 12:39:24 localhost kernel: drivers/usb/input/hid-core.c: v2.0:USB HID core driver
Aug  8 12:39:24 localhost input.agent[8347]:      tsdev: already loaded
Aug  8 12:39:24 localhost input.agent[8347]:      mousedev: already loaded
Aug  8 12:39:24 localhost input.agent[8347]:      evdev: already loaded
Aug  8 12:39:24 localhost input.agent[8347]:      evbug: blacklisted
Aug  8 12:39:24 localhost input.agent[8386]:      evdev: already loaded
Aug  8 12:39:24 localhost input.agent[8386]:      evbug: blacklisted
Aug  8 12:39:24 localhost input.agent[8468]:      evdev: already loaded
Aug  8 12:39:24 localhost input.agent[8468]:      evbug: blacklisted
Aug  8 12:39:24 localhost input.agent[8368]:      evdev: already loaded
Aug  8 12:39:24 localhost input.agent[8368]:      evbug: blacklisted 

``` 

really long... 

I hope someone has any idea for this stupid problem!

---

### Post by tlappy on 2005-08-18
I also have (had) a simular keyboard problem. I dual boot with xp and ubuntu. I don't know if this is your problem, but, if I have usb support enabled in bios, my usb keyboard won't work in ubuntu (debian), seems ok for gentoo though. So, for now, I just disable usb support in bios, grub defaults to ubuntu and boots after time out.
Heh, if I want windoz though, have to enable usb for dos in bios to be able to select
operating system. Windoz doesn't seem to care one way or the other. During ubuntu set-up though, had to have usb for dos enabled to use keyboard, and then turn it off once ubuntu was installed in order to use the keyboard in ubuntu. ( :roll:  :roll:  :roll: )
Hope this helps maybe...

---

