---
title: "Slow performance because of monitor? New installation"
date: 2012-01-01
forum: Installation &amp; Upgrades
---

### Post by lfq on 2012-01-01
Hello guys,

I'm new to linux and forum, so apologise if doing something wrong.

I decide to install linux, just finished after several hours. Monitor detection is wrong, resolution good, catalyst options grey'd out.


Straight to point:-

ATI hdd 6xxxx x2
AMD 64 1100TT
Gigabyte motherboard
LG monitor ( thats the issue )


What happened:-

After installation couldnt boot or log into unity.

1)Switched to terminal, update, upgrade

2)Upgrade didnt include linux headers images and software-center, so did a sudo install on these.

3)I logged on, downloaded the latest ati drivers from site, installed them, reboot all fine.

4)the monitor detection is totally wrong. I have a LG monitor and I got a " goldstar Company Ltd22" " as a display detection.


5)At catalyst, my monitor tab is grey, cant change anything and resolution is set to 4000x4000, however my pc runs on normal 1920


The pc runs ok, not that fast, dash takes some seconds to pop, firefox is buggy, although chrome looks to work ok. Navigation on windows is kinda buggy as well. Not fast responses.

I think my performance lacks a bit, because of the monitor issue.


What do you believe?




My xorg.conf file:-



Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection





If at selection monitor i replace the VendorName with LG and so the modelname with appropriate, would solve the issue? 

I had terrible time to get so far, so i would like some feedback from more experienced, cant stand to sit another 5 hours to pc to solve it.

and google search on iphone really makes eyes bleeding!!!



Thanks in advance


EDIT:-

lspci | grep VGA


01:00.0 VGA compatible controller: ATI Technologies Inc Barts XT [ATI Radeon HD 6800 Series]
04:00.0 VGA compatible controller: ATI Technologies Inc Barts XT [ATI Radeon HD 6800 Series]


EDIT:-
Despite I installed the ati drivers from the official site, at system info i got Graphics: VESA: BARTS as drivers. Is that normal? Also at additional drivers show both as not activated.

Is it a graphic driver issue after all maybe?

---

### Post by gordintoronto on 2012-01-01
I would suggest not installing video drivers until the monitor issue is solved. Please tell us the exact model of your monitor. LG makes hundreds of different monitors. How is your monitor connected to your computer?

Ubuntu installation should take about 20 or 30 minutes, if it took hours, there is something terribly wrong with your computer. Exactly what version of Ubuntu did you install?

I can't figure out what "ATI hdd 6xxxx x2" is. Is your video card a 6850 or a 6870?

To get a detailed description of your hardware, open a terminal window and enter these commands:
sudo lshw > myconfig.txt
gedit myconfig.txt

The first command creates a text file, the second command edits it so you can read the content. Tell us exactly what this claims your monitor to be.

---

### Post by lfq on 2012-01-01
Hey gordintoronto,

first of all, thanks for looking into my problem.

Before posting the results I want to make clear a misunderstanding, format took hours because of my lack of experience and knowledge.

I had the issue with black screen, then the purple screen, then I could write try to log but unity was never showing, so google and paste random suggestion caused me to reformat a couple of times. At top of these the google search was from my iphone. Ages!!!

All the times the installation was smooth. Nothing wrong, no errors, fast and easy. And I solve the issues, or at least i thought by doing the steps I described at first post.



**_Now back to the subject._**


_Screen is LG, FLATRON W2243S   W43 series._

Thats what the labels on it.

**_ATI Radeon HDD 6870_** the two cards, crossfirex. The machine had kubuntu before and was working fine if that helps. VGA connection

**_Ubuntu 11.10 64_**. Downloaded yesterday and tried it to install with 3 different cds. ( i re-installed it as I mentioned above )


**_My myconfig.txt looks like that:-_**

I couldnt attached it, its bigger size than the allowed.


-ga-990fxa-ud3
    description: Desktop Computer
    product: GA-990FXA-UD3 ()
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=35304535-3439-3531-4235-3137FFFFFFFF
  *-core
       description: Motherboard
       product: GA-990FXA-UD3
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F2
          date: 05/17/2011
          size: 128KiB
          capacity: 4032KiB
          capabilities: isa pci pnp upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Phenom(tm) II X6 1100T Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X6 1100T Processor
          slot: Socket M2
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L3 cache
             physical id: c
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM 1333 MHz (0.8 ns)
             physical id: 0
             slot: A0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM 1333 MHz (0.8 ns)
             physical id: 1
             slot: A1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM 1333 MHz (0.8 ns)
             physical id: 2
             slot: A2
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM 1333 MHz (0.8 ns)
             physical id: 3
             slot: A3
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci:0
          description: Host bridge
          product: RD890 PCI to PCI bridge (external gfx0 port B)
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 64 bits
          clock: 33MHz
          resources: memory:0-1fffffff
        *-pci:0
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port B)
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:c000(size=4096) memory:fd900000-fd9fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Barts XT [ATI Radeon HD 6800 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:45 memory:c0000000-cfffffff memory:fd9c0000-fd9dffff ioport:ce00(size=256) memory:fd900000-fd91ffff
           *-multimedia
                description: Audio device
                product: Barts HDMI Audio [Radeon HD 6800 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:43 memory:fd9fc000-fd9fffff
        *-pci:1
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port H)
             vendor: ATI Technologies Inc
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:b000(size=4096) memory:fd000000-fd0fffff ioport:fcf00000(size=1048576)
           *-usb
                description: USB Controller
                product: EJ168 USB 3.0 Host Controller
                vendor: Etron Technology, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:40 memory:fd0f8000-fd0fffff
        *-pci:2
             description: PCI bridge
             product: RD890 PCI to PCI bridge (external gfx1 port A)
             vendor: ATI Technologies Inc
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:e000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
           *-ide UNCLAIMED
                description: IDE interface
                product: Marvell Technology Group Ltd.
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress cap_list
                configuration: latency=0
                resources: ioport:ef00(size=8) ioport:ee00(size=4) ioport:ed00(size=8) ioport:ec00(size=4) ioport:eb00(size=16) memory:fdeff000-fdeff1ff memory:fdd00000-fdd0ffff
        *-pci:3
             description: PCI bridge
             product: RD890 PCI to PCI bridge (NB-SB link)
             vendor: ATI Technologies Inc
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:d000(size=4096) memory:fdc00000-fdcfffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Barts XT [ATI Radeon HD 6800 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:46 memory:d0000000-dfffffff memory:fdcc0000-fdcdffff ioport:de00(size=256) memory:fdc00000-fdc1ffff
           *-multimedia
                description: Audio device
                product: Barts HDMI Audio [Radeon HD 6800 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:04:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:44 memory:fdcfc000-fdcfffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:ff00(size=8) ioport:fe00(size=4) ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=16) memory:fdfff000-fdfff3ff
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fdffe000-fdffefff
        *-usb:1
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fdffd000-fdffd0ff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fdffc000-fdffcfff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fdffb000-fdffb0ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_atiixp latency=32
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fa00(size=16)
           *-disk
                description: ATA Disk
                product: Hitachi HDS5C302
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/sda
                version: ML6O
                serial: ML0220F30VGSUD
                size: 1863GiB (2TB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=bc742e08-bbf8-4fc1-8692-32a2bd0ab1a3
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 183da92c-3fb0-4219-ade0-560d54bfb123
                   size: 381GiB
                   capacity: 381GiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-01-01 16:33:25 filesystem=ext4 lastmountpoint=/ modified=2012-01-01 16:48:35 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2012-01-01 21:28:14 state=mounted
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@4:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /home
                   version: 1.0
                   serial: 75b7c3cf-1b83-4b86-a35e-6aeb03e5af27
                   size: 1415GiB
                   capacity: 1415GiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-01-01 16:33:28 filesystem=ext4 lastmountpoint=/home modified=2012-01-02 02:11:22 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,acl,barrier=1,data=ordered mounted=2012-01-02 02:11:22 state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@4:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: 85484edc-e60d-4dbf-a7f3-42b3b4fa8f87
                   size: 65GiB
                   capacity: 65GiB
                   capabilities: nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7280S
                vendor: Optiarc
                physical id: 0.1.0
                bus info: scsi@4:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:fdff4000-fdff7fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
             resources: ioport:a000(size=4096) memory:fdb00000-fdbfffff memory:fda00000-fdafffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: e
                bus info: pci@0000:05:0e.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=32
                resources: irq:22 memory:fdbff000-fdbff7ff ioport:af00(size=128)
        *-usb:4
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fdffa000-fdffafff
        *-pci:5
             description: PCI bridge
             product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
             vendor: ATI Technologies Inc
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:9000(size=4096) memory:fd800000-fd8fffff ioport:fd700000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth0
                version: 06
                serial: 50:e5:49:51:b5:17
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.2 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:42 ioport:9e00(size=256) memory:fd7ff000-fd7fffff memory:fd7f8000-fd7fbfff
        *-pci:6
             description: PCI bridge
             product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
             vendor: ATI Technologies Inc
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:8000(size=4096) memory:fd600000-fd6fffff ioport:fd500000(size=1048576)
           *-usb
                description: USB Controller
                product: EJ168 USB 3.0 Host Controller
                vendor: Etron Technology, Inc.
                physical id: 0
                bus info: pci@0000:07:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:41 memory:fd6f8000-fd6fffff
        *-pci:7
             description: PCI bridge
             product: SB900 PCI to PCI bridge (PCIE port 2)
             vendor: ATI Technologies Inc
             physical id: 15.2
             bus info: pci@0000:00:15.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:7000(size=4096) memory:fd400000-fd4fffff ioport:fd300000(size=1048576)
        *-pci:8
             description: PCI bridge
             product: SB900 PCI to PCI bridge (PCIE port 3)
             vendor: ATI Technologies Inc
             physical id: 15.3
             bus info: pci@0000:00:15.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:6000(size=4096) memory:fd200000-fd2fffff ioport:fd100000(size=1048576)
        *-usb:5
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fdff9000-fdff9fff
        *-usb:6
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fdff8000-fdff80ff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz



Thanks again for time and help.



P.S. I restart the pc and crossfirex is activated and now the monitor and analog tab at catalyst isn't grey'd out. Still at Display I have the Goldstar Company Ltd as monitor detection and I'm running on 1920x1080 I think should be 1920x1280 or something isnt it?


Apologise for big post.

---

### Post by gordintoronto on 2012-01-02
According to LG's web page: [http://www.lg.com/ae/it-products/lcd-monitors/LG-W2243S-PF.jsp](http://www.lg.com/ae/it-products/lcd-monitors/LG-W2243S-PF.jsp)

the resolution of that monitor is 1920 by 1080. (Also known as, 1080P.) It would not surprise me if the same monitor is sold with a Goldstar label on it, in some countries. It's no longer available from LG.

It's too bad the monitor does not have a DVI connector. The incorrect identification might be due to using a DVI to VGA converter.

---

### Post by lfq on 2012-01-02
Yeah, might be,at least with these versions.

It had ubuntu 11.04 and referred as LG before that was the surprising.

Anyways, the performance wasn't great with unity 3d, neither with gnome-shell.

So I decided to give a go on kubuntu. Apparently runs smooth as should be. Everything worked fine, installtion, drivers etc. 


A minor issue was the first boot. I couldn't even get the login screen. 

I just pressed the reset button on the box, restarted and was in!

Props drivers, updates, enable crossfirex, restart and all done. Runs with all effects on perfectly.

Apparently my set up "loves" KDE and "hates" gnome and unity. Too bad, really wanted to try out gnome-shell.


Anyway, problem ( partially ) solved. Thanks for help and spending time on my issue mate, much appreciated.

---

### Post by gordintoronto on 2012-01-03
Interesting, I have Ubuntu 11.10 and Kubuntu 11.10 installed in a triple-boot on my laptop. I have not seen any particular advantage of one over the other, although I lean towards the classic menu of Kubuntu.

---

### Post by lfq on 2012-01-04
Idd, quite odd.


This pc was running Ubuntu 64 from 10 up to 11.04 without any problems.
Only 11.10 version makes it laggy.

2 days now on kubuntu 11.10 64 and still no issues, fast and stable. Maybe is my graphic card that doesn't play good with gnome/unity? I had these 3-4 seconds to open dash and windows/folders, was irritating :~( 


On KDE with full effects, responses immediately.

---

