---
title: "Dual Boot Ubuntu 14 with added Budgie stalls in installation."
date: 2018-02-10
forum: Installation &amp; Upgrades
---

### Post by Richard_York on 2018-02-10
I'm playing with an old Toshiba laptop (maybe 10 yrs old) which I've been given, hopefully learning by mistakes before messing up a dual-boot of adding Ubuntu 16 or 17 to existing Windows10 on our new 2nd hand desktop, only 5 years old.

The Toshiba installed Ubuntu 14.04 quite happily. I can't get it to accept 16, it gets as far as the box where you fill in your username, when it refuses to respond to any entry, despite having accepted the correct keyboard identification.

So I tried instead adding "Budgie remix" along with 14.04, for the sake of trying a dual boot installation, see how it works out.

 It's accepted everything, copied lots of files,  got as far as "configuring target system", when the progress line has been stuck under the "e" of "system" for about two hours now. 
It's not a very powerful computer. I can't quote figures, with apologies, as it's not letting me look at anything other than the installation screen and the revolving disk symbol just now, but I'm wondering if it's simply asking too much for it to do both things at once, so I should accept it's not going to handle it, or whether to leave it longer.

Thanks for any help.

---

### Post by kansasnoob on 2018-02-10
My best guess is that the 16.04 kernel is not playing well with that hardware. If you can boot into Ubuntu 14.04 would you please post the output of:

```
uname -a
```

That will show us which kernel version you have running in 14.04. It could vary depending on which point release iso was used for installation. If it was the 14.04.5 iso then you should have the 16.04 kernel and X-stack already running, and if that's the case you may have better results using the 16.04.1 iso instead of 16.04.2 or 16.04.3. I know it gets confusing but the LTS versions have point releases that use HWE:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

That's at least a start so we can try to narrow this down. It may also help to have more detailed info about the exact model of laptop if you have that available. The following command will also provide detailed hardware info:

```
sudo lshw
```

---

### Post by Richard_York on 2018-02-10
Thanks, and you're right, it is confusing :-) 
"uname -a"  gives me: Linux richard-Satellite-Pro-A300 4.4.0-31-generic #50~14.04.1-Ubuntu SMP Wed Jul 13 01:06:37 UTC 2016 i686 i686 i686 GNU/Linux

I hope I've copied this by eye correctly! (Using a different laptop to type this). I trust this tells you a lot more than it tells me.

"sudo lshw" gives me... wow, a seriously long amount of information, I need to switch computers and copy & paste to get this to you. Back soon. I have to say that the output at this point is well beyond my comprehension!

---

### Post by Richard_York on 2018-02-10
... "sudo lshw" gives: ```
richard-satellite-pro-a300
    description: Notebook
    product: Satellite Pro A300 ()
    vendor: TOSHIBA
    version: PSAJ1E-01200XEN
    serial: 58179811W
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=C0C1A0B2-20F5-DB11-8C79-001E6862B9C8
  *-core
       description: Motherboard
       product: Satellite Pro A300
       vendor: TOSHIBA
       physical id: 0
       version: Not Applicable
       serial: 58179811W
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V4.20
          date: 01/05/2009
          size: 100KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: U2E1
          size: 800MHz
          capacity: 4096MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
          configuration: id=1
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
             capacity: 4MiB
             capabilities: burst internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: SODIMM000
             vendor: Mfg 0
             physical id: 0
             serial: 1234-B0
             slot: M1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: SODIMM001
             vendor: Mfg 1
             physical id: 1
             serial: 1234-B1
             slot: M2
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1067MHz
          capacity: 1067MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
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
             resources: irq:29 memory:f0000000-f00fffff memory:d0000000-dfffffff ioport:1800(size=8)
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
             version: 03
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
             version: 03
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
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:f0604000-f06043ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:28 memory:f0400000-f0403fff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:80000000-801fffff ioport:80200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) memory:f0200000-f02fffff ioport:80400000(size=2097152)
           *-network
                description: Ethernet interface
                product: 88E8072 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 16
                serial: 00:1e:68:62:b9:c8
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:27 memory:f0200000-f0203fff ioport:2000(size=256) memory:f0220000-f023ffff
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:4000(size=4096) memory:80600000-807fffff ioport:80800000(size=2097152)
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
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
             version: 03
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
             version: 03
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
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f0604400-f06047ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:f0300000-f03fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 1
                bus info: pci@0000:0a:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32
                resources: irq:16 memory:f0301000-f0301fff memory:f0300000-f03007ff
           *-generic
                description: SD Host controller
                product: Integrated MMC/SD Controller
                vendor: O2 Micro, Inc.
                physical id: 1.2
                bus info: pci@0000:0a:01.2
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=32
                resources: irq:16 memory:f0300800-f03008ff
           *-storage UNCLAIMED
                description: Mass storage controller
                product: Integrated MS/xD Controller
                vendor: O2 Micro, Inc.
                physical id: 1.3
                bus info: pci@0000:0a:01.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm cap_list
                configuration: latency=32
                resources: memory:f0302000-f0302fff
        *-isa
             description: ISA bridge
             product: 82801HM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
        *-ide:1
             description: IDE interface
             product: 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1c00(size=8) ioport:18f4(size=4) ioport:18f8(size=8) ioport:18f0(size=4) ioport:18e0(size=16) ioport:18d0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:80a00000-80a000ff ioport:1c20(size=32)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM UJ-850S
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.40
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MK1646GS
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 3M
             serial: 489MCAJRT
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=596563d6
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 7b74366e-2da4-4c53-92b2-f53353c633a7
                size: 75GiB
                capacity: 75GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2018-02-09 21:12:56 filesystem=ext4 lastmountpoint=/ modified=2018-02-10 13:31:37 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2018-02-10 09:13:50 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 73GiB
                capacity: 73GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2037MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 71GiB
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@2:4
       logical name: wlan0
       serial: 00:16:44:b3:29:89
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=4.4.0-31-generic firmware=N/A ip=192.168.1.147 link=yes multicast=yes wireless=IEEE 802.11bg
richard@richard-Satellite-Pro-A300:~$ uname -a^C
richard@richard-Satellite-Pro-A300:~$ uname -a
```

---

### Post by Richard_York on 2018-02-10
While we're here, I see it keeps mentioning both 32bits and 64bits as width of various components. I'm now puzzled whether this is a 32bit or a 64bit machine. I've been installing 32 bit versions of what I've tried on it so far.
Thanks for any help, especially in very basic language.

---

### Post by kansasnoob on 2018-02-10
You could run amd64 on that machine but with only 2GB of RAM you probably wouldn't see any notable improvement. Of course 18.04 iso images will not be available in 32 bit so since you're playing around it can't hurt to try the amd64 images rather than the i386 images. We can expect more and more apps to drop 32 bit support in the not-so-distant future

As to the problems with 16.04 images I'm fairly sure it is a kernel problem that began with 17.04 and 16.04.3. I'm not sure if it was fixed in 17.10.1 or not. The easiest thing to do would be to try booting/installing from a 16.04.1 image:

[http://old-releases.ubuntu.com/releases/16.04.1/](http://old-releases.ubuntu.com/releases/16.04.1/)

That's the link for Ubuntu but with those specs you might want to try something lighter like Lubuntu, Ubuntu MATE, or Xubuntu.

[http://cdimage.ubuntu.com/xubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/16.04/release/)

[http://cdimage.ubuntu.com/lubuntu/releases/16.04.1/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.04.1/release/)

[http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04.1/release/](http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04.1/release/)

Just be sure to use the 16.04.1 images because 16.04.2 is HWE EOL.

An optional light desktop environment for Ubuntu is GNOME Flashback w/Metacity:

[https://ubuntuforums.org/showthread.php?t=2302432](https://ubuntuforums.org/showthread.php?t=2302432)

There's a bit of info about that specific kernel problem here:

[https://askubuntu.com/questions/970679/drm-i915-gpu-hang-in-artful-advark-17-10?answertab=votes#tab-top](https://askubuntu.com/questions/970679/drm-i915-gpu-hang-in-artful-advark-17-10?answertab=votes#tab-top)

It does seem to effect both Intel GM965 and GMA X3100 graphics chips.

---

### Post by Richard_York on 2018-02-11
Thank you very much - lots of useful homework here, but stuff I can hopefully try even though I don't understand what or why I'm doing it! (eg at present I admit that neither HWE EOL nor most of the information in the forum links means anything to me, but small bits of it may do in time.)

 As you say, I'm playing to see what works, so if it all falls over I can start again with something else. 
Knowing that the machine will take 64bit is useful. I got the impression that trying to load a 64bit image from a working 32bit system in order to try the 64bit system out is doomed to failure, so wonder if that step is surmountable... only one way to find out!
Just started downloading Xubuntu 64bit.

---

### Post by kansasnoob on 2018-02-11
> **Richard_York said:**
> Thank you very much - lots of useful homework here, but stuff I can hopefully try even though I don't understand what or why I'm doing it! (eg at present I admit that neither HWE EOL nor most of the information in the forum links means anything to me, but small bits of it may do in time.)

It all seems much more complicated than it is. It just boils down to understanding Ubuntu's release cycle. Every two years Ubuntu releases an LTS (long term support) release that's supported for 5 years, eg; 12.04, 14.04, 16.04, 18.04. The version numbers simply reflect year and month released, 12.04 = April 2012, 14.04 = April 2014, 16.04 = April 2016, 18.04 = April 2018.

In between LTS releases Ubuntu has interim or "normal" releases at 6 month intervals that are only supported for 9 months. The only currently supported interim release is 17.10 (released October 2017) since 17.04 just reached EOL (end of life) in January. I'd personally never use an interim release on a production machine because release upgrades can and sometimes do fail.

So, back to the LTS releases. Each LTS release also has 5 point releases, the first usually coming in August following the initial release. Like 14.04 was released in April 2014 and it's already had its 5 point releases - 14.04.1, 14.04.2, 14.04.3, 14.04.4, and 14.04.5. The first point release still uses the original kernel series, but the second, third, and fourth point releases use the most recent interim releases kernel series. The fifth point release ends up using the next LTS versions kernel series. That's all reflected in this 14.04 kernel support graph:

[https://wiki.ubuntu.com/Kernel/Support?action=AttachFile&do=view&target=14.04.x+Ubuntu+Kernel+Support+Schedule.svg](https://wiki.ubuntu.com/Kernel/Support?action=AttachFile&do=view&target=14.04.x+Ubuntu+Kernel+Support+Schedule.svg)

You can see there that the original kernel series is supported throughout the entire life cycle of the release but the kernel series used in the 2nd, 3rd, and 4th point releases reach end-of-life (EOL) much sooner requiring upgrade to the 5th point releases kernel series. Actually the X-stack gets upgraded along with the kernel, this is all referred to as HWE (hardware enablement) with the intention of supporting the latest hardware:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

They changed things up in 16.04, actually shortening the support cycle of the HWE stacks used in the 2nd, 3rd, and 4th point releases:

[https://wiki.ubuntu.com/Kernel/Support?action=AttachFile&do=view&target=16.04.x+Ubuntu+Kernel+Support+Schedule.svg](https://wiki.ubuntu.com/Kernel/Support?action=AttachFile&do=view&target=16.04.x+Ubuntu+Kernel+Support+Schedule.svg)

So the smart bet is on always using the first point release installation media (aka; live image) to avoid the shorter HWE lifespan unless the latest kernel and X support is required for your specific hardware. Of course if the first point release iso is not yet available then you would use the initial release media.

Is any of that clear as mud? Or just more confusing?

 > As you say, I'm playing to see what works, so if it all falls over I can start again with something else. 
Knowing that the machine will take 64bit is useful. I got the impression that trying to load a 64bit image from a working 32bit system in order to try the 64bit system out is doomed to failure, so wonder if that step is surmountable... only one way to find out!
Just started downloading Xubuntu 64bit.

That's a super smart strategy! I do a lot of testing using spare machines before I commit any production machines to any new change. I frequently blow things up and have to start all over :oops:

---

### Post by Richard_York on 2018-02-11
Thank you for this patient explanation. It does help!
.... then, just when I was feeling newly confident, I got to the bit where you said you frequently blow things up....  !!

I think I take a step forward each time I really need to change something, and it all starts making more sense (up to a point!). Then, because I'm a user of computers rather than an enthusiast for the sake of it, once the system's behaving, I let it get on with things, so that each time I need to come back and update stuff, everything's moved on, and I've also forgotten half of what I learned last time. 

Meanwhile, I'm now using Xubuntu 16 here, dual booted on this tiny laptop alongside 14.04 Ubuntu, thanks to your help. Slow, but they both work. So I'm feeling more confident that I'll be able to install 16LTS on the new desktop machine, which already has WIndows10 on it, without breaking it.
So unless I've lost the plot, I'd download 16.04.5 and install on a USB startup, then allow the installation to put it alongside Windows....? Or am I over-simplifying and being over-optimistic?

Does it matter whether I download the Ubuntu iso onto an Ubuntu machine for this, or should I do this through the Windows machine?

I hope this isn't now too off-topic, but it's all part of the process which caused my first post in the thread here.

Thanks again,

---

### Post by oldfred on 2018-02-11
If a new system with Windows 10 pre-installed, you will then have UEFI with gpt partitioning. 
Older systems were BIOS with MBR partitioning.
Definitions of terms are at end of link in my signature.

But best to review link, but it has a lot of detail. And then more links to explain the things you may not understand.

At least look at this:
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

And do backups before anything else.

---

### Post by Richard_York on 2018-02-11
Thank you, this is more homework I'll have to approach carefully, but with good hope!
I'll mark this thread as solved, as my original issue is now dealt with, and maybe start a new thread if problems with the next stage arise.

I'm most grateful, again, for all these helpful answers.

---

