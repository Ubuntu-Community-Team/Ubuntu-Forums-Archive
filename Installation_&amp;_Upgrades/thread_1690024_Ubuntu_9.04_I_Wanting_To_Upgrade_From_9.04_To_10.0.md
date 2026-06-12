---
title: "Ubuntu 9.04: I Wanting To Upgrade From 9.04 To 10.04"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by SexySara on 2011-02-17
I am using 9.04 right now and want to upgrade to 10.04 beings it is a  LTS version. However, when 10.04 is installing, my laptop just shuts  down all together and even though its plugged in; the power light goes  off as well. Then I have to unplug my laptop and then plug it back it  again. That leads me to think that something is not working right with  my laptop, I dunno. I am trying to install the i386 version to fit my  32bit Intel laptop. Maybe I am doing something wrong, I dunno... here is  my lshw code for more info. Maybe I need to upgrade the ram to 2gigs  with better latency instead of using the stock 1gig. I don't know what  to do. Maybe flash the bios? Help please lol!

I am gonna try the info from this link and see if it works, if it does then I will let you know.
[http://ubuntuforums.org/showthread.php?t=1043129&page=2](http://ubuntuforums.org/showthread.php?t=1043129&page=2)

```
~$ sudo lshw
anonymous                 
    description: Computer
    product: Aspire 5315
    vendor: Acer
    version: V1.33
    serial:
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: cpus=1 uuid=EE743358-F0E8-316B-438C-001B38DC9723
  *-core
       description: Motherboard
       product: Acadia
       vendor: Acer
       physical id: 0
       version: V1.33
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.33 (03/15/2008)
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect  socketedrom edd int13floppynec int13floppytoshiba int13floppy360  int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video  acpi usb
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: 0x48594D503131325336344350362D59352020
             vendor: 0xAD00000000000000
             physical id: 0
             serial: 
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 1
             serial: NO DIMM
             slot: DIMM2
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU          550  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1f
          bus info: cpu@0
          version: 6.6.1
          serial: 
          slot: uPGA-478
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae  mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr  sse sse2 ss tm pbe x86-64 constant_tsc up arch_perfmon pebs bts pni  dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
        *-cache:0
             description: L2 cache
             physical id: 20
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 22
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
     *-cache
          description: L1 cache
          physical id: 21
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0

```**EDIT**

Perfect fix and perfect BIOS flash!

```
~$ sudo lshw
anonymous                 
    description: Computer
    product: Aspire 5315
    vendor: Acer
    version: V1.43
    serial: 
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: cpus=1 uuid=EE743358-F0E8-316B-438C-001B38DC9723
  *-core
       description: Motherboard
       product: Acadia
       vendor: Acer
       physical id: 0
       version: V1.43
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.43 (06/25/2008)
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect  socketedrom edd int13floppynec int13floppytoshiba int13floppy360  int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video  acpi usb
```

---

### Post by drs305 on 2011-02-17
How are you trying to do the upgrade? You cannot directly upgrade from 9.04 to 10.04 online. You can upgrade to 9.10 and then 10.04 if you are trying to do it online, or you can install 10.04 directly from the CD/DVD.

The only time you can skip releases via online upgrades is when you go from one LTS (e.g. 8.04) to another (10.04).

---

### Post by SexySara on 2011-02-18
It was a BIOS bug and I just flashed the BIOS and everything works great. I have the 9.10 and 10.04 CD's and when I tried to install them, the system would crash. After doing some reading, I decided to flash the BIOS and now I am successfully using 10.04.

---

