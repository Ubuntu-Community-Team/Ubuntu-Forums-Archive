---
title: "GUI won't use full screen"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by CaseyCaseyCasey on 2008-07-11
i've installed 8.04 on both my laptop and my desktop.  the desktop installation is a-0k, but the laptop installation fails to make full use of the screen.  I can see the GUI, but there is a 3cm border of unused screen surrounding it.

I've looked into Systems-> preferences -> screen resolution, and have selected the largest size offered (800x600), but i still have this large border and a very small GUI to look at. 

The laptop is a toshiba Satellite.  Were I on a desktop, I would just use the monitor config tools built into the monitor to stretch the image out.  But I'm not sure how to dot that on this laptop.

Casey

---

### Post by matt79 on 2008-07-11
You might have to update your vidoe card to see more options for screen size.

---

### Post by CaseyCaseyCasey on 2008-07-11
thanks!

do you mean to say that I might have to get a new hardware videocard for mylaptop?!?!  :confused:

---

### Post by matt79 on 2008-07-11
No, you have to find the software that tell the computer how to make full use of your installed video card. (I am assuming that is the problem). You might want to make sure your laptop is up to date. Sometimes it will correct the vidoe card.

---

### Post by Pumalite on 2008-07-11
Memory? Graphics?

---

### Post by CaseyCaseyCasey on 2008-07-11
how might i do that?

---

### Post by clw3388 on 2008-07-11
May not be a driver issue..
you can open a terminal and run sudo gedit /etc/apt/X11/xorg.conf
there should be a setting in there for your video card with supported resolutions, if i remember right it is called Section "Screen"
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"

Just add what you want in quotes and save the file then reboot... 

Did i mention to backup your xorg.conf first? ya never know...

---

### Post by Pumalite on 2008-07-11
Post:
sudo lshw

---

### Post by CaseyCaseyCasey on 2008-07-11
returns:

grep-wock                 
    description: Notebook
    product: Satellite 1400
    vendor: TOSHIBA
    version: PS140A-039HGP
    serial: 72111459P
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=disabled keyboard_password=disabled power-on_password=enabled uuid=7AFE6B00-9B93-11D6-8010-B31072111459
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: $$T027A0BC
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.30 (07/02/2002)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing vesa cdboot bootselect pcmciaboot edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(TM) CPU                1333MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.11.1
          slot: uFC-PGA Socket
          size: 1333MHz
          capacity: 1333MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 32KiB
             capacity: 32KiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 256KiB
             capacity: 256KiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back
     *-memory
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 512MiB
          capacity: 1GiB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 0
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous
             physical id: 1
             slot: DIMM 1
             size: 256MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: M1644/M1644T Northbridge+Trident
          vendor: ALi Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-ali module=ali_agp
        *-pci
             description: PCI bridge
             product: PCI to AGP Controller
             vendor: ALi Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CyberBlade XPAi1
                vendor: Trident Microsystems
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 82
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=8
        *-usb
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: c3
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ALI15x3_IDE latency=64 maxlatency=4 mingnt=2 module=alim15x3
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: IC25N020ATCS04-0
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: CA2OA71A
                   serial: CSH206D9H4RLKB
                   size: 18GiB (20GB)
                   capacity: 18GiB (20GB)
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma2 signature=3b7b3b7a smart=on
                 *-volume:0
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      logical name: /
                      logical name: /dev/.static/dev
                      version: 1.0
                      serial: 641e6d22-f99e-4647-9d14-e3588ae703ab
                      size: 17GiB
                      capacity: 17GiB
                      capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                      configuration: created=2008-07-11 22:02:39 filesystem=ext3 modified=2008-07-11 22:46:14 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-07-11 22:46:14 state=mounted
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 839MiB
                      capacity: 839MiB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 839MiB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: HL-DT-STDVD-ROM GDR8081N
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 0010
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: M5451 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ALI 5451 latency=64 maxlatency=24 mingnt=2 module=snd_ali5451
        *-isa
             description: ISA bridge
             product: M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-bridge
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=ali1535_smbus latency=0 module=i2c_ali1535
        *-pcmcia:0
             description: CardBus bridge
             product: ToPIC100 PCI to Cardbus Bridge with ZV Support
             vendor: Toshiba America Info Systems
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 32
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=0 maxlatency=5 mingnt=128 module=yenta_socket
        *-pcmcia:1
             description: CardBus bridge
             product: ToPIC100 PCI to Cardbus Bridge with ZV Support
             vendor: Toshiba America Info Systems
             physical id: 11.1
             bus info: pci@0000:00:11.1
             version: 32
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=0 maxlatency=5 mingnt=128 module=yenta_socket
  *-battery
       description: Lithium Ion Battery
       product: CG916A
       vendor: TOSHIBA
       physical id: 1
       version: 07/28/02
       serial: 0900002224
       slot: 1st Battery
       configuration: voltage=10.8V
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1b:2f:37:d9:6f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.0.0.3 multicast=yes wireless=IEEE 802.11g

---

### Post by CaseyCaseyCasey on 2008-07-11
and sudo gedit /etc/apt/X11/xorg.conf returns a seemingly blank file in gedit

---

### Post by Pumalite on 2008-07-11
The kernel is not recognizing your display:

*-display UNCLAIMED
description: VGA compatible controller
product: CyberBlade XPAi1
vendor: Trident Microsystems
physical id: 0
bus info: pci@0000:01:00.0
version: 82
width: 32 bits
clock: 66MHz
capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
configuration: latency=8
You might need to add different vga to your boot line:
vga=788 vga=789 vga=791

---

### Post by CaseyCaseyCasey on 2008-07-11
how do i add that to my boot line?

---

### Post by Pumalite on 2008-07-11
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by CaseyCaseyCasey on 2008-07-11
vga=788 and vga=789 made no difference but vga=791 resulted in many screens worth of output which actually made full use of the monitor before giving me options such as 'recovery mode resume noraml boot'.  Afterwhich, I am back to a smaller GUI than my screen is capable of.

---

### Post by Pumalite on 2008-07-11
Try this:
vga=0x317

---

### Post by CaseyCaseyCasey on 2008-07-11
0x317 also generates the recovery menu as did 791.  is the first letter to the left of 3 in the above case a zero or an upper case O?  I used a zero. Will try the uppercase O now.

---

### Post by CaseyCaseyCasey on 2008-07-11
still no joys :-(

---

### Post by upchucky on 2008-07-11
i read something about Trident microsystems in the past few days, some special way of setting them up, be danged if i can remember where though, but i was googling vid cards when i found it.

there is a setting for a generic lcd display.

I have a question, did the live boot cd display properly before you installed? if yes , then use it to try to see the settings it used as they scroll by when booting from live cd.

---

### Post by Pumalite on 2008-07-11
Investigate these links:
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

---

### Post by CaseyCaseyCasey on 2008-07-12
Thanks everyone, esp. Pumalite and upchucky!

I googled 'setting for a generic lcd display trident' and selecting the first listing ([http://ubuntuforums.org/archive/index.php/t-763964.html](http://ubuntuforums.org/archive/index.php/t-763964.html)) I was able to resize my screen to the correct resolution!

Yaaaaaaaaaay SOLVED!  :-)
:popcorn:

---

