---
title: "Upgrade to 12.04 , Slow Boot, Slow Desktop, Frequent System Errors"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by mdhicks1 on 2012-05-17
**My machine:**
Gateway ML6732 Notebook
Intel® Pentium® Dual-Core Mobile Processor T2370 
1 MB L2 Cache | 1.73 GHz | 533 MHz FSB 
3072 MB 667 MHz DDR2 SDRAM
Intel® Graphics Media Accelerator X3100

I was running 11.10 and things were great. Upgraded to 12.04, still fine.

But in the last two days, lots of problems:

**Problems**
* 5 minutes to boot to login screen
* 10-15 minutes from login screen to load desktop
* Constant system errors popping up (Apport)
* Generally slow and poorly responsive desktop environment 
* Several minutes for a program to load, though once a program is finally loaded, it works fine
* General spookiness (at this login, my indicator applet on the top right never showed up)

**Things I've already tried:**
Login with Unity 2D (Didn't help, maybe worse than before)
Wiped hard drive and did clean install with new live CD (no change)
Checked system processes for anything tying up CPU usage (nothing obvious)

**Output of some commands:**

```
lspci | grep -i VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
```

```
top -Sbn1 | head -n20
top - 06:10:18 up 42 min,  1 user,  load average: 1.09, 0.98, 1.55
Tasks: 159 total,   2 running, 157 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.5%us,  2.8%sy,  0.0%ni, 58.0%id, 30.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3088480k total,   913108k used,  2175372k free,    54716k buffers
Swap:  3135484k total,        0k used,  3135484k free,   465480k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3643 micah     20   0  511m 127m  31m R   16  4.2   5:29.39 firefox            
  989 root      20   0 77056  20m 7184 S    4  0.7   1:29.27 Xorg               
 2146 micah     20   0  253m  58m  24m S    4  1.9   0:53.79 compiz             
 5795 micah     20   0  2832 1140  860 R    4  0.0   0:00.02 top                
 4206 micah     20   0 89964  14m  10m S    2  0.5   0:01.43 gnome-terminal     
    1 root      20   0  3512 1972 1312 S    0  0.1   0:06.78 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.28 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.02 watchdog/0         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
   10 root      20   0     0    0    0 S    0  0.0   0:00.25 ksoftirqd/1        
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1    
```

```
sudo lshw
ghostlathe                
    description: Portable Computer
    product: ML6732 ()
    vendor: Gateway
    version: 3410125R
    serial: T0386V1005984
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=portable cpus=2 uuid=2869E1A8-8060-C4B9-1C85-D846A82433D5
  *-core
       description: Motherboard
       vendor: Gateway
       physical id: 0
       version: 93.13
       serial: QTFAMJ82305198
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 93.13
          date: 03/24/2008
          size: 108KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: uFCPGA2
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             physical id: 0
             serial: 757FD520
             slot: DIMM 1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             physical id: 1
             serial: 00004016
             slot: DIMM 2
             size: 2GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
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
             product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:f0000000-f00fffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0100000-f01fffff
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:f0604800-f0604bff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:f0400000-f0403fff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:f0200000-f02fffff ioport:f0700000(size=1048576)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:f0300000-f03fffff ioport:f0800000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:c0100000-c02fffff ioport:c0300000(size=2097152)
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1860(size=32)
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1880(size=32)
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18a0(size=32)
        *-usb:6
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0604c00-f0604fff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801HM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T40N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: JP01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:1c00(size=8) ioport:18d4(size=4) ioport:18d8(size=8) ioport:18d0(size=4) ioport:18e0(size=32) memory:f0604000-f06047ff
           *-disk
                description: ATA Disk
                product: WDC WD3200BEVT-2
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WXE408E75900
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00082299
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 5f3c9e25-942a-4a6a-840d-36704c828163
                   size: 295GiB
                   capacity: 295GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2012-05-16 21:43:53 filesystem=ext4 lastmountpoint=/ modified=2012-05-16 22:17:20 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-05-17 05:15:59 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3062MiB
                   capacity: 3062MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3062MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c0000000-c00000ff ioport:1c20(size=32)
     *-scsi
          physical id: 2
          bus info: usb@2:5
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdb
  *-battery
       description: Lithium Ion Battery
       product: MAL32b
       vendor: SANYO
       physical id: 1
       version: 2008/05/21
       serial: 1268
       slot: In the Back side
       capacity: 4800mWh
       configuration: voltage=11.1V
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1
       logical name: wlan0
       serial: 00:16:44:d4:f7:6e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.2.0-24-generic-pae firmware=N/A ip=192.168.2.2 link=yes multicast=yes wireless=IEEE 802.11bg
```

Thanks in advance.

---

### Post by fantab on 2012-05-17
First of all put the output of your commands in CODE, select the text and use # from your editor. It is difficult to go through the text otherwise. 

Also tell us more about the " Constant system errors popping up (Apport)"?

---

### Post by mdhicks1 on 2012-05-17
About the system errors, when using any application at all, I usually get a system error about once every 10 minutes or so.

When I click to see details, the error is always related to the application I'm using (Firefox, Rythmbox, Scribus, etc.), but the window continues trying to load the details forever and never shows me anything.

Sending the report takes several minutes also.

The application I'm using never seems to be affected by the errors.

---

### Post by mdhicks1 on 2012-05-17
Now it's giving errors whenever I try to take a screen shot, make a new folder, or plug in an external hard drive, telling me that this is a read only file system.

It tells me Firefox is already running and I must close existing process before starting a new one at boot.

Indicator applets in the right are still gone.

This is a BRAND NEW install of Pangolin. What the hell?

---

### Post by ezsit on 2012-05-17
Ever consider using Ubuntu 11.10 and try 12.04.1 in July when it comes out. The LTS releases usually stabilize after the July .1 release. Just a thought.

---

### Post by mdhicks1 on 2012-05-17
Just did a clean reinstall of 11.10. Same problems.

I booted the 12.04 live CD, and things are snappy and working like they're supposed to.

Does this mean my hard disk is bad?

The Live CD Disk Utility is giving me Warnings for Reallocated Sector Count and Current Pending Sector Count.

I'm running a Self-test now to see if I can get some more info...

---

### Post by zbeckerd on 2012-05-18
> **mdhicks1 said:**
> Just did a clean reinstall of 11.10. Same problems.

I booted the 12.04 live CD, and things are snappy and working like they're supposed to.

Does this mean my hard disk is bad?

The Live CD Disk Utility is giving me Warnings for Reallocated Sector Count and Current Pending Sector Count.

I'm running a Self-test now to see if I can get some more info...

Sounds like disk issues.  First I would replace the data cable to the drive even replacing it if in doubt.  Cheapest solution first.
I can reccomend buying a utility like spinrite if your disk already had a lot of data.  Buying a new drive is probably the most cost effective unless you have lots of disks to tune and repair.  In that case spinrite is a bargain. It even notices things like bad cabling.

---

### Post by mdhicks1 on 2012-05-22
Replacing the hard drive did the trick. It's running better than ever now. :)

---

