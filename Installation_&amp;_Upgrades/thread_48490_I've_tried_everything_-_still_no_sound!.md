---
title: "I've tried everything - still no sound!"
date: 2005-07-12
forum: Installation &amp; Upgrades
---

### Post by filemanager on 2005-07-12
I've looked at all the threads concerning sound in these forums;  including:

[http://ubuntuforums.org/showpost.php?p=100610&postcount=7](http://ubuntuforums.org/showpost.php?p=100610&postcount=7)

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+LS.&chip=SB0310%2C+P17&module=ca0106](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+LS.&chip=SB0310%2C+P17&module=ca0106)

if I type alsamixer in a terminal I get this:
> alsamixer: function snd_ctl_open failed for default: No such device

If I open Volume Control I get "No volume control elements and/or devices found"

I'm running an amd64 system. I have a Sound Blaster Live! 24-bit sound card, and I believe I also have AC97 on my motherboard (or so it says in the BIOS). I've tried disabling it, but it doesn't make a difference. (It is currently disabled, just in case it's conflicting with something along with another unknown problem).

My system is dual-booting with WinXP, where the sound works perfectly fine.

Please, if by some miracle someone can help me, post or PM me or anything!

---

### Post by C.B. on 2005-07-13
Am I right in assuming that SB Live is an older ISA card? If so, apparently Ubuntu doesn't auto-detect ISA sound cards. Not only that, but there may not even be a driver for it. I have one too . . . still no sound. I figure I'll just have to buy a cheap PCI card to get sound.

Sorry. Not very helpful.

Charles.
_____________________
[SIZE=1][FONT=Century Gothic][COLOR=DimGray]There's always the possibility that I haven't the faintest idea of what I'm talking about.[/COLOR] [/FONT][/SIZE]:wink:

---

### Post by codejunkie on 2005-07-13
[QUOTE=C.B.]Am I right in assuming that SB Live is an older ISA card? If so, apparently Ubuntu doesn't auto-detect ISA sound cards. Not only that, but there may not even be a driver for it. I have one too . . . still no sound. I figure I'll just have to buy a cheap PCI card to get sound.

Sorry. Not very helpful.

Charles.
_____________________
[SIZE=1][FONT=Century Gothic][COLOR=DimGray]There's always the possibility that I haven't the faintest idea of what I'm talking about.[/COLOR] [/FONT][/SIZE]:wink:[/QUOTE]
i don't think there would be a 64bit motherboard made that supports an ISA card today they have been phasing that out for years. but you guys might look into the 2.6.11 kernel there might be newer support for your sound cards using the 2.6.11 kernel in the universe repo don't know if it will work though. but i do know that the 2.6.12.2 kernel from kernel.org seems to have had some new support of sound blaster cards added but that would require you to compile your own kernel.

---

### Post by filemanager on 2005-07-13
I'm new to Linux. I don't know what "ISA" is but I just bought my sound card 2 weeks ago. If I have to buy a new one just to get sound then so be it! What should I get?

---

### Post by kleeman on 2005-07-13
According to the alsa sound matrix the card you mention IS supported (by the ca0106 driver rather than the more common emu10k1).
The sound matrix is here

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs)

and the detailed instructions are here

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106)

These instructions are for building the driver from scratch. Normally Ubuntu should have loaded the right alsa kernel drivers. Check this by issuing

lsmod | grep snd

and post output

---

### Post by filemanager on 2005-07-13
[QUOTE=kleeman]According to the alsa sound matrix the card you mention IS supported (by the ca0106 driver rather than the more common emu10k1).
The sound matrix is here

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs)

and the detailed instructions are here

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106)

These instructions are for building the driver from scratch. Normally Ubuntu should have loaded the right alsa kernel drivers. Check this by issuing

lsmod | grep snd

and post output[/QUOTE]
 "lsmod | grep snd" doesn't output anything

---

### Post by filemanager on 2005-07-13
[QUOTE=kleeman]According to the alsa sound matrix the card you mention IS supported (by the ca0106 driver rather than the more common emu10k1).
The sound matrix is here

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs)

and the detailed instructions are here

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106)

These instructions are for building the driver from scratch. Normally Ubuntu should have loaded the right alsa kernel drivers. Check this by issuing

lsmod | grep snd

and post output[/QUOTE]
 "lsmod | grep snd" doesn't output anything

I could never install from that page:

> jen@computer:/usr/src/alsa$ cp /downloads/alsa-*
cp: missing destination file
Try `cp --help' for more information.


Do I actually have to download the driver from somewhere?

---

### Post by kleeman on 2005-07-13
The drivers should normally be already compiled in Ubuntu but looks like they did not load in your case. Try this (from the page in question):

sudo modprobe snd-ca0106;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss

and see what happens also see what happens in dmesg

---

### Post by filemanager on 2005-07-13
> **kleeman]The drivers should normally be already compiled in Ubuntu but looks like they did not load in your case. Try this (from the page in question):

sudo modprobe snd-ca0106 said:**
> 
 > jen@computer:~$ sudo modprobe snd-ca0106;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss
Password:
FATAL: Module snd_ca0106 not found.
FATAL: Error running install command for snd_ca0106
WARNING: Error inserting soundcore (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error inserting snd_mixer_oss (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/oss/snd-mixer-oss.ko): Operation not permitted
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/snd-page-alloc.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/snd-timer.ko): Operation not permitted
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/snd-page-alloc.ko): Operation not permitted
WARNING: Error inserting soundcore (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/snd-timer.ko): Operation not permitted
FATAL: Error inserting snd_pcm (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/snd-pcm.ko): Operation not permitted
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_pcm_oss (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/oss/snd-pcm-oss.ko): Operation not permitted
WARNING: Error inserting soundcore (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/snd.ko): Operation not permitted
FATAL: Error inserting snd_mixer_oss (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/oss/snd-mixer-oss.ko): Operation not permitted
WARNING: Error inserting soundcore (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/seq/snd-seq-device.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/snd-timer.ko): Operation not permitted
WARNING: Error inserting soundcore (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/seq/snd-seq-device.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/snd-timer.ko): Operation not permitted
FATAL: Error inserting snd_seq (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/seq/snd-seq.ko): Operation not permitted
WARNING: Error running install command for snd_seq
WARNING: Error inserting snd_seq_midi_event (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/seq/snd-seq-midi-event.ko): Operation not permitted
FATAL: Error inserting snd_seq_oss (/lib/modules/2.6.10-5-amd64-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko): Operation not permitted


and

[quote]
jen@computer:~$ dmesg
496)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 256 (order: 0, 4096 bytes)
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU: AMD Athlon(tm) 64 Processor 3500+ stepping 00
ACPI: Looking for DSDT in initrd... not found!
Using local APIC NMI watchdog using perfctr0
Using local APIC timer interrupts.
Detected 12.516 MHz APIC timer.
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
NET: Registered protocol family 16
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Via IRQ fixup
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 12 devices
usbcore: registered new driver usbfs
usbcore: registered new driver hub
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
agpgart: Detected AGP bridge 0
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 256M @ 0xe0000000
PCI-DMA: Disabling IOMMU.
pnp: 00:07: ioport range 0x680-0x6ff has been reserved
pnp: 00:07: ioport range 0x290-0x297 has been reserved
IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
audit: initializing netlink socket (disabled)
audit(1121206224.188:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Linux agpgart interface v0.100 (c) Dave Jones
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 32768)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, khubd not stopped
 Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
PCI0 PS2K UAR1 AC97 USB1 USB2 USB3 USB4 EHCI PWRB SLPB
ACPI: (supports S0 S1 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4044KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 132k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
VP_IDE: IDE controller at PCI slot 0000:00:0f.1
ACPI: PCI interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
VP_IDE: chipset revision 6
VP_IDE: not 100% native mode: will probe irqs later
VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
    ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: WDC WD800JB-00FMA0, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 p7 >
Probing IDE interface ide1...
hdc: AOPEN COM5232/AAH PRO, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ===|
Freeing memory... done (518 pages freed)
Restarting tasks... done
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: recovery complete.
EXT3-fs: mounted filesystem with ordered data mode.
Adding 939760k swap on /dev/hda7.  Priority:-1 extents:1
EXT3 FS on hda6, internal journal
hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
Real Time Clock Driver v1.12
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
input: PC Speaker
inserting floppy driver for 2.6.10-5-amd64-generic
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 17
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 17
sk98lin: Asus mainboard with buggy VPD? Correcting data.
eth0: Yukon Gigabit Ethernet 10/100/1000Base-T Adapter
      PrefPort:A  RlmtMode:Check Link State
SCSI subsystem initialized
libata version 1.10 loaded.
sata_via version 1.1
ACPI: PCI interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
sata_via(0000:00:0f.0): routed to hard irq line 4
ata1: SATA max UDMA/133 cmd 0xD400 ctl 0xD002 bmdma 0xC000 irq 20
ata2: SATA max UDMA/133 cmd 0xC800 ctl 0xC402 bmdma 0xC008 irq 20
ata1: no device found (phy stat 00000000)
scsi0 : sata_via
ata2: no device found (phy stat 00000000)
scsi1 : sata_via
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:10.0: irq 21, io base 0xd800
uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:10.1: irq 21, io base 0xe000
uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
uhci_hcd 0000:00:10.2: irq 21, io base 0xe400
uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
usb 1-1: new full speed USB device using uhci_hcd and address 2
uhci_hcd 0000:00:10.3: irq 21, io base 0xe800
uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
hub 1-1:1.0: USB hub found
hub 1-1:1.0: 4 ports detected
ACPI: PCI interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
ehci_hcd 0000:00:10.4: VIA Technologies, Inc. USB 2.0
ehci_hcd 0000:00:10.4: irq 21, pci mem 0xfae00000
ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
ehci_hcd 0000:00:10.4: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
usb 1-1: USB disconnect, address 2
usb 5-5: new high speed USB device using ehci_hcd and address 3
usb 1-1: new full speed USB device using uhci_hcd and address 3
hub 1-1:1.0: USB hub found
hub 1-1:1.0: 4 ports detected
Initializing USB Mass Storage driver...
usb 1-1.1: new full speed USB device using uhci_hcd and address 4
NET: Registered protocol family 17
usb 1-1.4: new low speed USB device using uhci_hcd and address 5
scsi2 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
usbcore: registered new driver hiddev
input: USB HID v1.11 Mouse [Microsoft Microsoft USB Wireless Mouse] on usb-0000:00:10.0-1.4
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
ts: Compaq touchscreen protocol output
eth0: network connection up using port A
    speed:           100
    autonegotiation: yes
    duplex mode:     full
    flowctrl:        symmetric
    irq moderation:  disabled
    scatter-gather:  enabled
NET: Registered protocol family 10
Disabled Privacy Extensions on device ffffffff80350fc0(lo)
IPv6 over IPv4 tunneling driver
  Vendor: SanDisk   Model: Cruzer Micro      Rev: 0.2
  Type:   Direct-Access                      ANSI SCSI revision: 02
usb-storage: device scan complete
SCSI device sda: 501759 512-byte hdwr sectors (257 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 501759 512-byte hdwr sectors (257 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
 /dev/scsi/host2/bus0/target0/lun0:<6>ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
drivers/usb/input/hid-input.c: event field not found
eth0: no IPv6 routers present
powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.00.09e)
powernow-k8: BIOS error - no PSB
Device sda not ready.
end_request: I/O error, dev sda, sector 0
Buffer I/O error on device sda, logical block 0
Buffer I/O error on device sda, logical block 1
Buffer I/O error on device sda, logical block 2
Buffer I/O error on device sda, logical block 3
Buffer I/O error on device sda, logical block 4
Buffer I/O error on device sda, logical block 5
Buffer I/O error on device sda, logical block 6
Buffer I/O error on device sda, logical block 7
Device sda not ready.
end_request: I/O error, dev sda, sector 0
Buffer I/O error on device sda, logical block 0
Buffer I/O error on device sda, logical block 1
Buffer I/O error on device sda, logical block 2
Buffer I/O error on device sda, logical block 3
Buffer I/O error on device sda, logical block 4
Buffer I/O error on device sda, logical block 5
Buffer I/O error on device sda, logical block 6
Buffer I/O error on device sda, logical block 7
 unable to read partition table
Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
usb 5-5: USB disconnect, address 3
usb 5-5: new high speed USB device using ehci_hcd and address 4
scsi3 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
usb 5-5: USB disconnect, address 4
usb 5-5: new high speed USB device using ehci_hcd and address 5
scsi4 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
usb 5-5: USB disconnect, address 5
usb 5-6: new high speed USB device using ehci_hcd and address 6
scsi5 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 6
usb-storage: waiting for device to settle before scanning
  Vendor: SanDisk   Model: Cruzer Micro      Rev: 0.2
  Type:   Direct-Access                      ANSI SCSI revision: 02
SCSI device sda: 501759 512-byte hdwr sectors (257 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 501759 512-byte hdwr sectors (257 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
 /dev/scsi/host5/bus0/target0/lun0: p1
Attached scsi removable disk sda at scsi5, channel 0, id 0, lun 0
usb-storage: device scan complete
usb 5-6: USB disconnect, address 6
usb 5-5: new high speed USB device using ehci_hcd and address 7
scsi6 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 7
usb-storage: waiting for device to settle before scanning
atkbd.c: Unknown key pressed (translated set 2, code 0xbc on isa0060/serio0).
atkbd.c: Use 'setkeycodes e03c <keycode>' to make it known.
atkbd.c: Unknown key released (translated set 2, code 0xbc on isa0060/serio0).
atkbd.c: Use 'setkeycodes e03c <keycode>' to make it known.
  Vendor: SanDisk   Model: Cruzer Micro      Rev: 0.2
  Type:   Direct-Access                      ANSI SCSI revision: 02
SCSI device sda: 501759 512-byte hdwr sectors (257 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 501759 512-byte hdwr sectors (257 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
 /dev/scsi/host6/bus0/target0/lun0: p1
Attached scsi removable disk sda at scsi6, channel 0, id 0, lun 0
usb-storage: device scan complete
cdrom: open failed.
cdrom: open failed.
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
nvidia: module license 'NVIDIA' taints kernel.
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
NVRM: loading NVIDIA Linux x86_64 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:45:40 PST 2005
NVRM: WARNING: Your Linux kernel has problems in its implementation of
NVRM: the change_page_attr kernel interface.  The NVIDIA kernel
NVRM: module will attempt to work around these problems, but
NVRM: system stability may be affected.  It is recommended that
NVRM: you update to a 2.6.11 or newer kernel.


---

### Post by kleeman on 2005-07-13
Hmm interesting, I have that module in my kernel but I am using the intel kernel and you are using amd. Just to make sure do this

ls -al /lib/modules/2.6.10-5-amd64-generic/kernel/sound/pci

---

### Post by filemanager on 2005-07-13
[QUOTE=kleeman]Hmm interesting, I have that module in my kernel but I am using the intel kernel and you are using amd. Just to make sure do this

ls -al /lib/modules/2.6.10-5-amd64-generic/kernel/sound/pci[/QUOTE]


Here's the output:

> 
jen@computer:~$ ls -al /lib/modules/2.6.10-5-amd64-generic/kernel/sound/pci
total 700
drwxr-xr-x  15 root root  4096 2005-07-07 17:05 .
drwxr-xr-x  10 root root  4096 2005-07-07 17:05 ..
drwxr-xr-x   2 root root  4096 2005-07-07 17:05 ac97
drwxr-xr-x   2 root root  4096 2005-07-07 17:05 ali5451
drwxr-xr-x   2 root root  4096 2005-07-07 17:05 au88x0
drwxr-xr-x   2 root root  4096 2005-07-07 17:05 cs46xx
drwxr-xr-x   2 root root  4096 2005-07-07 17:05 emu10k1
drwxr-xr-x   2 root root  4096 2005-07-07 17:05 ice1712
drwxr-xr-x   2 root root  4096 2005-07-07 17:05 korg1212
drwxr-xr-x   2 root root  4096 2005-07-07 17:05 mixart
drwxr-xr-x   2 root root  4096 2005-07-07 17:05 nm256
drwxr-xr-x   2 root root  4096 2005-07-07 17:05 rme9652
-rw-r--r--   1 root root 20234 2005-06-24 13:52 snd-als4000.ko
-rw-r--r--   1 root root 28863 2005-06-24 13:52 snd-atiixp.ko
-rw-r--r--   1 root root 24515 2005-06-24 13:52 snd-atiixp-modem.ko
-rw-r--r--   1 root root 30849 2005-06-24 13:52 snd-azt3328.ko
-rw-r--r--   1 root root 20213 2005-06-24 13:52 snd-bt87x.ko
-rw-r--r--   1 root root 47958 2005-06-24 13:52 snd-cmipci.ko
-rw-r--r--   1 root root 31242 2005-06-24 13:52 snd-cs4281.ko
-rw-r--r--   1 root root 26843 2005-06-24 13:52 snd-ens1370.ko
-rw-r--r--   1 root root 33453 2005-06-24 13:52 snd-ens1371.ko
-rw-r--r--   1 root root 33166 2005-06-24 13:52 snd-es1938.ko
-rw-r--r--   1 root root 39544 2005-06-24 13:52 snd-es1968.ko
-rw-r--r--   1 root root 28004 2005-06-24 13:52 snd-fm801.ko
-rw-r--r--   1 root root 48577 2005-06-24 13:52 snd-intel8x0.ko
-rw-r--r--   1 root root 28739 2005-06-24 13:52 snd-intel8x0m.ko
-rw-r--r--   1 root root 31578 2005-06-24 13:52 snd-maestro3.ko
-rw-r--r--   1 root root 34098 2005-06-24 13:52 snd-rme32.ko
-rw-r--r--   1 root root 35045 2005-06-24 13:52 snd-rme96.ko
-rw-r--r--   1 root root 34551 2005-06-24 13:52 snd-sonicvibes.ko
-rw-r--r--   1 root root 41100 2005-06-24 13:52 snd-via82xx.ko
drwxr-xr-x   2 root root  4096 2005-07-07 17:05 trident
drwxr-xr-x   2 root root  4096 2005-07-07 17:05 vx222
drwxr-xr-x   2 root root  4096 2005-07-07 17:05 ymfpci


---

### Post by kleeman on 2005-07-13
Here's mine
drwxr-xr-x  17 root root  4096 2005-07-04 16:17 .
drwxr-xr-x  11 root root  4096 2005-07-04 16:17 ..
drwxr-xr-x   2 root root  4096 2005-07-04 16:17 ac97
drwxr-xr-x   2 root root  4096 2005-07-04 16:17 ali5451
drwxr-xr-x   2 root root  4096 2005-07-04 16:17 au88x0
drwxr-xr-x   2 root root  4096 2005-07-04 16:17 ca0106
drwxr-xr-x   2 root root  4096 2005-07-04 16:17 cs46xx
drwxr-xr-x   2 root root  4096 2005-07-04 16:17 emu10k1
drwxr-xr-x   2 root root  4096 2005-07-04 16:17 hda
drwxr-xr-x   2 root root  4096 2005-07-04 16:17 ice1712
drwxr-xr-x   2 root root  4096 2005-07-04 16:17 korg1212
drwxr-xr-x   2 root root  4096 2005-07-04 16:17 mixart
drwxr-xr-x   2 root root  4096 2005-07-04 16:17 nm256
drwxr-xr-x   2 root root  4096 2005-07-04 16:17 rme9652
-rw-r--r--   1 root root 18461 2005-07-04 14:28 snd-als4000.ko
-rw-r--r--   1 root root 25856 2005-07-04 14:28 snd-atiixp.ko
-rw-r--r--   1 root root 21209 2005-07-04 14:28 snd-atiixp-modem.ko
-rw-r--r--   1 root root 24950 2005-07-04 14:28 snd-azt3328.ko
-rw-r--r--   1 root root 18867 2005-07-04 14:28 snd-bt87x.ko
-rw-r--r--   1 root root 42373 2005-07-04 14:28 snd-cmipci.ko
-rw-r--r--   1 root root 27257 2005-07-04 14:28 snd-cs4281.ko
-rw-r--r--   1 root root 24503 2005-07-04 14:28 snd-ens1370.ko
-rw-r--r--   1 root root 30499 2005-07-04 14:28 snd-ens1371.ko
-rw-r--r--   1 root root 27353 2005-07-04 14:28 snd-es1938.ko
-rw-r--r--   1 root root 39396 2005-07-04 14:28 snd-es1968.ko
-rw-r--r--   1 root root 23405 2005-07-04 14:28 snd-fm801.ko
-rw-r--r--   1 root root 41620 2005-07-04 14:28 snd-intel8x0.ko
-rw-r--r--   1 root root 23483 2005-07-04 14:28 snd-intel8x0m.ko
-rw-r--r--   1 root root 31236 2005-07-04 14:28 snd-maestro3.ko
-rw-r--r--   1 root root 28291 2005-07-04 14:28 snd-rme32.ko
-rw-r--r--   1 root root 29471 2005-07-04 14:28 snd-rme96.ko
-rw-r--r--   1 root root 29100 2005-07-04 14:28 snd-sonicvibes.ko
-rw-r--r--   1 root root 35693 2005-07-04 14:28 snd-via82xx.ko
-rw-r--r--   1 root root 19711 2005-07-04 14:28 snd-via82xx-modem.ko
drwxr-xr-x   2 root root  4096 2005-07-04 16:17 trident
drwxr-xr-x   2 root root  4096 2005-07-04 16:17 vx222
drwxr-xr-x   2 root root  4096 2005-07-04 16:17 ymfpci

Notice the  ca0106
subdirectory which has the driver in my case but not yours....
To get this to work threfore you will unfortunately need to compile the alsa modules from scratch as in the directions on the page. I worries me however that they are not already there. Perhaps there are issues with amd64? One other thing to try is a later version of the kernel. Is there a 2.6.11 kernel for amd64 and does it have this driver?

---

### Post by filemanager on 2005-07-13
Gah! so what should I do? Should I get a sound card that's compliant with emu10k1 (which I already have, apparently), or recompile the alsa modules from scratch?

Because on that page I keep getting errors. =\

---

### Post by kleeman on 2005-07-13
Hah just discovered a Ubuntu howto on this topic. Its for warty but obviously relevant!

[http://www.ubuntuforums.org/showthread.php?t=19307](http://www.ubuntuforums.org/showthread.php?t=19307)

---

### Post by filemanager on 2005-07-13
[QUOTE=kleeman]Hah just discovered a Ubuntu howto on this topic. Its for warty but obviously relevant!

[http://www.ubuntuforums.org/showthread.php?t=19307](http://www.ubuntuforums.org/showthread.php?t=19307)[/QUOTE]
 Ah, I think I saw that thread before (I've seen them all. lol), but I wasn't sure if it was applicable because I'm running amd64, and it doesn't say specifically whether it would work with it or not. I will give it a try!

---

### Post by filemanager on 2005-07-13
Oh my sweet god, I have SOUND!! I am hearing the glorious beats of MUSIC!!! Thank you thank you!!!

---

### Post by kleeman on 2005-07-13
As we say in Australia: "No worries cobber"

---

### Post by filemanager on 2005-07-13
Actually I realized, I can hear sound from CDs, DVDs, mp3s, etc. but I can't hear any system sounds! Why no system sounds?

---

### Post by kleeman on 2005-07-13
Check whether they are enabled in System-Preferences-Sound
System sounds in gnome I think are controlled by the esd daemon.

---

### Post by filemanager on 2005-07-13
[QUOTE=kleeman]Check whether they are enabled in System-Preferences-Sound
System sounds in gnome I think are controlled by the esd daemon.[/QUOTE]
 They are enabled, and here's something weird, I get system sounds when I click buttons in Evolution, but no startup sounds.

Also whenever I reboot, the alsamixer mutes everything and I have to go in and change it back. Is there a way to do this automatically on startup, or save the settings somehow?

---

### Post by filemanager on 2005-07-13
Well that's weird, I rebooted again and now all the system sounds are working. Cool! Nevermind :)

---

### Post by kleeman on 2005-07-13
I think the alsa-base package controls saving and restoring of settings
Also in System-Preferences-Multimedia Systems Selector
I chose alsa for audio output

---

### Post by JPatrick on 2005-07-13
I've tried two HOWTOs and nothing works :neutral:

---

### Post by Steve1961 on 2005-09-05
Have you tried this how to for the soundblaster 24 on amd64:

[http://ubuntuforums.org/showthread.php?t=19307&highlight=soundblaster+24](http://ubuntuforums.org/showthread.php?t=19307&highlight=soundblaster+24)

I managed to get my card working with it and then adapted it to sort out the sound with a couple of onboard ac97 chips on two other 386i ubuntu boxes -  I went to the alsa website to fine the right driver and just changed the driver name when following the how to.

---

