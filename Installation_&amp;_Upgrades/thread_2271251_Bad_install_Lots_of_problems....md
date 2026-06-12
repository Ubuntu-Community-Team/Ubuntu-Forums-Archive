---
title: "Bad install? Lots of problems..."
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by Vega_31 on 2015-03-28
New to this - please be gentle.

Until recently I had Ubuntu 14.10 installed on a laptop however I started getting frequent crashes. Firefox would crash very often and I got many “system program error detected” and “Ubuntu 14.10 has experienced an internal error” and advice to restart if problems continued. They did.

 

 The hard drive was on its way out so I decided to replace it and do a clean Ubuntu 14.04LTS install. I have experienced the crashes and error messages ever since.  

 

 Things I've noticed which don't seem right:

 

 The OS only boots every other time, the initial laptop splash screen appears then, when it should go to the select loading screen (where you can choose various Ubuntu boots or say windows if you have both installed), it often just goes black, requiring a restart before booting as normal. Sometimes when the screen goes black I can press the arrow keys and a command line style enter encryption pass phrase comes up and I can boot.

 

 I get two “System program problem detected” when I log in to my one and only user area.

 

 Software centre does not work. It often crashes immediately during loading. Sometimes it's painfully slow for a few minutes and then crashes.  

 

 I am unable to install software. Often it looks like it had installed but it hasn't. This is often frustrating as sometimes programs work and others they don't. For instance a few days ago (last time I used the machine) I was unable to run VLC media player. Software centre said it was there, but wouldn't launch it, terminal wouldn't launch it and right-clicking mp3 files and choosing VLC on the open with menu. I've just tried it again and it worked fine using open with. Cest la vie.

 

 The system test feature comes back with everything either passed or skipped.

 

 When trying to install software using terminal I often get errors.  

 

 I've have just tried, by way of example to install synaptic package manager using terminal, I entered the super user password and it prints “reading package lists... done”, then awaits for input with “cy tree...50%” which I imagine is something going wrong and my user name covers where “building dependency tree” should be. Synaptic has not been installed.

 

 I'm less inclined to think I have a hardware problem.

 

 Obviously I've tried searching for similar issues, running updates, upgrades, uninstalling things, reinstalling fresh etcetera, etcetera.  

 

 Is there anything that I can do to make Ubuntu at least usable? The laptop runs as well as can be expected using windows 7 on a different hard drive so I'm convinced it's something to do with Ubuntu. I've tried a full format and reinstall and the problem persists.

 

 Any help would be very much appreciated.

---

### Post by jimmy-frydkaer on 2015-03-28
Hello, and welcome to the Ubuntu Forums

The error you describe when booting the machine is like the scenario on my computer when making a clean install with encrypted LVM. Blank screen, while the monitor goes to sleep. Out of nowhere I tried typing my decrypt key and press Enter. After a few seconds the boot will continue. This error will persist until you install the proprietary graphics driver.

The heep of other errors you mention leads me to believe that you are running Ubuntu GNOME, which had just the scenario you describe when it first hit Alpha2-stage, lots of regressions.Only thing to do to mend this is to make another install media with the latest daily build. Download an iso file and burn it onto a dvd at the lowest possible speed to avoid errors on the disk.

---

### Post by Vladlenin5000 on 2015-03-29
No point in speculating and no matter how similar symptoms might look the underlining causes can be quite different.
Please start by posting the make/model and other specs of the said notebook. Then - and only then - can someone here start troubleshooting.

---

### Post by grahammechanical on 2015-03-29
> [COLOR=#000000]The hard drive was on its way out so I decided to replace it and do a clean Ubuntu 14.04LTS install. [/COLOR]

So with another hard drive and a newly installed OS you are still getting these problems. Could it be a memory fault? There is a memory test option in the Advanced options sub-menu of the boot menu.

---

### Post by Vega_31 on 2015-04-03
The laptop in question is an old Sony VPCEE2S1E. Full spec below from terminal. It had 2x4G RAM, I ran a memory test (hold shift after splash screen, select memory test option) and errors were found. I've since replaced the RAM with 2x2G and stability has improved however I still get the initial boot problem, now every time, and the system program problem detected immediately on log in, albeit less frequentley when running.

On booting, after the splash screen, the screen goes purple, then blank. I've discovered that pressing a key (normally the down arrow key) brings up a black screen (command line, not the purple Ubuntu screen) prompting me to enter my encryption key. Once I've entered it I see various processes starting and stopping before the Ubuntu log in screen loads. 

I can't help but think I'm being thick and missing something very obvious, but everything's obvious in hindsight I suppose.

```

    description: Notebook
    product: VPCEE2S1E (N/A)
    vendor: Sony Corporation
    version: C104LVHX
    serial: ********-*******
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=notebook family=VAIO sku=N/A uuid=********-****-****-****-************
  *-core
       description: Motherboard
       product: VAIO
       vendor: Sony Corporation
       physical id: 0
       version: N/A
       serial: N/A
       slot: SODIMM1
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: R0180Z5
          date: 07/09/2010
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int9keyboard int10video acpi usb smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Phenom(tm) II P820 Triple-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 6
          bus info: cpu@0
          version: AMD Phenom(tm) II P820 Triple-Core Processor
          serial: N/A
          slot: N/A
          size: 800MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr hw_pstate npt lbrv svm_lock nrip_save vmmcall cpufreq
        *-cache:0
             description: L1 cache
             physical id: 7
             slot: L1 Cache
             size: 384KiB
             capacity: 384KiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 8
             slot: L2 Cache
             size: 1536KiB
             capacity: 1536KiB
             capabilities: asynchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3
             physical id: 0
             slot: SODIMM1
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR3
             physical id: 1
             slot: SODIMM2
             size: 2GiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (ext gfx port 0)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:a000(size=4096) memory:f4100000-f41fffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RV710/M92 [Mobility Radeon HD 4530/4570/545v]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:45 memory:e0000000-efffffff ioport:a000(size=256) memory:f4100000-f410ffff memory:f4120000-f413ffff
           *-multimedia
                description: Audio device
                product: RV710/730 HDMI Audio [Radeon HD 4000 series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:46 memory:f4110000-f4113fff
        *-pci:1
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:6000(size=16384) memory:f3100000-f40fffff ioport:f0000000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 06
                serial: 54:42:49:2c:ea:5c
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:6000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
        *-pci:2
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 memory:f3000000-f30fffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: wlan0
                version: 01
                serial: 78:dd:08:ed:e5:d3
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.16.0-33-generic firmware=N/A ip=192.168.0.15 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:19 memory:f3000000-f300ffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:44 ioport:b038(size=8) ioport:b04c(size=4) ioport:b030(size=8) ioport:b048(size=4) ioport:b010(size=16) memory:f4208000-f42083ff
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
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f4207000-f4207fff
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
             configuration: driver=ehci-pci latency=64
             resources: irq:17 memory:f4208600-f42086ff
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
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f4206000-f4206fff
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
             configuration: driver=ehci-pci latency=64
             resources: irq:17 memory:f4208500-f42085ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 41
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:b000(size=16)
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
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:f4200000-f4203fff
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
             capabilities: pci subtractive_decode bus_master
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
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f4205000-f4205fff
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
             resources: irq:16 ioport:2000(size=16384) memory:f2000000-f2ffffff ioport:f1000000(size=16777216)
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
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f4204000-f4204fff
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
             configuration: driver=ehci-pci latency=64
             resources: irq:17 memory:f4208400-f42084ff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
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
          product: Family 10h Processor Link Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HGST HTS545050A7
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: AC90
             serial: TM85014C0412LL
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=0007246b
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: b1c27edb-b003-41fa-9c85-90f12ce87412
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2015-04-03 17:23:00 mount.fstype=ext2 mount.options=rw,relatime,stripe=4 mounted=2015-04-03 17:23:00 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 465GiB
                capacity: 465GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 465GiB
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW TS-L633C
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: SN01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@3:3
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
             configuration: sectorsize=512
```

---

### Post by mateojonsonguynn on 2015-04-03
I think you can rule out the two "System Program Problem Detected" messages. Whenever I start up either of my two Linux computers I get two of those messages, one in the top left and one in the center.

---

### Post by Vladlenin5000 on 2015-04-07
You Sony supports up to 8GB (2*4GB) of PC3-8500 RAM which is good. You mentioned errors were detected with the previous modules so you swapped them for a 2*2GB ones. Have you tested again with the new memory?
Here's the thing(s) you should know about memory tests in your laptop:
1) the test also checks the Video RAM when applicable; your Sony has a discrete ATI Mobility Radeon&#8482; HD 5145 Graphics with its own 512MB and the possibility of using additional reserved system memory;
2) Errors found with that test are in the memory itself in the vast majority of cases but sometimes also in the motherboard's chipset; in that cases changing memory won't help.

---

