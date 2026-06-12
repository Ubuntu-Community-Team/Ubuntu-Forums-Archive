---
title: "Upgrade from 14.04.2 (latest updated trusty) to 16.4.1 is not smooth"
date: 2016-09-15
forum: Installation &amp; Upgrades
---

### Post by sylwester on 2016-09-15
I'm using nvidia drivers, but the very same version as under Trusty so it hasn't changed. 

I am having a very sluggish machine after upgrading from 14.4 to 16.4.1. It's slow logging in, it's slow switcing user and even login from terminal takes a while before I get prompt. 
It was never like this before so I'm wondering if there are some sort of daemon for user maintance or something that is causing this.

Sometimes the list of users doesn't appear or takes a long time until it appears. 

I sometimes need to press Altgr + SysRq + K to kill X and it's children and this has stopped working. Now I enter screensaver and second tmie around I'm still logged in but have made the X tty useless. Sometimes everything hangs and I need to press hard reset. Usually "Altgr + SysRq + K" was the general solution i told my wife to do when she had problems with her system and now using that trick seems to make everything worse.

My .xsession-errors has this after login:
```
openConnection: connect: Fila eller mappa finnes ikke <-- norwegian for file or directory doesn't exist
cannot connect to brltty at :0

```

After upgrades, when compiz has been involved, I have had to remove .cache/compizconfig-1/ or else my system will not show any menues or indicators at all. This has happened twice since I got Xenial. 

Neither dmesg, syslog doesn't have any interesting lines. DIsk utility doesn't indicate there are any problems with the disks.

Hope you got any ideas on how to debug or even a possible workaround/solution. Right now I feel my machine is near unusable.

Btw: The graphical upgrade was sort of a nightmare too since I lost all possibilities to click on dialogs since I couldn't give them focus and had to kill X and resume from terminal. 
This happened to all three machines so I'm now not willing to try it again but go terminal-only next time. I though such things were fixed by .1-releases. I feel bad for the people who don't like to use CLI.

---

### Post by mörgæs on 2016-09-18
Let's see the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by sylwester on 2016-09-19
I think I have managed to fix the delay in user switch/login/logout considerably by turing off dnsmasq in /etc/NetworkManager/NetworkManager.conf (just commenting it out)
I know DNS i crucial for a system to work and it might seem like dnsmasq doesn't work as planned or is prone to die perhaps?
I guess the unusable factor was that the resolver waited for dnsmasq and after a timeout turned to the second in line for each lookup and that somehow happened before loginscreen shows up and during shell initialization/pam?

I made the hardware output anyway in case you have some additional ideas other things I can do/or perhaps try to figure out whats happening with compiz:
```

computer
    description: Desktop Computer
    product: GA-990FXA-UD3
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=desktop uuid=[REMOVED]
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
          version: FD
          date: 05/30/2012
          size: 128KiB
          capacity: 4032KiB
          capabilities: isa pci pnp upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD FX(tm)-8120 Eight-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD FX(tm)-8120 Eight-Core Processor
          slot: Socket M2
          size: 1400MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core perfctr_nb cpb hw_pstate vmmcall arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
             configuration: level=1
        *-cache:1
             description: L3 cache
             physical id: c
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back
             configuration: level=3
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM 1333 MHz (0,8 ns) [empty]
             physical id: 0
             slot: A0
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM 1333 MHz (0,8 ns) [empty]
             physical id: 1
             slot: A1
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM 1333 MHz (0,8 ns)
             physical id: 2
             slot: A2
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM 1333 MHz (0,8 ns)
             physical id: 3
             slot: A3
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci:0
          description: Host bridge
          product: RD890 PCI to PCI bridge (external gfx0 port B)
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 64 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port B)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:e000(size=4096) memory:f8000000-fbffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: GF114 [GeForce GTX 560 Ti]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:27 memory:f8000000-f9ffffff memory:d0000000-d7ffffff memory:dc000000-dfffffff ioport:ef00(size=128) memory:fa000000-fa07ffff
           *-multimedia
                description: Audio device
                product: GF114 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:19 memory:fbffc000-fbffffff
        *-pci:1
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port H)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:d000(size=4096) memory:fd100000-fd1fffff ioport:fde00000(size=1048576)
           *-usb
                description: USB controller
                product: EJ168 USB 3.0 Host Controller
                vendor: Etron Technology, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:24 memory:fd1f8000-fd1fffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.4.0-36-generic xhci-hcd
                   physical id: 0
                   bus info: usb@9
                   logical name: usb9
                   version: 4.04
                   capabilities: usb-3.00
                   configuration: driver=hub slots=2 speed=5000Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.4.0-36-generic xhci-hcd
                   physical id: 1
                   bus info: usb@8
                   logical name: usb8
                   version: 4.04
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
                 *-usb:0
                      description: Mouse
                      product: USB Optical Mouse
                      vendor: A4Tech
                      physical id: 1
                      bus info: usb@8:1
                      version: 0.01
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
                 *-usb:1
                      description: Keyboard
                      product: Mad Catz V.5 Keyboard
                      vendor: Madcatz
                      physical id: 2
                      bus info: usb@8:2
                      version: 1.37
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
        *-pci:2
             description: PCI bridge
             product: RD890 PCI to PCI bridge (external gfx1 port A)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:c000(size=4096) memory:fdb00000-fdbfffff ioport:fd200000(size=1048576)
           *-storage
                description: SATA controller
                product: JMB363 SATA/IDE Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:18 memory:fdbff000-fdbff1ff
           *-ide
                description: IDE interface
                product: JMB368 IDE controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm pciexpress bus_master cap_list
                configuration: driver=pata_jmicron latency=0
                resources: irq:19 ioport:cf00(size=8) ioport:ce00(size=4) ioport:cd00(size=8) ioport:cc00(size=4) ioport:cb00(size=16)
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:ff00(size=8) ioport:fe00(size=4) ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=16) memory:fdfff000-fdfff3ff
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:fdffe000-fdffefff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.4.0-36-generic ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=5 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:fdffd000-fdffd0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-36-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=5 speed=480Mbit/s
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:fdffc000-fdffcfff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.4.0-36-generic ohci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=5 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:fdffb000-fdffb0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-36-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=5 speed=480Mbit/s
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=32
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fa00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:fdff4000-fdff7fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
             resources: ioport:b000(size=4096) memory:fdd00000-fddfffff memory:fdc00000-fdcfffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: e
                bus info: pci@0000:04:0e.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=32
                resources: irq:22 memory:fddff000-fddff7ff ioport:bf00(size=128)
        *-usb:4
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:fdffa000-fdffafff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.4.0-36-generic ohci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-pci:4
             description: PCI bridge
             product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:a000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 06
                serial: [REMOVED]
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:26 ioport:ae00(size=256) memory:fd9ff000-fd9fffff memory:fd9f8000-fd9fbfff
        *-pci:5
             description: PCI bridge
             product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:9000(size=4096) memory:fd800000-fd8fffff ioport:fd700000(size=1048576)
           *-usb
                description: USB controller
                product: EJ168 USB 3.0 Host Controller
                vendor: Etron Technology, Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:25 memory:fd8f8000-fd8fffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.4.0-36-generic xhci-hcd
                   physical id: 0
                   bus info: usb@11
                   logical name: usb11
                   version: 4.04
                   capabilities: usb-3.00
                   configuration: driver=hub slots=2 speed=5000Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.4.0-36-generic xhci-hcd
                   physical id: 1
                   bus info: usb@10
                   logical name: usb10
                   version: 4.04
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
        *-pci:6
             description: PCI bridge
             product: SB900 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 15.2
             bus info: pci@0000:00:15.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:8000(size=4096) memory:fd600000-fd6fffff ioport:fd500000(size=1048576)
        *-pci:7
             description: PCI bridge
             product: SB900 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 15.3
             bus info: pci@0000:00:15.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:7000(size=4096) memory:fd400000-fd4fffff ioport:fd300000(size=1048576)
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:fdff9000-fdff9fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.4.0-36-generic ohci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=4 speed=12Mbit/s
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:fdff8000-fdff80ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-36-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
     *-pci:1
          description: Host bridge
          product: Family 15h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 15h Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 15h Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: BW-12B1ST
             vendor: ASUS
             physical id: 0.1.0
             bus info: scsi@2:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.03
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 2
          logical name: scsi5
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: OCZ-AGILITY3
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sda
             version: 2.22
             serial: [REMOVED]
             size: 55GiB (60GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=00054d0a
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 55GiB
                capacity: 55GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-09-01 03:59:01 filesystem=ext4 lastmountpoint=/ modified=2016-09-18 08:44:25 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-09-18 08:44:26 state=mounted
     *-scsi:2
          physical id: 3
          logical name: scsi6
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD30EZRX-00D
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             version: 0A80
             serial: [REMOVED]
             size: 2794GiB
             capacity: 2794GiB
             capabilities: lvm2
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096
     *-scsi:3
          physical id: 5
          logical name: scsi7
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD30EZRX-00D
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdc
             version: 0A80
             serial: [REMOVED]
             size: 2794GiB
             capacity: 2794GiB
             capabilities: lvm2
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096

```

---

### Post by mörgæs on 2016-09-20
There is certainly no hardware bottleneck. 
My guess is that the upgrade itself is to blame and I suggest a fresh install of 16.04.1.

---

### Post by Bucky Ball on 2016-09-20
May have spotted your issue from the title without reading the rest of the thread (but I did read it). You upgraded from 14.04.2. 14.04 is at the .5 point release and you should have been, too, before you upgraded. You needed to be at 14.04.5, update/upgrade that, *then* do the upgrade to 16.04 LTS.

Doesn't help now and not guaranteeing this was the cause (leaving third-party PPAs and drivers, particularly video, enabled can be problematic and not advised) but just mentioning, perhaps for future reference.

IMHO probable cause would be your release wasn't up to date before you tried to upgrade it to a newer one or you've left a PPA or driver enabled during the install and are now feeling the consequences. Unfortunately, upgrade problems caused by these things don't often end well but wishing you luck in getting it sorted. :)

Do you have good back ups?

PS: If you[ take a look here]("https://wiki.ubuntu.com/Releases") you'll find that, rather than being the latest 14.04, 14.04.2 is in fact no longer support and EOL. In other words, you tried to upgrade from an unsupported release. It can get confusing with the HWE stack and point releases.

---

### Post by Skaperen on 2016-09-20
it has been quite fast for me.  but, i did a fresh new install of 16.04.  i recommend this to others.  do make *TWO backups* before doing this (and check them both) or like me, buying a new machine or new disk space.

---

### Post by sylwester on 2016-09-20
@Bucky Ball
Sorry. The from version must be a type then since I did update all packages and reboot before I started the distribution upgrade. It must have been 14.04.5.

@Skaperen
My desktop computer is from 2012 but was nicely speched with SSD root, 16GB Ram, 8 core CPU and Nvidia 560 (that is better than the generations after since they reduced bus size). 
I bought it specifically to run Unity smoothly and perhaps some games :-) since I had to either do that or change distro when Unity2D was discontinued. 
Since my, at that time, 6 year old daughter was used to Unity menu I choose not to change the look and feel since she liked the new menu. At almost 11 years old she still prefers Ubuntu.

---

### Post by Bucky Ball on 2016-09-20
> **sylwester said:**
> @Bucky Ball
Sorry. The from version must be a type then since I did update all packages and reboot before I started the distribution upgrade. It must have been 14.04.5.

Unless you did something like

```
sudo apt-get update
sudo apt-get **dist-upgrade**
```

... to upgrade to the .5 point release, hard to confirm that. Did you?

---

### Post by sylwester on 2016-09-21
> **Bucky Ball said:**
> Unless you did something like

```
sudo apt-get update
sudo apt-get **dist-upgrade**
```

... to upgrade to the .5 point release, hard to confirm that. Did you?

Yes. I do this before upgrading to a new distribution:

```

apt-get update
apt-get dist-upgrade
shutdown -r now
# enter CLI again
apt-get autoremove
apt-get clean
shutdown -r now

```

---

### Post by sylwester on 2016-10-03
I was a little fast when I said I thought it was done. Even after removing dnsmasq and even editing nsswitch.conf to "hosts: hosts: files dns" I still have problems with the userswitch and then it won't come back until I have rebooted. 
As mentioned before there is little information in the logs.

---

