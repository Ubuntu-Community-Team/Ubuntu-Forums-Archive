---
title: "HDMI no longer working in 16.04"
date: 2016-07-31
forum: Installation &amp; Upgrades
---

### Post by dashell2 on 2016-07-31
So I upgraded to 16.04 (I know I'm late) and today I wanted to use my HDMI to watch a movie on my computer on my TV (if that makes sense) but even though it's connected, it just doesn't show up.  Usually when I turn the TV on, what's on the computer displays on the TV... I tried to reboot with the TV on to see if that would help and... I don't quite know how to explain what happened, but what appeared on the TV was my desktop proper... but what was on the computer was my desktop with the wrong background and no menus available.  That was quite strange.  Also when I check sound, I can set the sound to HDMI but no actual sound comes out the TV when I do this.

Does anyone have any ideas what's going on?  I know my graphics card is an AMD if that matters.


EDIT
okay tried the reboot with the TV on again to see if maybe it'd work this time and I figured out what's going on... it's basically treating my TV as an extended monitor.  If I move my mouse over to the right on the TV it appears on my computer monitor and vice versa.  Is there a way to get it to display the same thing on both or flip them around??  This is really weird.

---

### Post by sudodus on 2016-07-31
Yes, you can display the same picture on the internal screen and the external one, but it will limit the resolution to that of the screen with lowest resolution (probably the internal screen). It can be a good idea to have this 'extended monitor mode'.

What happens it you move the window of your video playing program to the TV screen, and when it is there, make it full-screen?

---

### Post by dashell2 on 2016-07-31
[COLOR=#000000][INDENT]What happens it you move the window of your video playing program to the TV screen, and when it is there, make it full-screen?[/INDENT]


[/COLOR]
which is what I ended up doing, but the problem still exists that when I turn my TV off, I'm stuck with the desktop without menus on my computer.  What I have to do, apparently, is turn the TV on, log out, do what you just said, and when I'm done, log out again, turn off the TV and log back in to get it to reset which is an odd amount of work.  So I'm wondering, is it possible to switch the screens?  Have the desktop without the menus appear on my TV instead of the computer?

---

### Post by sudodus on 2016-08-01
I don't run any system with two monitors, I only test it occasionally (particularly with new versions), so I don't know a convenient way.

If ***[COLOR="#0000CD"]you[/COLOR]***, who a reading this thread, know how to manage two monitors in a good way, please chip in and help us :-)

---

### Post by QIII on 2016-08-01
Hello!

What model of AMD graphics adapter?  What are the rest of your machine's specifications?

AMD graphics drivers are in a state of flux at them moment and depending on your adapter you may have some difficulty.

---

### Post by dashell2 on 2016-08-01
okay specs:

[IMG]https://s31.postimg.org/7q621czbf/specs.png[/IMG]
let me know if you need more than that


as for graphics card
Radeon R7 240/340





edit
I did another command just in case:

```
fredii                        description: Desktop Computer
    product: MS-7850 (To be filled by O.E.M.)
    vendor: MSI
    version: 1.0
    serial: To be filled by O.E.M.
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.7 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop family=To be filled by O.E.M. frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=To be filled by O.E.M. uuid=00000000-0000-0000-0000-448A5BA4D04D
  *-core
       description: Motherboard
       product: Z97 PC Mate(MS-7850)
       vendor: MSI
       physical id: 0
       version: 1.0
       serial: To be filled by O.E.M.
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: V4.3
          date: 06/27/2014
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) CPU G3258 @ 3.20GHz
          vendor: Intel Corp.
          physical id: 3d
          bus info: cpu@0
          version: Intel(R) Pentium(R) CPU G3258 @ 3.20GHz
          slot: SOCKET 0
          size: 3200MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer xsave rdrand lahf_lm abm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust erms invpcid xsaveopt dtherm ida arat pln pts cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 3e
             slot: CPU Internal L1
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 3f
             slot: CPU Internal L2
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 40
             slot: CPU Internal L3
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 42
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             vendor: 0000
             physical id: 0
             serial: 00000061
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             vendor: 0000
             physical id: 1
             serial: 00000061
             slot: ChannelA-DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 2
             serial: [Empty]
             slot: ChannelB-DIMM0
        *-bank:3
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 3
             serial: [Empty]
             slot: ChannelB-DIMM1
     *-pci
          description: Host bridge
          product: 4th Gen Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
          configuration: driver=hsw_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:e000(size=4096) memory:f7e00000-f7efffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Oland PRO [Radeon R7 240/340]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:28 memory:e0000000-efffffff memory:f7e00000-f7e3ffff ioport:e000(size=256) memory:f7e40000-f7e5ffff
           *-multimedia
                description: Audio device
                product: Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:31 memory:f7e60000-f7e63fff
        *-usb:0
             description: USB controller
             product: 9 Series Chipset Family USB xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:25 memory:f7f00000-f7f0ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-31-generic xhci-hcd
                physical id: 0
                bus info: usb@4
                logical name: usb4
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-31-generic xhci-hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=14 speed=480Mbit/s
              *-usb:0
                   description: Generic USB device
                   product: Gamepad F310
                   vendor: Logitech
                   physical id: 3
                   bus info: usb@3:3
                   version: 40.14
                   serial: E1292D8C
                   capabilities: usb-2.00
                   configuration: driver=xpad maxpower=500mA speed=12Mbit/s
              *-usb:1
                   description: Video
                   product: Webcam C270
                   vendor: Logitech, Inc.
                   physical id: 9
                   bus info: usb@3:9
                   version: 0.12
                   serial: 10E6DF50
                   capabilities: usb-2.00
                   configuration: driver=snd-usb-audio maxpower=500mA speed=480Mbit/s
        *-communication
             description: Communication controller
             product: 9 Series Chipset Family ME Interface #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:29 memory:f7f19000-f7f1900f
        *-usb:1
             description: USB controller
             product: 9 Series Chipset Family USB EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7f17000-f7f173ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-31-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 9 Series Chipset Family HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:30 memory:f7f10000-f7f13fff
        *-pci:1
             description: PCI bridge
             product: 9 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:f0100000-f02fffff ioport:f0300000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 9 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:d000(size=4096) memory:f7d00000-f7dfffff ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 0c
                serial: 44:8a:5b:a4:d0:4d
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.0.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:27 ioport:d000(size=256) memory:f7d00000-f7d00fff memory:f0000000-f0003fff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
           *-pci
                description: PCI bridge
                product: ASM1083/1085 PCIe to PCI Bridge
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                resources: iomemory:202001f10-202001f0f
        *-usb:2
             description: USB controller
             product: 9 Series Chipset Family USB EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7f16000-f7f163ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-31-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: 9 Series Chipset Family Z97 LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 9 Series Chipset Family SATA Controller [AHCI Mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:26 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:f7f15000-f7f157ff
        *-serial UNCLAIMED
             description: SMBus
             product: 9 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7f14000-f7f140ff ioport:f000(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD3200AAKS-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3A01
             serial: WD-WCAT11605109
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=e809de47
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 508a-e918
                size: 348MiB
                capacity: 350MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2014-10-17 06:57:36 filesystem=ntfs label=System Reserved modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: d8d4cf67-9143-6d46-b6c0-c57a6b03daef
                size: 92GiB
                capacity: 92GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2014-10-17 06:57:38 filesystem=ntfs state=clean
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 205GiB
                capacity: 205GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 197GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 8142MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GH22LS40
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: LL00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
alison@FredII:~$
```

---

### Post by Bucky Ball on 2016-08-01
Plug the computer into the TV. Switch TV on, boot computer. Go to 'Display' and set the displays how you want to see them (mirrored, side by side, etc) then set the resolutions to whatever you like for each monitor. You are not limited to the monitor with the lowest resolution. You can set each monitor independently.

I have two machines with dual-monitors, a desktop and a laptop (and the laptop is using an AMD GPU), and another machine I plug into the TV on a regular basis. This is how they all work. Good luck.

PS: Please use code tags for terminal output (instructions in my signature). I have added them to your last post.

---

### Post by dashell2 on 2016-08-01
Okay thanks, that did the trick.  ^_^

---

### Post by Bucky Ball on 2016-08-01
Excellent news! :)

Please mark the thread as solved to help others using Thread Tools at top right of page or follow instructions in link in my signature. Cheers and enjoy. :)

---

