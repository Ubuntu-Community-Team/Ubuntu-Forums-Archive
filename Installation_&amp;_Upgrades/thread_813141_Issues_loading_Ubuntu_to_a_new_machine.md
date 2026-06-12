---
title: "Issues loading Ubuntu to a new machine"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by Toaster34 on 2008-05-30
Hello, 

I have recently gotten an HP Mini-Note 2133 that has SuSE loaded on it. I hate SuSE and I'm trying to get it loaded with Ubuntu. I have to boot from a USB CD Drive because the mini-note doesnt have a CD drive. I am able to boot to my Ubuntu CD, it loads the linux kernel and begins to load. After a few minutes of loading with a lot of OKs, I get the error below. I'm not able to get past that not even into the desktop. 

[255.508000] bcmx43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

It keeps ticking this message. Any help would be awesome! Thanks!

Toast

---

### Post by Pumalite on 2008-05-30
First, I'd burn a new CD after doing md5sum; burn it at 4x or less in good quality CD-R. Try again. Maybe being wired to the Internet might help.

---

### Post by Toaster34 on 2008-05-30
While I do that, does the error tell you anything?

---

### Post by Pumalite on 2008-05-30
It's trying to find and load a module for a wireless card.

---

### Post by Toaster34 on 2008-05-30
I've burnt a new CD and have checked the CD for effects. The CD has tested fine. 

I was again able to get to the menu after trying to boot from the CD. I chose to install and some thing were happening and after a while the screen just went white. I am going to try and install again. Any ideas?

---

### Post by Pumalite on 2008-05-30
Post:
lshw

---

### Post by Toaster34 on 2008-05-30
is this what you are looking for?


  Device: pci 0x169c "NetXtreme BCM5788 Gigabit Ethernet"
  SubVendor: pci 0x14e4 "Broadcom"
  SubDevice: pci 0x969c
  Revision: 0x03
  Driver: "tg3"
  Device File: eth0
  Memory Range: 0xfeaf0000-0xfeafffff (rw,non-prefetchable)
  IRQ: 225 (922 events)
  HW Address: 00:1f:29:89:95:9b
  Link detected: yes
  Module Alias: "pci:v000014E4d0000169Csv000014E4sd0000969Cbc02sc00i00"
  Driver Info #0:
    Driver Status: tg3 is active
    Driver Activation Cmd: "modprobe tg3"
  Config Status: cfg=no, avail=yes, need=no, active=unknown
  Attached to: #31 (PCI bridge)
 
35: PCI 8001.0: 0403 Audio device
  [Created at pci.317]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3288
  Unique ID: FVI2.GlJxKj9C3MF
  SysFS ID: /devices/pci0000:80/0000:80:01.0
  SysFS BusID: 0000:80:01.0
  Hardware Class: sound
  Model: "VIA High Definition Audio Controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3288 "VIA High Definition Audio Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x3030
  Revision: 0x10
  Driver: "HDA Intel"
  Memory Range: 0xfebfc000-0xfebfffff (rw,non-prefetchable)
  IRQ: 169 (361 events)
  Module Alias: "pci:v00001106d00003288sv0000103Csd00003030bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
36: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.147]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0a03
  Unique ID: z9pp.QBqTp8zQt87
  SysFS ID: /devices/pnp0/00:00
  SysFS BusID: 00:00
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0a03
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
37: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.147]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0200
  Unique ID: QL3u.ld94kxNGZf5
  SysFS ID: /devices/pnp0/00:01
  SysFS BusID: 00:01
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0200
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
38: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.147]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0303
  Unique ID: tWJy.xhndlW9HXJ7
  SysFS ID: /devices/pnp0/00:02
  SysFS BusID: 00:02
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0303
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
39: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.147]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0800
  Unique ID: KiZ0.bvKf3UMzZfE
  SysFS ID: /devices/pnp0/00:03
  SysFS BusID: 00:03
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0800
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
40: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.147]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c04
  Unique ID: ntp4.DE8RM9cWQQ8
  SysFS ID: /devices/pnp0/00:04
  SysFS BusID: 00:04
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c04
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
41: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.147]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02_1
  Unique ID: E349.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:05
  SysFS BusID: 00:05
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
42: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.147]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0b00
  Unique ID: hEKD.WYwRElrJa93
  SysFS ID: /devices/pnp0/00:06
  SysFS BusID: 00:06
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0b00
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
43: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.147]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02_0
  Unique ID: NhVi.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:07
  SysFS BusID: 00:07
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
44: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.147]
  UDI: /org/freedesktop/Hal/devices/pnp_SYN013d
  Unique ID: qslm.+t_YHFi_6u4
  SysFS ID: /devices/pnp0/00:08
  SysFS BusID: 00:08
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: SYN
  SubDevice: eisa 0x013d
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
45: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.147]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02
  Unique ID: H20r.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:09
  SysFS BusID: 00:09
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
46: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.147]
  UDI: /org/freedesktop/Hal/devices/pnp_HPQ0004
  Unique ID: iT2w.B95vU_X3dpD
  SysFS ID: /devices/pnp0/00:0a
  SysFS BusID: 00:0a
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: HPQ
  SubDevice: eisa 0x0004
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
47: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.147]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c01
  Unique ID: 9fI_.gNN83gfynbD
  SysFS ID: /devices/pnp0/00:0b
  SysFS BusID: 00:0b
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c01
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
48: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.147]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0a08
  Unique ID: cqY2.+GmdJItMGB9
  SysFS ID: /devices/pnp0/00:0c
  SysFS BusID: 00:0c
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0a08
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
49: IDE 00.0: 10600 Disk
  [Created at block.194]
  UDI: /org/freedesktop/Hal/devices/storage_serial_48OKFA1JS
  Unique ID: z70z.Rh8R30R9R14
  Parent ID: _+Pw.zAbjSTJgADD
  SysFS ID: /block/sda
  SysFS BusID: 0:0:0:0
  SysFS Device
Link: /devices/pci0000:00/0000:00:0f.0/host0/target0:0:0/0:0:0:0
  Hardware Class: disk
  Model: "TOSHIBA MK1246GS"
  Vendor: "TOSHIBA"
  Device: "MK1246GS"
  Revision: "LB21"
  Serial ID: "48OKFA1JS"
  Driver: "sata_via", "sd"
  Device File: /dev/disk/by-id/scsi-SATA_TOSHIBA_MK1246G_48OKFA1JS
  Device
Files: /dev/sda, /dev/disk/by-id/scsi-SATA_TOSHIBA_MK1246G_48OKFA1JS, /dev/disk/by-id/ata-TOSHIBA_MK1246GSX_48OKFA1JS, /dev/disk/by-path/pci-0000:00:0f.0-scsi-0:0:0:0
  Device Number: block 8:0-8:15
  BIOS id: 0x80
  Geometry (Logical): CHS 14593/255/63
  Size: 234441648 sectors a 512 bytes
  Geometry (BIOS EDD): CHS 232581/16/63
  Size (BIOS EDD): 234441648 sectors
  Geometry (BIOS Legacy): CHS 1024/255/63
  Config Status: cfg=no, avail=yes, need=no, active=unknown
  Attached to: #23 (IDE interface)
 
50: None 00.0: 11300 Partition
  [Created at block.363]
  UDI: /org/freedesktop/Hal/devices/volume_part1_size_509967360
  Unique ID: 1tKY.SE1wIdpsiiC
  Parent ID: z70z.Rh8R30R9R14
  SysFS ID: /block/sda/sda1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/disk/by-id/scsi-SATA_TOSHIBA_MK1246G_48OKFA1JS-part1
  Device
Files: /dev/sda1, /dev/disk/by-id/scsi-SATA_TOSHIBA_MK1246G_48OKFA1JS-part1, /dev/disk/by-id/ata--part1, /dev/disk/by-path/pci-0000:00:0f.0-scsi-0:0:0:0-part1
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #49 (Disk)
 
51: None 00.0: 11300 Partition
  [Created at block.363]
 
UDI: /org/freedesktop/Hal/devices/volume_uuid_6796e4a5_fa67_4cb1_8571_6ef03269db1e
  Unique ID: U2bc.SE1wIdpsiiC
  Parent ID: z70z.Rh8R30R9R14
  SysFS ID: /block/sda/sda2
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/disk/by-id/scsi-SATA_TOSHIBA_MK1246G_48OKFA1JS-part2
  Device
Files: /dev/sda2, /dev/disk/by-id/scsi-SATA_TOSHIBA_MK1246G_48OKFA1JS-part2, /dev/disk/by-id/ata--part2, /dev/disk/by-path/pci-0000:00:0f.0-scsi-0:0:0:0-part2, /dev/disk/by-uuid/6796e4a5-fa67-4cb1-8571-6ef03269db1e
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #49 (Disk)
 
52: SCSI 200.0: 10602 CD-ROM (DVD)
  [Created at block.198]
  UDI: /org/freedesktop/Hal/devices/storage_model_DVDRAM_GSA_E50L
  Unique ID: PYMB.aHFf10mEraD
  Parent ID: WQQk.Bbr16aUOXm1
  SysFS ID: /block/sr0
  SysFS BusID: 2:0:0:0
  SysFS Device
Link: /devices/pci0000:00/0000:00:10.4/usb4/4-1/4-1:1.0/host2/target2:0:0/2:0:0:0
  Hardware Class: cdrom
  Model: "HL-DT-ST DVDRAM GSA-E50L"
  Vendor: usb 0x152e "HL-DT-ST"
  Device: usb 0x2507 "DVDRAM GSA-E50L"
  Revision: "NE01"
  Serial ID: "P01020330131954"
  Driver: "usb-storage", "sr"
  Device
File: /dev/disk/by-id/usb-HL-DT-ST_DVDRAM_GSA-E50L_P01020330131954
(/dev/sg1)
  Device
Files: /dev/sr0, /dev/disk/by-id/usb-HL-DT-ST_DVDRAM_GSA-E50L_P01020330131954, /dev/disk/by-path/pci-0000:00:10.4-usb-0:1:1.0-scsi-0:0:0:0
  Device Number: block 11:0 (char 21:1)
  Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL,
DVDRAM, Hotpluggable
  Speed: 480 Mbps
  Module Alias: "usb:v152Ep2507d0000dc00dsc00dp00ic08isc06ip50"
  Driver Info #0:
    Driver Status: usb_storage is active
    Driver Activation Cmd: "modprobe usb_storage"
  Config Status: cfg=no, avail=yes, need=no, active=unknown
  Attached to: #27 (USB Controller)
  Drive Speed: 24
  Volume ID: "Ubuntu 8.04 i386"
  Application: "MKISOFS ISO 9660/HFS FILESYSTEM BUILDER & CDRECORD
CD-R/DVD CREATOR (C) 1993 E.YOUNGDALE (C) 1997 J.PEARSON/J.SCHILLING"
  Creation date: "2008042302033100"
  El Torito info: platform 0, bootable
    Boot Catalog: at sector 0x00a2
    Media: none starting at sector 0x009b
    Load: 2048 bytes
 
53: USB 00.0: 10a00 Hub
  [Created at usb.123]
  UDI: /org/freedesktop/Hal/devices/usb_device_0_0_0000_00_10_0_if0
  Unique ID: k4bc.f6TYH0Mq_i4
  Parent ID: 37TO.M+iEzzTSsLF
  SysFS ID: /devices/pci0000:00/0000:00:10.0/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.16.60-0.23-default uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: "Linux 2.6.16.60-0.23-default uhci_hcd"
  Device: "UHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:10.0"
  Driver: "hub"
  Speed: 12 Mbps
  Module Alias: "usb:v0000p0000d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #24 (USB Controller)
 
54: USB 00.0: 10a00 Hub
  [Created at usb.123]
  UDI: /org/freedesktop/Hal/devices/usb_device_0_0_0000_00_10_2_if0
  Unique ID: pBe4.Baci0XxFuG3
  Parent ID: nmR3.M+iEzzTSsLF
  SysFS ID: /devices/pci0000:00/0000:00:10.2/usb2/2-0:1.0
  SysFS BusID: 2-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.16.60-0.23-default uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: "Linux 2.6.16.60-0.23-default uhci_hcd"
  Device: "UHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:10.2"
  Driver: "hub"
  Speed: 12 Mbps
  Module Alias: "usb:v0000p0000d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #25 (USB Controller)
 
55: USB 00.0: 10a00 Hub
  [Created at usb.123]
  UDI: /org/freedesktop/Hal/devices/usb_device_0_0_0000_00_10_3_if0
  Unique ID: uIhY.yIhHOHkzqYA
  Parent ID: f5xu.M+iEzzTSsLF
  SysFS ID: /devices/pci0000:00/0000:00:10.3/usb3/3-0:1.0
  SysFS BusID: 3-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.16.60-0.23-default uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: "Linux 2.6.16.60-0.23-default uhci_hcd"
  Device: "UHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:10.3"
  Driver: "hub"
  Speed: 12 Mbps
  Module Alias: "usb:v0000p0000d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #26 (USB Controller)
 
56: USB 00.0: 10a00 Hub
  [Created at usb.123]
  UDI: /org/freedesktop/Hal/devices/usb_device_0_0_0000_00_10_4_if0
  Unique ID: zPk0.Djr6mfjLIT1
  Parent ID: WQQk.Bbr16aUOXm1
  SysFS ID: /devices/pci0000:00/0000:00:10.4/usb4/4-0:1.0
  SysFS BusID: 4-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.16.60-0.23-default ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: "Linux 2.6.16.60-0.23-default ehci_hcd"
  Device: "EHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:10.4"
  Driver: "hub"
  Speed: 480 Mbps
  Module Alias: "usb:v0000p0000d0206dc09dsc00dp01ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #27 (USB Controller)
 
58: USB 00.0: 0000 Unclassified device
  [Created at usb.123]
 
UDI: /org/freedesktop/Hal/devices/usb_device_4f2_b107_SN0001_if0_logicaldev_input
  Unique ID: Bb1l.6SrbWBBevvA
  Parent ID: zPk0.Djr6mfjLIT1
  SysFS ID: /devices/pci0000:00/0000:00:10.4/usb4/4-8/4-8:1.0
  SysFS BusID: 4-8:1.0
  Hardware Class: unknown
  Model: "Chicony Electronics CNF7070"
  Hotplug: USB
  Vendor: usb 0x04f2 "Chicony Electronics Co., Ltd."
  Device: usb 0xb107 "CNF7070"
  Revision: "8.52"
  Serial ID: "SN0001"
  Driver: "uvcvideo"
  Device File: /dev/input/event3
  Device Number: char 13:67
  Speed: 480 Mbps
  Module Alias: "usb:v04F2pB107d0852dcEFdsc02dp01ic0Eisc01ip00"
  Driver Info #0:
    Driver Status: uvcvideo is active
    Driver Activation Cmd: "modprobe uvcvideo"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #56 (Hub)
 
60: PS/2 00.0: 10800 Keyboard
  [Created at input.159]
 
UDI: /org/freedesktop/Hal/devices/platform_i8042_i8042_Kbd_Port_logicaldev_input
  Unique ID: nLyy.TBWTwSuMeW2
  Hardware Class: keyboard
  Model: "AT Translated Set 2 keyboard"
  Vendor: int 0x0211
  Device: int 0x0001 "AT Translated Set 2 keyboard"
  Device File: /dev/input/event0
  Device Number: char 13:64
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
61: PS/2 00.0: 10500 PS/2 Mouse
  [Created at input.179]
 
UDI: /org/freedesktop/Hal/devices/platform_i8042_i8042_Aux_3_Port_logicaldev_input
  Unique ID: AH6Q.845qvaQafo3
  Hardware Class: mouse
  Model: "SynPS/2 Synaptics TouchPad"
  Vendor: int 0x0212
  Device: int 0x0001 "SynPS/2 Synaptics TouchPad"
  Compatible to: int 0x0210 0x0003
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event1
  Device Number: char 13:63 (char 13:32)
  Driver Info #0:
    Buttons: 3
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
62: None 00.0: 10103 CPU
  [Created at cpu.290]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "CentaurHauls"
  Model: 6.13.0 "VIA C7-M Processor 1200MHz"
  Features:
fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,cmov,pat,clflush,acpi,mmx,fxsr,sse,sse2,tm,nx,pni,est,tm2,xtpr,rng,rng_en,ace,ace_en,ace2,ace2_en,phe,phe_en,pmm,pmm_en
  Clock: 800 MHz
  Cache: 128 kb
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
63: None 00.0: 10000 Monitor
  [Created at fb.70]
  Unique ID: rdCR.EY_qmtb9YY0
  Hardware Class: monitor
  Model: "Generic Monitor"
  Vendor: "Generic"
  Device: "Monitor"
  Resolution: 800x600@75Hz
  Driver Info #0:
    Max. Resolution: 800x600
    Vert. Sync Range: 50-90 Hz
    Hor. Sync Range: 31-48 kHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
64: None 00.0: 10701 Ethernet
  [Created at net.114]
  UDI: /org/freedesktop/Hal/devices/net_00_1f_29_89_95_9b
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.T+rPVhv0B_8
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:13.1/0000:07:03.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "tg3"
  Device File: eth0
  HW Address: 00:1f:29:89:95:9b
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #34 (Ethernet controller)
 
65: None 00.0: 10700 Loopback
  [Created at net.114]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
 
66: None 00.0: 10781 Network Interface
  [Created at net.114]
  Unique ID: wl2P.nfEXJulusj6
  SysFS ID: /class/net/sit0
  Hardware Class: network interface
  Model: "Network Interface"
  Device File: sit0
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by Pumalite on 2008-05-30
Let's wait and see how you do with a good CD.

---

### Post by Toaster34 on 2008-05-30
I white screened again.

---

### Post by Pumalite on 2008-05-30
Try the ALternate CD. You might also need some boot parameters. Try these:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
Start with the most common:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=791 vga=788
One at the time or in different combinations.
Good luck.

---

### Post by catdriver97 on 2008-05-31
> **Toaster34 said:**
> I white screened again.

Hi **Toaster**,

The whitescreen happens because Ubuntu doesn't know which video driver to use.  

There's an extensive install how-to for your Mini-Note [here]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133").  It should walk you through setting up your video card correctly and show you how to fix a lot of other Mini-Note quirks.

There's also a lot of good reference information in the other big Mini-Note thread [here]("http://ubuntuforums.org/showthread.php?t=749693&page=5").

Good luck!

---

### Post by Toaster34 on 2008-05-31
CatDriver, 

Thanks a ton! This was huge. I pounded this out in the few hours without a hitch. Everything is up and running as usual and wireless works like a charm. Thanks again!

Toast

---

### Post by catdriver97 on 2008-06-01
No problem **Toast**.  Glad it all worked out.

**ldrn** has just posted a fix for the headphone-jack sensing, and that's now up on the [wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133").  You may want to check it out.

---

