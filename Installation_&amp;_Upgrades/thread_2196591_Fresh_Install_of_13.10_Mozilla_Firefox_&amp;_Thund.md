---
title: "Fresh Install of 13.10 Mozilla Firefox &amp; Thunderbird CRASHES over &amp; over"
date: 2013-12-30
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2013-12-30
What Repositories should we allow besides Canonical for v13.10 updates?

Any suggestions regarding the CRASHES? Mozilla Firefox and Thunderbird completely unstable. Neither will run past a minute without Crashing. Also, should Crash Reports ask for your Login Credentials everytime??? Sounds like a spoof to access our username and password if you ask me.

Is v13.10 a Security Threat ?!?!?

Thanks!
Rick

---

### Post by vasa1 on 2013-12-30
I think you have a lot of other problems, maybe hardware issues, based on some of your other posts. If you feel uncomfortable with "v13.10" just use some other distro or Windows.

---

### Post by Rick St. George on 2013-12-30
Other posts have to deal with other computers, as I have 4 with different versions of Ubuntu (K,X,studio) and one trashed Desktop due to NO Drivers for SIS video. This computer referred to in this posting, has the following.

Intel Pent. 2800 Mhz
1GB Ram
Radeon 7000 64MB AGP w/DVI & Svideo out
1 Generic DVD drive (operable as it installed ubuntu)

I would give a complete Printout of LSHW, but can't even get LibreOffice to run.

Any suggestions? Is this the correct forum to Post Problems with Beta Releases?

AND NO - Reverting to Windows is NOT an Option. But I may roll it back to v12.04 and get 569 updates, most of which are not applicable as I have no Printer, Running one flavor -don't need Gnome compats, etc.

---

### Post by Rick St. George on 2013-12-30
Full Post of Computer Periphials;
For what its worth ...

    ```
description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1019MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.7
          size: 2800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:d0000000-d7ffffff
        *-pci:0
             description: PCI bridge
             product: 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:9000(size=4096) memory:e0000000-e1ffffff memory:d8000000-dfffffff
           *-display
                description: VGA compatible controller
                product: RV100 [Radeon 7000 / Radeon VE]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:16 memory:d8000000-dfffffff ioport:9000(size=256) memory:e1000000-e100ffff memory:e0000000-e001ffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:b800(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:b000(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:b400(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:e2100000-e21003ff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:a000(size=4096) memory:e2000000-e20fffff
           *-network
                description: Ethernet interface
                product: 82801DB PRO/100 VE (CNR) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 82
                serial: 00:20:ed:73:72:45
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.2.52 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
                resources: irq:20 memory:e2001000-e2001fff ioport:a400(size=64)
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16) memory:40000000-400003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:5000(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:c000(size=256) ioport:c400(size=64) memory:e2101000-e21011ff memory:e2102000-e21020ff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```
------------------------

See any hardware problems or incompatibles?

Thanks!

---

### Post by mörgæs on 2013-12-30
Have you tried running **memtest** for a few hours?

---

### Post by Rick St. George on 2013-12-30
No !

---

### Post by Rick St. George on 2013-12-31
After looking at the P/O above, it shows 1019 MiB (what is that Men In Black?),
But I have 1.5 GB installed. Will pull them and take a closer look, and report back.
NOTE: MemTest is confirmed on computer startup.

Rick '-)

---

### Post by Rick St. George on 2013-12-31
I knew I had 3 Mem-sticks, but 2 were 333/512, and 1 was 400/512. Removed the 400 Mhz mem-chip and ....

No Crash as of yet, with both Mozilla Firefox and Thunderbird open.

Will consider this CASE CLOSED ! ! !

---

