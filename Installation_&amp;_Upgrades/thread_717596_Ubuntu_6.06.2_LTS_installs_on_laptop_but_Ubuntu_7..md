---
title: "Ubuntu 6.06.2 LTS installs on laptop but Ubuntu 7.10 does not"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by boondocks on 2008-03-07
On the same laptop I am able to install Ubuntu 6.06.2 LTS   :)
but I cannot install Ubuntu 7.10 because it cannot find the hard disk  :confused:

There is only one 4.1 GB internal hard disk ide (hda) on this laptop.

---

### Post by Pumalite on 2008-03-07
Post the exact error message. Post your specs.

---

### Post by boondocks on 2008-03-07
During the 7.10 install process it fails at "Detecting Disks ..."

"No disk drive was detected.  If you know the name of the driver needed by your disk drive you can selected it from the list."

I tried selecting
ide-core 
ide-disk
ide-generic

But nothing works.

---

### Post by boondocks on 2008-03-07
It is an IBM 4100 MB hard disk.

---

### Post by Pumalite on 2008-03-07
Do you have another OS there? What about your graphics and memory?

---

### Post by boondocks on 2008-03-07
Ok.  I did a dmesg and put the output on a floppy:
> 
lot 1
[53020.914778] Cannot allocate resource for EISA slot 2
[53020.915066] Cannot allocate resource for EISA slot 5
[53020.915221] EISA: Detected 0 cards.
[53020.916160] TCP cubic registered
[53020.916427] NET: Registered protocol family 1
[53020.916778] Using IPI No-Shortcut mode
[53020.917514]   Magic number: 0:766:501
[53020.922978] Freeing unused kernel memory: 364k freed
[53020.991296] input: AT Translated Set 2 keyboard as /class/input/input1
[53028.276640] usbcore: registered new interface driver usbfs
[53028.277007] usbcore: registered new interface driver hub
[53028.277547] usbcore: registered new device driver usb
[53028.288750] USB Universal Host Controller Interface driver v3.0
[53028.289324] PCI: Enabling device 0000:00:01.2 (0004 -> 0005)
[53028.289457] PCI: Assigned IRQ 11 for device 0000:00:01.2
[53028.289623] uhci_hcd 0000:00:01.2: UHCI Host Controller
[53028.290737] uhci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[53028.290978] uhci_hcd 0000:00:01.2: irq 11, io base 0x00001000
[53028.292583] usb usb1: configuration #1 chosen from 1 choice
[53028.293018] hub 1-0:1.0: USB hub found
[53028.293221] hub 1-0:1.0: 2 ports detected
[53028.511709] Yenta: CardBus bridge found at 0000:00:0a.0 [0e11:b047]
[53028.511877] Yenta: Using CSCINT to route CSC interrupts to PCI
[53028.511970] Yenta: Routing CardBus interrupts to PCI
[53028.512066] Yenta TI: socket 0000:00:0a.0, mfunc 0x01c01d22, devctl 0x64
[53028.743710] Yenta: ISA IRQ mask 0x0698, PCI irq 11
[53028.743821] Socket status: 30000010
[53028.744727] Yenta: CardBus bridge found at 0000:00:0a.1 [0e11:b047]
[53028.744868] Yenta: Using CSCINT to route CSC interrupts to PCI
[53028.744961] Yenta: Routing CardBus interrupts to PCI
[53028.745058] Yenta TI: socket 0000:00:0a.1, mfunc 0x01c01d22, devctl 0x64
[53028.918104] Floppy drive(s): fd0 is 1.44M
[53028.975650] Yenta: ISA IRQ mask 0x0698, PCI irq 11
[53028.975761] Socket status: 30000006
[53029.269422] input: PS/2 Mouse as /class/input/input2
[53029.296044] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[53029.363259] FDC 0 is a post-1991 82077
[53029.378782] pccard: PCMCIA card inserted into slot 0
[53030.980410] cs: IO port probe 0x100-0x3af: excluding 0x100-0x107 0x200-0x207 0x220-0x22f 0x250-0x257 0x330-0x337 0x378-0x37f 0x388-0x38f
[53030.983338] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[53030.984868] cs: IO port probe 0x820-0x8ff: clean.
[53030.986211] cs: IO port probe 0xc00-0xcf7: clean.
[53030.989350] cs: IO port probe 0xa00-0xaff: clean.
[53030.990839] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[53030.996627] pcmcia: registering new device pcmcia0.0
[53031.013269] cs: IO port probe 0x100-0x3af: excluding 0x100-0x107 0x200-0x207 0x220-0x22f 0x250-0x257 0x330-0x337 0x378-0x37f 0x388-0x38f
[53031.016194] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[53031.017734] cs: IO port probe 0x820-0x8ff: clean.
[53031.019144] cs: IO port probe 0xc00-0xcf7: clean.
[53031.022267] cs: IO port probe 0xa00-0xaff: clean.
[53031.188663] eth0: 3Com 3c589, io 0x300, irq 3, hw_addr 00:60:08:EC:21:FB
[53031.189019]   8K FIFO split 5:3 Rx:Tx, auto xcvr
[53031.701473] thermal: Unknown symbol acpi_processor_set_thermal_limit
[53037.958660] usbcore: registered new interface driver usbkbd
[53037.960174] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/usbkbd.c: :USB HID Boot Protocol keyboard driver
[53038.040328] usbcore: registered new interface driver hiddev
[53038.042046] usbcore: registered new interface driver usbhid
[53038.043517] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[53038.124441] usbcore: registered new interface driver usbserial
[53038.133840] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[53038.143407] usbcore: registered new interface driver usbserial_generic
[53038.143464] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[53040.320724] vga16fb: initializing
[53040.320787] vga16fb: mapped to 0xc00a0000
[53040.332444] fb0: VGA16 VGA frame buffer device
[53040.604853] Console: switching to colour frame buffer device 80x30
[53090.008973] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[53090.010519] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[53090.314968] usbcore: registered new interface driver libusual
[53090.420649] SCSI subsystem initialized
[53090.456339] Initializing USB Mass Storage driver...
[53090.465651] usbcore: registered new interface driver usb-storage
[53090.467116] USB Mass Storage support registered.
[53090.755981] ide-floppy driver 0.99.newide
[53104.106097] NET: Registered protocol family 17
[53105.393209] eth0: flipped to 10baseT
[53514.426384] libata version 2.21 loaded.
[53514.641609] ata_piix 0000:00:01.1: version 2.11
[53514.644734] scsi0 : ata_piix
[53514.646878] scsi1 : ata_piix
[53514.648595] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011020 irq 14
[53514.648649] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011028 irq 15
[53514.817605] ata1.00: ATA-3: IBM-DTCA-24090, TC6OAB1A, max UDMA/33
[53514.817655] ata1.00: 8007552 sectors, multi 16: LBA 
[53514.833637] ata1.00: configured for UDMA/33
[53514.835244] ata2: port disabled. ignoring.
[53514.841769] scsi 0:0:0:0: Direct-Access     ATA      IBM-DTCA-24090   TC6O PQ: 0 ANSI: 5
[53515.114388] parport_pc 00:01: reported by Plug and Play BIOS
[53515.114508] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[53515.389827] irda_init()
[53515.389967] NET: Registered protocol family 23
[53517.579619] sd 0:0:0:0: [sda] 8007552 512-byte hardware sectors (4100 MB)
[53517.581611] sd 0:0:0:0: [sda] Write Protect is off
[53517.581652] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[53517.584307] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[53517.585925] sd 0:0:0:0: [sda] 8007552 512-byte hardware sectors (4100 MB)
[53517.586932] sd 0:0:0:0: [sda] Write Protect is off
[53517.586970] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[53517.588511] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[53517.589371]  sda:<3>ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[53547.588940] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[53547.588964]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[53547.589032] ata1: soft resetting port
[53547.768945] ata1.00: configured for UDMA/33
[53547.769059] ata1: EH complete
[53577.768261] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[53577.768340] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[53577.768361]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[53577.768417] ata1: soft resetting port
[53577.956368] ata1.00: configured for UDMA/33
[53577.956481] ata1: EH complete
[53607.955681] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[53607.955760] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[53607.955782]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[53607.955838] ata1: soft resetting port
[53608.143783] ata1.00: configured for UDMA/33
[53608.143897] ata1: EH complete
[53638.143147] ata1.00: limiting speed to UDMA/25:PIO4
[53638.143207] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[53638.143278] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[53638.143299]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[53638.143370] ata1: soft resetting port
[53638.331207] ata1.00: configured for UDMA/25
[53638.331345] ata1: EH complete

In fact, I specified nousb noscsi on the kernel boot line and still it probing both.

---

### Post by Pumalite on 2008-03-07
Try editing your boot. F6, then 'e' to get to a Grub menu, add 'all_generic_ide' at the end of the boot line, then 'b' to boot.
If that doesn't work; go for a smaller distro, like Puppy or DSL.

---

