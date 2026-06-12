---
title: "Can't upgrade 10.04 LTS with Upgrade Manager"
date: 2015-10-05
forum: Installation &amp; Upgrades
---

### Post by kyphos on 2015-10-05
I have an older desktop system with 10.04 LTS.  Support has come to an end, so I have to upgrade.

Being relatively unskilled in things Ubuntu, I'm following the instructions here (which stipulate I first must upgrade to 12.04):
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS)

Upon launching the Update Manager, it puts up an error message telling me my version of Ubuntu is no longer supported and needs to be updated.  Update Manager then freezes and has to be force-quit.   I've tried a few times, and rebooted for good measure.  No matter - Update Manager won't progress past the error message.

This system does not have an optical drive, so booting from a LiveCD is problematic. 

Any suggestions gratefully received. Thanks.

---

### Post by v3.xx on 2015-10-05
You need to do a EOL upgrade.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by kyphos on 2015-10-05
Thanks for the pointer to the EOLUpgrades page.
Unfortunately, it's over my head.  For example, the first instruction says:
*To begin the upgrade, make sure you have a sources.list like the following, with CODENAME being your release, e.g. quantal. *

I don't know where to look to see if I already have a sources.list file, nor how I'd modify it as required.

The instructions go on to say:
[I]You can use -backports and or -proposed if you want.
[/I]
I don't know what either of those terms mean, much less whether I'd want to use them:-(

---

### Post by yancek on 2015-10-05
The sources.list file is a simple text file and is located in the directory:  /etc/apt/

The code names are shown at the Ubuntu site below for releases.  10.04 is Lucid Lynx.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

> *You can use -backports and or -proposed if you want.*

Can't help with that, never done it but someone else should know.

---

### Post by v3.xx on 2015-10-05
First make a copy of your sources list.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```

Then edit your original sources list.

```
gksudo gedit /etc/apt/sources.list
```

Comment out (#) ALL lines or remove them if you want and add just the following lines.

> deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse

[https://help.ubuntu.com/community/EOLUpgrades#Update_sources.list](https://help.ubuntu.com/community/EOLUpgrades#Update_sources.list)

Then update your current install.

```
sudo apt-get update && sudo apt-get dist-upgrade
```

From there you should be able to upgrade to 12.04.

You should also disable all PPA or other third party software.

Release upgrades can go smooth or completely wrong.  Do you have backup?

---

### Post by mörgæs on 2015-10-06
Before attempting to upgrade please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE (not QUOTE) tags. It will show us your hardware details.

I am not sure an upgrade to a new Ubuntu is the right way to go. We might be able to suggest something with better performance for your older desktop.

---

### Post by Bucky Ball on 2015-10-06
> **mörgæs said:**
> 

I am not sure an upgrade to a new Ubuntu is the right way to go. We might be able to suggest something with better performance for your older desktop.

I fully agree. A LOT has changed since 10.04 LTS. I'd suggest a clean install of Xubuntu or Lubuntu 14.04 LTS (Ubuntu Mate is apparently light, too).

You could create Ubuntu 14.04 LTS install media, boot from that and 'Try Ubuntu'. See what happens. If it's a nightmare speed-wise or graphics-wise, another, lighter flavour is in order.

---

### Post by coffeecat on 2015-10-06
@kyphos, I suggest you do not install Lubuntu or Xubuntu until you have posted your hardware specifications and until you have understood the pros and cons of the various Ubuntu flavours. Members are right to caution you that older hardware might do better with one of the lighter flavours. **However**, it could very well be that your hardware can cope with the newer and heavier Unity desktop that Ubuntu now comes with, thank you very much. Until you have confirmed what your specs are, everything else is assumption. 

Perhaps more importantly, you need to be aware that the old gnome2 desktop, which you use in Ubuntu 10.04, is now obsolete and has been replaced by the newer Unity desktop. Some like it; others dislike it. If you would prefer to stick with the old gnome2 desktop, then the Mate fork, which comes in the Ubuntu Mate flavour as Bucky Ball suggests, might be a good choice for you. If you need more information about all these desktops, just ask. But be aware that some members here allow their own preferences to colour the advice they give - as in so much of life.

Trying out the various Ubuntu flavours in a live session is a good idea. If you have the bandwidth, there's nothing stopping you from downloading Ubuntu, Ubuntu Mate, Xubuntu and Lubuntu and trying them all out, seeing which works on your hardware and which you prefer, making **your** choice, and not someone else's

---

### Post by v3.xx on 2015-10-06
Or just install the "Flashback" desktop (similar 10.04 desktop) if the "Unity" desktop will not perform.

```
sudo apt-get install gnome-panel
```

And choose your desktop at login.

---

### Post by kyphos on 2015-10-06
Thanks to all who have responded. The Ubuntu community is extremely supportive and I really appreciate the help.

A couple of you (wisely) asked about my hardware environment in order to better advise what release to migrate to (if any). It's a tiny (literally) Zotac ZBOX HD-ID11, with an Atom CPU and 2 GB of RAM. I don't do a lot with it. Browse the web, monitor my LAN, update/maintain the firmware in various routers & switches, and run Wireshark occasionally to troubleshoot network problems.

Below is the output from lshw, as requested by morgaes. Given the diminutive capabilities of the Zotac, my intent was to upgrade to the next (after 10.04) LTS release, which presumably is less demanding than 14.04 LTS.

```

computer
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: To be filled by O.E.M.
       vendor: To be filled by O.E.M.
       physical id: 0
       version: To be filled by O.E.M.
       serial: [REMOVED]
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080016 (08/25/2010)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Atom(TM) CPU D510   @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.10
          serial: [REMOVED]
          slot: CPU 1
          size: 1666MHz
          capacity: 1666MHz
          width: 64 bits
          clock: 167MHz
          capabilities: boot fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm pse
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 48KiB
             capacity: 48KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
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
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.12.10
          serial: [REMOVED]
          size: 1650MHz
          capabilities: ht
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             capabilities: logical
     *-pci
          description: Host bridge
          product: N10 Family DMI Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:fe9fc000-fe9fffff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:d000(size=4096) memory:fea00000-feafffff ioport:fbf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 03
                serial: [REMOVED]
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=10MB/s
                resources: irq:27 ioport:d800(size=256) memory:fbffb000-fbffbfff(prefetchable) memory:fbffc000-fbffffff(prefetchable) memory:feae0000-feafffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:1000(size=4096) memory:feb00000-febfffff memory:80000000-801fffff(prefetchable)
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=[REMOVED] latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:febf0000-febfffff
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:e000(size=4096) memory:fcf00000-fdffffff ioport:ce000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GT218 [ION]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:ce000000-cfffffff(prefetchable) ioport:ec00(size=128) memory:fcf80000-fcffffff(prefetchable)
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:18 memory:fcf7c000-fcf7ffff
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:cc00(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c880(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c800(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:c480(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fe9fbc00-fe9fbfff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: NM10 Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:b880(size=8) ioport:c400(size=4) ioport:c080(size=8) ioport:c000(size=4) ioport:bc00(size=16) memory:fe9fb800-fe9fbbff
           *-disk
                description: ATA Disk
                product: ST98823AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 7.01
                serial: [REMOVED]
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00087f97
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-01-14 17:12:31 filesystem=ext4 lastmountpoint=/&#65533;&#65533;&#65533;&#65533;&#65533;}&#65533;O&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;)&#65533;H&#65533; &#65533;=&#65533;/&#65533;&#65533;&#65533;)&#65533;~C!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;}&#65533;&#65533;&#65533;&#65533;&#65533;)&#65533;&#65533;)&#65533;&#65533;&#65533; modified=2015-06-07 17:13:58 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2015-10-05 14:58:53 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3152MiB
                   capacity: 3152MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3152MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)

```

---

### Post by v3.xx on 2015-10-06
> my intent was to upgrade to the next (after 10.04) LTS release, which presumably is less demanding than 14.04 LTS.

True and 12.04 can run Unity in 2D mode, so maybe that will suit you.  If not, the Fallback desktop can still be installed.  Fallback uses the same window manager as your current 8.04 install (metacity).

---

### Post by Dennis N on 2015-10-06
We have the identical model (ID-11) to yours, but no longer use it. Originally (2010) it ran Ubuntu 10.04. Then I installed either Lubuntu or Xubuntu releases - the last installed was Xubuntu 14.04. Xubuntu 14.04 worked well, and I would recommend using that. It still has support period left.

I bought a Zotac ID-18 in Dec 2014 for $99 from Amazon.com and retired the ID-11 to storage. This one is UEFI, cool, quiet and very nice. A real bargain.

---

### Post by mörgæs on 2015-10-07
For an Atom it's a good idea to install a light Buntu like one of the suggestions mentioned here but there's no point in picking the old 12.04. The semi-old 14.04 X/Lubuntu or Mate are better choices. 

You could also take 15.10 (beta) if you want the latest applications. Don't get scared by the 'beta' status, in my experience it is stable as of now. 

Whatever you do, do a fresh install. Upgrades are risky.

---

