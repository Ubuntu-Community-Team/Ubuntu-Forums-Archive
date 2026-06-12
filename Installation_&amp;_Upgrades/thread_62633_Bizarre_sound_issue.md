---
title: "Bizarre sound issue"
date: 2005-09-05
forum: Installation &amp; Upgrades
---

### Post by Mozzer on 2005-09-05
When I first installed Ubuntu all the sound worked fine. Obviously I couldn't listen to mp3s (until I used the Add-on CD) but the little jingle when you login and sounds like that all worked fine.

Then fairly recently the sound has been very intermittent indeed. Sometimes it plays no sounds at all, one time it did the drummy bit when the login screen appears but nothing else and sometimes it works fine.

Today being one of the days where none of it worked, I decided to do a little experimenting. For some reason, 2 applications could play mp3: Firefox and Xine.

But there's a whole list of others that won't...

Totem, MPlayer, Music Player, RealPlayer, XMMS, CD Player and Sound Preferences (when trying to preview sounds like the login sound).

Audacity gives me an error on loading: 
"There was an error initializing the audio i/o layer. You will not be able to play or record audio."

When opening Volume Meter:
"Cannot connect to a sound daemon. Please run 'esd' at a command prompt."

When running esd:
LSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave

All this suggests to me that for some reason most applications can't actually see my audio devices.

Volume Control can see 4 devices:
1. Analog Devices AD1981A (OSS Mixer)
2. CMedia PCI (OSS Mixer)
3. Intel 82801DB-ICH4 (Alsa Mixer)
4. C-Media PCI CMI8738-MC6 (Alsa Mixer)

I assume the one it wants is the intel because I am using the sound card built into the motherboard but I don't know what the "Analog Devices" are. The motherboard works fine with Windows.

Any suggestions for this strange scenario?

Thanks,
Mozzer

---

### Post by Steve1961 on 2005-09-05
Try following the steps in the how to below and install totem-xine and xine-ui.  Then reboot.

[http://ubuntuforums.org/showthread.php?t=19089&highlight=change+sound+daemon](http://ubuntuforums.org/showthread.php?t=19089&highlight=change+sound+daemon)

You'll also need to change the sound driver in XMMS to libesdout.so

---

### Post by Mozzer on 2005-09-05
I tried everything suggested apart from this:

Enable your sound server startup

which I don't understand and this:

You'll also need to change the sound driver in XMMS to libesdout.so

which I don't know how to do. So far, no dice, but thanks for your help anyway.

---

### Post by Steve1961 on 2005-09-05
No problem, I'm only just starting to get used to the language myself and it's amazing how fast you start to take some knowledge for granted rather than explaining in detail.  To restart the sound server just check the box in system/preferences/sound.  In XMMS go into the menu/options/preferences and make sure the output plugin is set to libesdout.so.  You may need to re-boot.

---

### Post by Mozzer on 2005-09-06
Ah... well, there's a box saying "enable sound server startup" which is already ticked in sound preferences, and as for XMMS I had already unknowingly done that following the link you gave me (changing the Output plugin to eSound = libesdout.so).

When I try to play using XMMS it says: 

"Please check that:

Your soundcard is configured properly.
You have the correct output plugin selected.
No other program is blocking the sound card."

Thanks,
Mozzer

---

### Post by Steve1961 on 2005-09-06
OK, lets look at what your system is detecting.  Can you post the output of the following two commands here: dmesg and lspci -v.

---

### Post by Mozzer on 2005-09-06
The thing is, Xine and Firefox still play audio so I don't see why other apps can't...

Anyway:

```
root@ubuntu:/home/mozzer # dmesg
)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 1800.189 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 510364k/522496k available (1436k kernel code, 11464k reserved, 754k data , 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 3563.52 BogoMIPS (lpj=1781760)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 3febfbff 00000000 00000000 00000000 00000000 0 0000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: After all inits, caps: 3febfbff 00000000 00000000 00000080 00000000 0000000 0
CPU: Intel(R) Pentium(R) 4 CPU 1.80GHz stepping 04
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like a n initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
ACPI: Power Resource [URP1] (off)
ACPI: Power Resource [FDDP] (off)
ACPI: Power Resource [LPTP] (off)
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
    ACPI-1138: *** Error: Method execution failed [\MCTH] (Node dfe3ece0), AE_AM L_BUFFER_LIMIT
    ACPI-1138: *** Error: Method execution failed [\OSFL] (Node dfe3ed00), AE_AM L_BUFFER_LIMIT
    ACPI-1138: *** Error: Method execution failed [\_SB_.SYSM._CRS] (Node df9f36 a0), AE_AML_BUFFER_LIMIT
    ACPI-0158: *** Error: Method execution failed [\_SB_.SYSM._CRS] (Node df9f36 a0), AE_AML_BUFFER_LIMIT
pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0c01
pnp: PnP ACPI: found 12 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
    ACPI-1138: *** Error: Method execution failed [\MCTH] (Node dfe3ece0), AE_AM L_BUFFER_LIMIT
    ACPI-1138: *** Error: Method execution failed [\OSFL] (Node dfe3ed00), AE_AM L_BUFFER_LIMIT
    ACPI-1138: *** Error: Method execution failed [\_SB_.SYSM._CRS] (Node df9f36 a0), AE_AML_BUFFER_LIMIT
    ACPI-0158: *** Error: Method execution failed [\_SB_.SYSM._CRS] (Node df9f36 a0), AE_AML_BUFFER_LIMIT
pnp: 00:0b: ioport range 0x400-0x47f could not be reserved
pnp: 00:0b: ioport range 0x680-0x6ff has been reserved
pnp: 00:0b: ioport range 0x480-0x4bf has been reserved
audit: initializing netlink socket (disabled)
audit(1126004432.569:0): initialized
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
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
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
P0P1 UAR1 USB0 USB1 USB2 USB3 AC97 SLPB
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: Processor [CPU1] (supports 8 throttling states)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH4: IDE controller at PCI slot 0000:00:1f.1
PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
ICH4: chipset revision 1
ICH4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: ST313640A, ATA DISK drive
hdb: Maxtor 6E030L0, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 26562500 sectors (13600 MB) w/512KiB Cache, CHS=26351/16/63, UDMA(33)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
hdb: max request size: 128KiB
hdb: 60058656 sectors (30750 MB) w/2048KiB Cache, CHS=59582/16/63, UDMA(100)
hdb: cache flushes supported
 /dev/ide/host0/bus0/target1/lun0: p1
Probing IDE interface ide1...
hdc: SAMSUNG CD-ROM SC-152L, ATAPI CD/DVD-ROM drive
hdd: CD-RW CR52, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (459 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 570268k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdc: ATAPI 52X CD-ROM drive, 128kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ndiswrapper version 1.3rc1 loaded (preempt=yes,smp=no)
ndiswrapper: driver net8180 (Realtek,10/07/2004,5.173.1007.2004) loaded
ACPI: PCI interrupt 0000:01:02.0[A] -> GSI 18 (level, low) -> IRQ 18
ndiswrapper: using irq 18
wlan0: ndiswrapper ethernet device 00:40:05:3e:55:3a using driver net8180, confi guration file 1186:3300.5.conf
wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS volume version 3.1.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 845G Chipset.
agpgart: Maximum main memory to use for agp memory: 438M
agpgart: Detected 892K stolen memory.
agpgart: AGP aperture is 128M @ 0xf0000000
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI  Controller #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 16, io base 0xe800
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI  Controller #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 19, io base 0xe880
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI  Controller #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0xec00
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb 2-1: new full speed USB device using uhci_hcd and address 2
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Contro ller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xffa7fc00
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
ACPI: PCI interrupt 0000:01:00.3[A] -> GSI 21 (level, low) -> IRQ 21
ehci_hcd 0000:01:00.3: ALi Corporation USB 2.0 Controller
ehci_hcd 0000:01:00.3: irq 21, pci mem 0xff8ffc00
ehci_hcd 0000:01:00.3: new USB bus registered, assigned bus number 5
PCI: cache line size of 128 is not supported by device 0000:01:00.3
ehci_hcd 0000:01:00.3: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 6 ports detected
usb 2-1: USB disconnect, address 2
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
hw_random hardware driver 1.0.0 loaded
usb 5-4: new high speed USB device using ehci_hcd and address 2
SCSI subsystem initialized
Initializing USB Mass Storage driver...
usb 2-1: new full speed USB device using uhci_hcd and address 3
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
usb 3-1: new full speed USB device using uhci_hcd and address 3
usbcore: registered new driver snd-usb-audio
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49868 usecs
intel8x0: clocking to 48000
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI interrupt 0000:01:00.0[B] -> GSI 22 (level, low) -> IRQ 22
ohci_hcd 0000:01:00.0: ALi Corporation USB 1.1 Controller
ohci_hcd 0000:01:00.0: irq 22, pci mem 0xff8fc000
ohci_hcd 0000:01:00.0: new USB bus registered, assigned bus number 6
hub 6-0:1.0: USB hub found
hub 6-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:01:00.1[C] -> GSI 23 (level, low) -> IRQ 23
ohci_hcd 0000:01:00.1: ALi Corporation USB 1.1 Controller (#2)
ohci_hcd 0000:01:00.1: irq 23, pci mem 0xff8fd000
ohci_hcd 0000:01:00.1: new USB bus registered, assigned bus number 7
hub 7-0:1.0: USB hub found
hub 7-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:01:00.2[D] -> GSI 20 (level, low) -> IRQ 20
ohci_hcd 0000:01:00.2: ALi Corporation USB 1.1 Controller (#3)
ohci_hcd 0000:01:00.2: irq 20, pci mem 0xff8fe000
ohci_hcd 0000:01:00.2: new USB bus registered, assigned bus number 8
hub 8-0:1.0: USB hub found
hub 8-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 18
  Vendor: USB 2.0   Model: Flash Disk        Rev: 2.00
  Type:   Direct-Access                      ANSI SCSI revision: 02
usb-storage: device scan complete
sda: Unit Not Ready, sense:
Current : sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
sda : READ CAPACITY failed.
sda : status=1, message=00, host=0, driver=08
Current sd: sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
sda: test WP failed, assume Write Enabled
sda: assuming drive cache: write through
SCSI device sda: 256000 512-byte hdwr sectors (131 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 256000 512-byte hdwr sectors (131 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: unknown partition table
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
[drm] Initialized drm 1.0.0 20040925
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corp. 82845G/GL[Brookdal e-G]/GE Chipset Integrated Graphics Device
mtrr: base(0xf0020000) is not aligned on a size(0x300000) boundary
wlan0: no IPv6 routers present
```

And (I have highlighted the device which I think is correct):

```
root@ubuntu:/home/mozzer # lspci -v
0000:00:00.0 Host bridge: Intel Corp. 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
        Subsystem: Intel Corp. 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
        Flags: bus master, fast devsel, latency 0
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [e4] #09 [0105]

0000:00:02.0 VGA compatible controller: Intel Corp. 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) (prog-if 00 [VGA])
        Subsystem: Intel Corp.: Unknown device 5247
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at ffa80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 1

0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Intel Corp.: Unknown device 5247
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at e800 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Intel Corp.: Unknown device 5247
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at e880 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Intel Corp.: Unknown device 5247
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at ec00 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Intel Corp.: Unknown device 5247
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at ffa7fc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #0a [2080]

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: ff800000-ff8fffff
        Prefetchable memory behind bridge: e6a00000-e6afffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) LPC Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) UltraATA-100 IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Intel Corp.: Unknown device 5247
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]
        Memory at 1ff00000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
        Subsystem: Intel Corp.: Unknown device 5247
        Flags: medium devsel, IRQ 3
        I/O ports at e000 [size=32]

[COLOR=Red]0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Intel Corp.: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at e400 [size=256]
        I/O ports at e080 [size=64]
        Memory at ffa7f800 (32-bit, non-prefetchable) [size=512]
        Memory at ffa7f400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2[/COLOR]

0000:01:00.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ALi Corporation USB 1.1 Controller
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 22
        Memory at ff8fc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [60] Power Management version 2

0000:01:00.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ALi Corporation USB 1.1 Controller
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 23
        Memory at ff8fd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [60] Power Management version 2

0000:01:00.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ALi Corporation USB 1.1 Controller
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 20
        Memory at ff8fe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [60] Power Management version 2

0000:01:00.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Unknown device 2020:8888
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 21
        Memory at ff8ffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #0a [2090]

0000:01:02.0 Ethernet controller: D-Link System Inc DWL-510 2.4GHz Wireless PCI Adapter (rev 20)
        Subsystem: D-Link System Inc: Unknown device 3301
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at d800 [size=256]
        Memory at ff8ff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

0000:01:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at d400 [size=256]
        Capabilities: [c0] Power Management version 2
```

---

### Post by Steve1961 on 2005-09-06
OK, I'm no expert but you seem to have two multimedia audio devices in the lspci output.  I've just checked my system and there's only one entry.  Have you got onboard sound and a pci sound card?  If so, disable the onboard chip in your bios.  Also check if you're system's loading a sound driver by typing lsmod.  The output from the sound section of my ouput looks like this:

snd_intel8x0           34368  2
snd_ac97_codec         76704  1 snd_intel8x0
snd_pcm_oss            53668  1
snd_mixer_oss          19072  2 snd_pcm_oss
snd_pcm                96012  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24968  1 snd_pcm
snd                    55400  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11168  3 snd

I have an onboard ac97 chip and the system's using the intel8x0 driver.

---

### Post by Mozzer on 2005-09-13
```
snd_cmipci             29472  0
snd_opl3_lib           10112  1 snd_cmipci
snd_hwdep               9220  1 snd_opl3_lib
gameport                4608  1 snd_cmipci
snd_mpu401_uart         7168  1 snd_cmipci
ohci_hcd               19848  0
snd_intel8x0           29984  1
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  3 snd_pcm_oss
snd_usb_audio          60224  1
snd_usb_lib            11776  1 snd_usb_audio
snd_rawmidi            22944  2 snd_mpu401_uart,snd_usb_lib
snd_seq_device          8332  2 snd_opl3_lib,snd_rawmidi
snd_pcm                84872  5 snd_cmipci,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_usb_audio
snd_timer              23300  2 snd_opl3_lib,snd_pcm
snd                    50276  13 snd_cmipci,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
```

The CMIPCI is my PCI sound card but I don't actually use this for my sound - I only bought it to connect my keyboard to the computer for it's MIDI functions. The Intel will be the one I should be using.

---

### Post by Steve1961 on 2005-09-13
I think the two sound devices are the problem.  Try following this thread:

[http://www.ubuntuforums.org/showthread.php?t=27186](http://www.ubuntuforums.org/showthread.php?t=27186)

---

### Post by Mozzer on 2005-10-08
The reason I stopped posting was because for some reason the sound started working again so I thought all was well. Today it went funny again so I tried to follow that thread.

Unfortunately that didn't seem to help and I don't really know why... now nothing works. :(

EDIT (about 5 minutes later)

Looking back at the thread again I noticed a post mentioning that when editing /etc/asound.conf "it was also necessary for me to use "mixer" instead of "default" in the line shown below as "pcm.!default {""

So I did that, rebooted and hey presto! Working again! Cheers, Steve! :)

---

### Post by Mozzer on 2005-10-25
Bump...

I still have a bit of trouble.

Xine won't play sound. I can see the video/visualisations fine but there is no audio whether I'm playing video or music. Same with Totem. Audacity still can't detect any sound hardware. Despite the fact that Volume Control can see 4... though I only have 2 sound cards (one build into motherboard which I use, one in the PCI which I don't).

Also, this may not be the same problem but MPlayer crashes when you open it and RealPlayer just refuses to open in the first place. The only music players that will work are Music Player (or rhythmbox as I think it is know) and XMMS.

Can anyone help?

---

### Post by Steve1961 on 2005-10-25
[QUOTE=Mozzer]Bump...

I still have a bit of trouble.

Xine won't play sound. I can see the video/visualisations fine but there is no audio whether I'm playing video or music. Same with Totem. Audacity still can't detect any sound hardware.

Also, this may not be the same problem but MPlayer crashes when you open it and RealPlayer just refuses to open in the first place. The only music players that will work are Music Player (or rhythmbox as I think it is know) and XMMS.

Can anyone help?[/QUOTE]

Sorry for the delay in replying, I've been away from ubuntu for a few weeks trying out other distros - so many distros and so little time.  Anyway, it sounds to me like you need codecs for xine and mplayer.  Try this how to:

[http://ubuntuforums.org/showthread.php?t=54399](http://ubuntuforums.org/showthread.php?t=54399)

If I remember correctly I think mplayer looks for codecs in /usr/lib/codecs, so copy the codecs to this directory as well as win32 (you'll probably have to create it.  That should do it.

---

### Post by Mozzer on 2005-10-26
I already have the codecs as I used the add-on CD. I can see the video but there's no sound. On Xine it produces no error messages so I'm assuming it's trying to use the wrong sound card. It also loads music properly and plays it but I can't hear that either.

---

### Post by Steve1961 on 2005-10-26
[QUOTE=Mozzer]I already have the codecs as I used the add-on CD. I can see the video but there's no sound. On Xine it produces no error messages so I'm assuming it's trying to use the wrong sound card. It also loads music properly and plays it but I can't hear that either.[/QUOTE]

In that case I'm out of ideas.  Sorry!

---

