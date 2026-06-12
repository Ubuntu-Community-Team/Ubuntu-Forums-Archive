---
title: "Forcepae: Unable to boot live or install from 14.04 - blank screen"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by megsona on 2014-04-22
I have an old Toshiba R100 (non-PAE Pentium M) which has been running 12.04 happily. When I read 14.04 now included the forcepae fix as a boot option I burnt a Lubuntu DVD and gave it a go.

I'm adding the forcepae option and getting the 'warning: forcing pae in cpu' message as you'd expect so I think that's all fine. I then get the Lubuntu 14.04 blue loading screen with dots below followed by two messages, 

"starting lightdm display manager"
"stopping send an event to indicate plymouth is up".

Then the screen goes blank and I can hear the dvd drive spin down, additionally ctrl+alt+f1 doesn't give me a tty terminal. I have to power off with the button.

I've tried Xubuntu and Ubuntu as well, Xubuntu does the same, ends with a freeze on a blank screen. Ubuntu gives me the 'running in low graphics mode' dialog, none of the options get me any further though (either another blank freeze or returned to that dialog).

Be glad of any advice,

Thanks.

Here's my lshw output for starters,

```
computer
    description: Notebook
    version: PPR10E-04M8Z-EN
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.60
          date: 05/17/2005
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing vesa cdboot bootselect pcmciaboot edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp biosbootspecification netboot
     *-cpu:0 DISABLED
          description: CPU [empty]
          vendor: Intel Corporation
          physical id: 4
          slot: uFC-PGA Socket
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 64KiB
             capacity: 64KiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 1MiB
             capacity: 1MiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 1280MiB
          capacity: 1280MiB
        *-bank:0
             description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2014-01-06 21:08+0000X-Generator: Launchpad (build 16877) SDRAM Synchronous
             physical id: 0
             slot: System 0
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous
             physical id: 1
             slot: DIMM 1
             size: 1GiB
             width: 64 bits
     *-cpu:1
          product: Intel(R) Pentium(R) M processor 1000MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.9.5
          size: 1GHz
          capacity: 1GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2 cpufreq
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:c0000000-cfffffff
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:dff00000-f7ffffff memory:50000000-500fffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CyberBlade XP4m32
                vendor: Trident Microsystems
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 91
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=8
                resources: memory:f0000000-f7ffffff memory:efc00000-efffffff memory:e0000000-e7ffffff memory:dfff8000-dfffffff memory:50000000-5003ffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:efe0(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:ef80(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:11 memory:50100000-501003ff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:dfd00000-dfdfffff memory:54000000-57ffffff
           *-network:0
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 83
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                resources: irq:11 memory:dfdff000-dfdfffff ioport:cf40(size=64)
           *-network:1
                description: Wireless interface
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
                physical id: a
                bus info: pci@0000:02:0a.0
                logical name: eth1
                version: 04
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=[REMOVED] latency=64 link=yes maxlatency=34 mingnt=2 multicast=yes wireless=IEEE 802.11b
                resources: irq:11 memory:dfdfe000-dfdfefff
           *-pcmcia
                description: CardBus bridge
                product: ToPIC100 PCI to Cardbus Bridge with ZV Support
                vendor: Toshiba America Info Systems
                physical id: b
                bus info: pci@0000:02:0b.0
                version: 33
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=0 maxlatency=5 mingnt=128
                resources: irq:11 memory:58000000-58000fff ioport:c400(size=256) ioport:c000(size=256) memory:54000000-57ffffff memory:5c000000-5fffffff
           *-generic UNCLAIMED
                description: System peripheral
                product: SD TypA Controller
                vendor: Toshiba America Info Systems
                physical id: d
                bus info: pci@0000:02:0d.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
                resources: memory:dfd00000-dfd001ff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16) memory:50100400-501007ff
           *-disk
                description: ATA Disk
                product: KingSpec KSD-CF1
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 2012
                serial: [REMOVED]
                size: 29GiB (31GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000502e5
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2014-04-02 19:00:01 filesystem=ext4 lastmountpoint=/ modified=2014-04-02 19:13:49 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2014-04-21 23:46:39 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1277MiB
                   capacity: 1277MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1277MiB
                      capabilities: nofs
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:11 ioport:1000(size=256) ioport:1880(size=64) memory:50100800-501009ff memory:50100a00-50100aff
        *-communication
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic bus_master cap_list
             configuration: driver=snd_intel8x0m latency=0
             resources: irq:11 ioport:1400(size=256) ioport:1800(size=128)
     *-scsi:0
          physical id: 2
          bus info: usb@1:2
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW GH50N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             logical name: /media/Lubuntu 14.04 LTS i386
             version: B104
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /media/Lubuntu 14.04 LTS i386
                capabilities: partitioned partitioned:dos
                configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 signature=0e838d4d state=mounted
              *-volume UNCLAIMED
                   description: Hidden HPFS/NTFS partition
                   physical id: 1
                   capacity: 682MiB
                   capabilities: primary bootable hidden
     *-scsi:1
          physical id: 3
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SanDisk SDP3B-12
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: Vdg
             serial: [REMOVED]
             size: 1221MiB (1280MB)
             capabilities: removable
             configuration: ansiversion=5
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 1221MiB (1280MB)
                capabilities: partitioned partitioned:dos
                configuration: signature=000b8fa4
              *-volume
                   description: Windows FAT volume
                   vendor: mkdosfs
                   physical id: 1
                   logical name: /dev/sdb1
                   version: FAT32
                   serial: [REMOVED]
                   size: 1214MiB
                   capacity: 1214MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat
  *-battery
       description: Lithium-Polymer Battery
       product: L6113A
       vendor: TOSHIBA
       physical id: 1
       version: 09/04/03
       serial: [REMOVED]
       slot: 1st Battery
       configuration: voltage=10.8V
```

---

### Post by mörgæs on 2014-04-22
Have you tried the same option for the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

By the way, Lubuntu fits to a CD. There's no need for a DVD.

---

### Post by megsona on 2014-04-22
Hi thanks for the reply, yes, I tried the lubuntu alternate iso while it was still in beta 2 (not since). As I recall I could go through the text-based setup ok but I never got to a desktop. After the 'Lubuntu 14.04' splash screen with activity indicator dots below I got the blank screen freeze.

I'm all out of CD's at the moment, DVD-RW's I've got plenty...

---

### Post by kalehrl on 2014-04-22
AFAIK, force pae is intended for processors which do have pae capability but do not advertise it in the cpu flags.
Are you sure your processor supports pae?
You've got plenty of RAM for the installation so that's not the cause of your problems.

---

### Post by megsona on 2014-04-22
hi kalehrl, that seems like a possibility. It seems difficult to determine if that is the case though. Obviously if a cpu reports the pae flag then that's fine, but of the ones that don't how can we know if they *really* do but just aren't saying?

Is there some test I can do beyond just checking for the flag in cpuinfo?

---

### Post by kalehrl on 2014-04-23
Check this out:
[https://help.ubuntu.com/community/Lubuntu-fake-PAE#Test](https://help.ubuntu.com/community/Lubuntu-fake-PAE#Test)
There was also a mention of non-pae kernel build on Lubuntu mailing list but I don't know how far that has gone.

---

### Post by mörgæs on 2014-04-23
[http://ubuntuforums.org/showthread.php?t=2216356](http://ubuntuforums.org/showthread.php?t=2216356)

Until that the easiest solution is probably LXLE or Bodhi Linux.

---

### Post by megsona on 2014-04-23
Thanks for the links and advice, I'll follow those up.

Had also read that debian still offer a non-pae kernel, so may give that a try...

---

### Post by megsona on 2014-04-23
here's my output from cpuid

```
 eax in    eax      ebx      ecx      edx
00000000 00000002 756e6547 6c65746e 49656e69
00000001 00000695 00000816 00000180 a7e9f9bf
00000002 02b3b001 00000000 00000000 2c043087
80000000 80000004 00000000 00000000 00000000
80000001 00000000 00000000 00000000 00000000
80000002 20202020 20202020 65746e49 2952286c
80000003 6e655020 6d756974 20295228 7270204d
80000004 7365636f 20726f73 30303031 007a484d

Vendor ID: "GenuineIntel"; CPUID level 2

Intel-specific functions:
Version 00000695:
Type 0 - Original OEM
Family 6 - Pentium Pro
Model 9 - 
Stepping 5
Reserved 0

Brand index: 22 [not in table]
Extended brand string: "        Intel(R) Pentium(R) M processor 1000MHz"
CLFLUSH instruction cache line size: 8

Feature flags a7e9f9bf:
FPU    Floating Point Unit
VME    Virtual 8086 Mode Enhancements
DE     Debugging Extensions
PSE    Page Size Extensions
TSC    Time Stamp Counter
MSR    Model Specific Registers
MCE    Machine Check Exception
CX8    COMPXCHG8B Instruction
SEP    Fast System Call
MTRR   Memory Type Range Registers
PGE    PTE Global Flag
MCA    Machine Check Architecture
CMOV   Conditional Move and Compare Instructions
FGPAT  Page Attribute Table
CLFSH  CFLUSH instruction
DS     Debug store
ACPI   Thermal Monitor and Clock Ctrl
MMX    MMX instruction set
FXSR   Fast FP/MMX Streaming SIMD Extensions save/restore
SSE    Streaming SIMD Extensions instruction set
SSE2   SSE2 extensions
TM     Thermal monitor
31     reserved

TLB and cache info:
b0: unknown TLB/cache descriptor
b3: unknown TLB/cache descriptor
02: Instruction TLB: 4MB pages, 4-way set assoc, 2 entries
87: unknown TLB/cache descriptor
30: unknown TLB/cache descriptor
04: Data TLB: 4MB pages, 4-way set assoc, 8 entries
2c: unknown TLB/cache descriptor
megsona@R100:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 9
model name	: Intel(R) Pentium(R) M processor 1000MHz
stepping	: 5
microcode	: 0x7
cpu MHz		: 600.000
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2
bogomips	: 1197.04
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:


```

The second last line doesn't look too promising...

---

### Post by megsona on 2014-04-24
Just to close this thread off, I torrented the live lxde version of debian 7.4. The boot menu from that offers a 486 pae option as well as a 686 non-pae. Went for the 486 and it installed no problem.  Quite happy with that.

Thanks for your help.

---

### Post by sudodus on 2014-04-24
> **megsona said:**
> here's my output from cpuid

```
 eax in    eax      ebx      ecx      edx
00000000 00000002 756e6547 6c65746e 49656e69
[COLOR=#ff0000]00000001 00000695 00000816 00000180 a7e9f9bf[/COLOR]
00000002 02b3b001 00000000 00000000 2c043087
80000000 80000004 00000000 00000000 00000000
80000001 00000000 00000000 00000000 00000000
80000002 20202020 20202020 65746e49 2952286c
80000003 6e655020 6d756974 20295228 7270204d
80000004 7365636f 20726f73 30303031 007a484d

```
The red line is the same as for another Pentium M which is PAE capable, but that CPU has a higher frequency, 1.4 GHz. This CPU is very slow and is probably quite old, so an early version of Pentium M.

Maybe it is not working properly with PAE, maybe the problem is due to the old Intel graphics.
> 
```

Vendor ID: "GenuineIntel"; CPUID level 2

Intel-specific functions:
Version 00000695:
Type 0 - Original OEM
Family 6 - Pentium Pro
Model 9 - 
Stepping 5
Reserved 0

Brand index: 22 [not in table]
[COLOR=#ff0000]Extended brand string: "        Intel(R) Pentium(R) M processor **1000**MHz[/COLOR]"
CLFLUSH instruction cache line size: 8

Feature flags a7e9f9bf:
FPU    Floating Point Unit
VME    Virtual 8086 Mode Enhancements
DE     Debugging Extensions
PSE    Page Size Extensions
TSC    Time Stamp Counter
MSR    Model Specific Registers
MCE    Machine Check Exception
CX8    COMPXCHG8B Instruction
SEP    Fast System Call
MTRR   Memory Type Range Registers
PGE    PTE Global Flag
MCA    Machine Check Architecture
CMOV   Conditional Move and Compare Instructions
FGPAT  Page Attribute Table
CLFSH  CFLUSH instruction
DS     Debug store
ACPI   Thermal Monitor and Clock Ctrl
MMX    MMX instruction set
FXSR   Fast FP/MMX Streaming SIMD Extensions save/restore
SSE    Streaming SIMD Extensions instruction set
SSE2   SSE2 extensions
TM     Thermal monitor
31     reserved

TLB and cache info:
b0: unknown TLB/cache descriptor
b3: unknown TLB/cache descriptor
02: Instruction TLB: 4MB pages, 4-way set assoc, 2 entries
87: unknown TLB/cache descriptor
30: unknown TLB/cache descriptor
04: Data TLB: 4MB pages, 4-way set assoc, 8 entries
2c: unknown TLB/cache descriptor
megsona@R100:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 9
model name    : Intel(R) Pentium(R) M processor 1000MHz
stepping    : 5
microcode    : 0x7
cpu MHz        : 600.000
cache size    : 1024 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2
bogomips    : 1197.04
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:


```> 

The second last line doesn't look too promising...

This is normal when running a non-pae kernel. Only when running a PAE kernel, you will see 36 bits physical address size.

> **megsona said:**
> Just to close this thread off, I torrented the live lxde version of debian 7.4. The boot menu from that offers a 486 pae option as well as a 686 non-pae. Went for the 486 and it installed no problem.  Quite happy with that.

Thanks for your help.

I'm glad debian 7.4 with lxde works for you :-)

As mörgæs wrote, LXLE or Bodhi would probably work for you too.

We are not sure, if the problem is caused by problems with PAE or with the graphics. If you want to explore it further (not installing, only testing from a live CD/DVD/USB drive), I suggest trying with the two [boot options]("https://help.ubuntu.com/community/BootOptions") **forcepae text** at the same time

And if you test it, please let us know the result: Will the computer run in text mode?

---

### Post by megsona on 2014-04-24
Thanks for your continued suggestions.

I've now tried Lubuntu 14.04 with **forcepae text** and I can report success. My laptop boots without issue to a command prompt. So, I then did a cat /proc/cpuinfo and it reports 36 bit physical, 32 bit virtual.

From this I assume we can discount a pae problem, I'd like to look further down the graphics avenue.

Again, if you have any guidance I'd be glad to continue the investigation.

---

### Post by sudodus on 2014-04-25
I'm glad that your old Pentium M works with forcepae :-)

Often problems with old Intel graphics can be solved with UXA acceleration in newer versions of Lubuntu (13.10 and 14.04 LTS). See these links

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics)
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

