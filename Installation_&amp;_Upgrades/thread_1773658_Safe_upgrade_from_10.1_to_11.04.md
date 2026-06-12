---
title: "Safe upgrade from 10.1 to 11.04?"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by Pablo W on 2011-06-02
Hello.
I am planning to upgrade from Ubuntu 10.1 (maverick) to the latest version. I use an HP 5101 solid state netbook. 
In previous upgrades I had issues with my graphic card and wifi card too. I had to desperately post questions here. I have already learned that I should make a full backup and a list of software I am using BEFORE any attempt to upgrade.

My question for you, expert guys, is if you think there is a way to make sure I will have a flawless upgrade.

Details of the hardware are as follows:

```
pablo@pablo-netbook:~$ lshw
WARNING: you should run this program as super-user.
pablo-netbook             
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2003MiB
     *-cpu
          product: Intel(R) Atom(TM) CPU N280   @ 1.66GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8100000-e817ffff ioport:6000(size=8) memory:d0000000-dfffffff memory:e8180000-e81bffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:e8200000-e827ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:45 memory:e8280000-e8283fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=4096) memory:e8000000-e80fffff ioport:7f800000(size=2097152)
           *-network
                description: Wireless interface
                product: BCM43224 802.11a/b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth1
                version: 01
                serial: 00:26:82:38:d8:61
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.16.12 latency=0 multicast=yes wireless=IEEE 802.11
                resources: irq:16 memory:e8000000-e8003fff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:4000(size=8192) memory:e4000000-e7ffffff ioport:7fa00000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:e0000000-e3ffffff ioport:7fc00000(size=2097152)
           *-network
                description: Ethernet interface
                product: 88E8072 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:20:00.0
                logical name: eth0
                version: 10
                serial: 18:a9:05:93:3b:86
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 multicast=yes
                resources: irq:43 memory:e0000000-e0003fff ioport:2000(size=256) memory:7fc00000-7fc1ffff
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6020(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6040(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:6060(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:6080(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:e8284000-e82843ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:60a0(size=16)
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:13f0(size=8) ioport:15f4(size=4) ioport:1370(size=8) ioport:1574(size=4) ioport:60d0(size=16) memory:e8285000-e82853ff
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
pablo@pablo-netbook:~$ 
``` 

Thanks for your advice.

---

### Post by johngreth on 2011-06-02
I've always had better experiences with fresh installs than with upgrades. That being said, doing an upgrade may be the best option given the amount of work that would go into doing a fresh install.
There is always risk, but there isn't much more you can do after backing everything up. Upgrades are fairly reliable so I wouldn't worry too much about it.

---

### Post by mörgæs on 2011-06-02
> **Pablo W said:**
> 
...if you think there is a way to make sure I will have a flawless upgrade.



No, one can never be sure about that. You can try, but I would recommend a fresh install. 

By the way, why do you want to leave 10.10?

---

### Post by Pablo W on 2011-06-02
> **mörgæs said:**
> No, one can never be sure about that. You can try, but I would recommend a fresh install. 

By the way, why do you want to leave 10.10?

Thanks mörgæs and johngreth for your answers.
The reason why I want to upgrade is because I am assuming the new one is better. Am I wrong? Should I stick to maverick?

---

### Post by mörgæs on 2011-06-02
I can not answer this. Best is to try a live boot and see for yourself which release you like the most.

---

### Post by Pablo W on 2011-06-02
> **mörgæs said:**
> I can not answer this. Best is to try a live boot and see for yourself which release you like the most.

Takk mörgæs for the advice.
 I have earlier tested the new version booting from a usb stick. Although I can surf the net, there are many other things I could not test, due to lack of disk space. I was not able to change the settings to allow more disk space when running ubuntu from my pen drive.

---

### Post by blauendonau on 2011-06-02
Upgrades are somewhat iffy, especially if you've got a heavily modified system. The transition to Natty also seems to be less reliable than usual (this release was somewhat rushed, resulting in more bugs). That being said, if an upgrade is successful, it's much less hassle overall because your files, settings, etc, are kept and don't need to be readded/reinstalled.

If the upgrade fails, then you can do a fresh install and you won't lose anything compared to if you had done a fresh install immediately. This is assuming that all your files are backed up to an external medium, of course.

Personally, I would not advise moving to Natty, but opinions vary on that subject. Keep in mind that 10.10 is supported for another year, so there's no big rush to upgrade. I suggest waiting for Natty to mature or for 11.10 to come out, and then see what you want to do.

---

### Post by Pablo W on 2011-06-03
Thank you all for your advices.
Taking into account your comments, I have decided to postpone the upgrade for a while.

Cheers.

---

### Post by ubvin on 2011-06-07
Hi all,
       
Am new to this forum. I need to clarify a doubt regarding serial port. My question is "Usually we represent COM1 port as /dev/ttyS0. Similarly how we represent super IO controlled serial port?" Port is enabled but cannot be able to access it for data transmission. Kindly help me.....
 
Thanks in advance.

---

### Post by mörgæs on 2011-06-07
Hi, welcome to the fora.

Does this help?
[http://expat.dyndns.org/2011/05/10/debugging-lpcxpresso/](http://expat.dyndns.org/2011/05/10/debugging-lpcxpresso/)

If not then it is best to open a new thread, for example here:
[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

---

