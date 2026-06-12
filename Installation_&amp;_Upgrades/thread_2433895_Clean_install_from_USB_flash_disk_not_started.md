---
title: "Clean install from USB flash disk not started"
date: 2019-12-27
forum: Installation &amp; Upgrades
---

### Post by david-sen on 2019-12-27
Hello, I would like to ask for a help regarding installation of Lubuntu on my old notebook. In the past, I successfully installed Lubuntu in VirtualBox on Windows 10 and as a base system on my old computer because no issue appears and I just clicked next button again and again :).

That changed with my old notebook: **MSI U123** (Model Names from BIOS: **MS-N033**), 32-bit architecture, no optical disc drive.

What I did:
1. I created bootable USB flash disk via **Rufus** software on my second Windows 10 notebook.
1a. ISO: [B]lubuntu-18.04-alternate-i386.iso
[/B]1b. New volume label: **Lubuntu** (no spaces, numbers, etc.)
1c. Method: **Write in ISO Image mode** (the recommended one, not DD Image mode)
2. I successfully boot from USB flash disk to intro screen (I **have not** GRUB).
3a. I tried **Install Lubuntu** option.
3b. I tried to press **F6** and select **nomodeset** option before I select **Install Lubuntu** option.
3c. I tried to press **F6** and select **nomodeset**, **acpi=off**, **noapic**, and **nolapic** options before I select **Install Lubuntu** option.
3d. I tried to press **F6**, than **Escape** and modify the **Boot Options** via text line from: **file=/cdrom/preseed/lubuntu.seed FRONTEND_BACKGROUND=original vga=788 initrd=/install/initrd.gz quiet ---** to: **file=/cdrom/preseed/lubuntu.seed FRONTEND_BACKGROUND=original vga=788 initrd=/install/initrd.gz nomodeset --- nomodeset**
3d1: Because I removed **quiet** option, I expected some log but nothing appears.

Everytime, the installer stuck and nothing happened.

My observations:
1. When I tried to install Windows XP back, the HDD was labelled with **E** and the flash disk (with the installation files) was labelled with **C**. It is strange, isn't it?
2. I was not able to start Debian live.
3. I was able to start TinyCore and Porteus live.

---

### Post by mörgæs on 2019-12-27
Hi, welcome to the fora.

> **david-sen said:**
> 
I successfully boot from USB flash disk to intro screen 

So far, so good. In stead of installing try the live boot option.

From here, please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it onto the command line, run it and post lshw.txt in CODE tags.

---

### Post by david-sen on 2019-12-27
Thank you for the hint. I missed the Live option in Lubuntu image. If I get it right, it's available only in 64-bit version. Am I right?

I run **lshw** command in Porteus live.
```

computer
    description: Desktop Computer
    product: MS-N033 (To be filled by O.E.M.)
    vendor: MICRO-STAR INTERNATIONAL CO., LTD
    version: Ver.001
    serial: [REMOVED]
    width: 32 bits
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=[REMOVED]
  *-core
       description: Motherboard
       product: U-100
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       version: Ver.001
       serial: [REMOVED]
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 4.6.3
          date: 04/24/2009
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N280   @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.2
          serial: [REMOVED]
          slot: CPU 1
          size: 1667MHz
          capacity: 4GHz
          width: 32 bits
          clock: 667MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts cpuid aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm dtherm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 24KiB
             capacity: 24KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 1008MiB
        *-bank:0
             description: DIMM DDR2 Synchronous [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
        *-bank:1
             description: DIMM DDR2 Synchronous [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
     *-pci
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0 UNCLAIMED
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
             resources: memory:dfe80000-dfefffff ioport:e0f0(size=8) memory:c0000000-cfffffff memory:dff00000-dff3ffff memory:c0000-dffff
        *-display:1 UNCLAIMED
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:dfe00000-dfe7ffff
        *-multimedia UNCLAIMED
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0
             resources: memory:ffe00000-ffe03fff
        *-pci:0
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) memory:dfd00000-dfdfffff ioport:ffd00000(size=1048576)
           *-network
                description: Ethernet interface
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp aui bnc mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 latency=0 link=no multicast=yes port=MII
                resources: irq:16 ioport:d000(size=256) memory:ffd10000-ffd10fff memory:ffd00000-ffd0ffff memory:dfd00000-dfd1ffff
        *-pci:1
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:2000(size=4096) memory:dfc00000-dfcfffff ioport:40000000(size=2097152)
           *-network
                description: Wireless interface
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=4.19.10-tinycore firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:18 memory:dfc00000-dfc0ffff
        *-usb:0
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:e080(size=32)
        *-usb:1
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:e060(size=32)
        *-usb:2
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:e040(size=32)
        *-usb:3
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:e020(size=32)
        *-usb:4
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:dff40000-dff403ff
        *-pci:2
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e0a0(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1600BEVT-2
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1A11
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=04750866
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 148GiB
                capacity: 148GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2019-12-26 23:57:11 filesystem=ntfs state=clean
           *-volume:1
                description: EXT3 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 1.0
                serial: [REMOVED]
                size: 1GiB
                capacity: 1GiB
                capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                configuration: created=2019-12-27 20:29:38 filesystem=ext3 lastmountpoint=/mnt/sda2 modified=2019-12-27 23:35:29 mounted=2019-12-27 23:35:28 state=clean
     *-scsi:1
          physical id: 2
          bus info: usb@1:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 7680MiB (8053MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=02687a2d
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /mnt/sdb1
                version: FAT32
                serial: [REMOVED]
                size: 7676MiB
                capacity: 7679MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0000,dmask=0000,allow_utime=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
     *-scsi:2
          physical id: 3
          bus info: usb@1:6
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=ums-realtek
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdc
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: dummy0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=dummy driverversion=1.0

```

---

### Post by guiverc on 2019-12-27
Do you really have <700MB of RAM?  That is what the alternative download option is for (plus it's no longer produced, so you're using a version that is very old and thus will have loads of updates).


The alternative ISO does NOT include 'live' mode as that required most of 700MB of RAM, which didn't leave any for  `ubiquity` to actually run; thus the existence it's existence. In most cases though its not the **ISO** to use.

I'll provide

[https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html](https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html)
[https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html)

though please note I tested Lubuntu 18.04 LTS using machines as old as from 2003, and 18.10 & 19.04 up with machines as old as 2004 (x86 or 32-bit only boxes).  All my x86/32-bit boxes had 1GB of ram or more (1.5 being the average).  A quick scan tells me your machine is from 2009 which is much newer; the **newest x86 only** I have is from 2008 (asus eeepc) so I'd hope your box will boot & run x86_64 but I don't know.  (32bit winxp was often put on new things as it was cheaper)

From the Lubuntu site i'll provide the following

[https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html](https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html)
[https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html)

I'd always suggest using the 'Check disc for defects' option mentioned in the 1.3 page (note screens for the manual prefer to 'stable' version which is currently 19.10. Also I'll mention many sites offer Lubuntu for download, but only the official site is under the control of Ubuntu/Lubuntu so I believe it's safer to not use search engines like google to find the site, but go to ubuntu.com directly where you'll end up at [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) which will send you to official sites which will provide official images that haven't been doctored.  If you did download it from a 3rd party site, I'd suggest ensuring it validates correctly ([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0) and [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck) which whilst not for Lubuntu, apply equally to all flavors, but get the checksum from an official site!)

---

### Post by david-sen on 2019-12-27
Thank you for the overview. This time I downloaded ISOs from the official page (last time I thought that it's official page but it wasn't).

1. I started with **19.10 Eoan Ermine (LXQt)** / 64-bit, there is no 32-bit version. Option **Start Lubuntu (safe graphics)** shows *This kernel requires an x86-64 CPU, but only detected an i686 CPU*. Therefore, I continue with 32-bit version of the oldest version.
2. **18.04.3 Bionic Beaver LTS (LXDE)** / 32-bit. I tried both, **Try Lubuntu without installing** and **Install Lubuntu** options. Unfortunately, none of them started. I also tried **Check disc for defects** option that you pointed out and also this one does not start.

In my previous post, I posted my configuration obtained via **lshw** command if it can help.

---

### Post by sudodus on 2019-12-27
Using data from the output of lshw:

From Intel's data sheet for Intel(R) Atom(TM) CPU N280   @ 1.66GHz:

- Intel® 64 ‡ No
- Instruction Set 32-bit

So you need a 32-bit operating system for this computer.

Good news: RAM size 1008MiB (approx 1 GiB), which is enough for the desktop installer (and running Lubuntu live)

Edit: You might have better luck with a really small operating system, for example Tiny Core or Puppy Linux.

I think Debian 32 -bit could be an alternative, but will probably not work better than 32-bit Lubuntu 18.04.1 LTS.

---

### Post by tea for one on 2019-12-27
Have a look at Peppermint 10 - based on Lubuntu with xfce panel.

Min RAM is 512MB and 32bit ISO is available

[https://peppermintos.com/](https://peppermintos.com/)

---

### Post by guiverc on 2019-12-27
:(  "*This kernel requires an x86-64 CPU, but only detected an i686 CPU.*" is the message I get when I boot a x86_64 image on a x86 only cpu - so your n280 (my eeepc has n270) can only boot x86  (*I didn't read your `lshw`detail sorry*).

I would suggest either Lubuntu 18.04 (inc. 18.04.3) LTS (supported until 2021-April) or Debian 10. I would expect both to operate on my eeepc so should be fine for yours (it's within reach, but I'm to lazy to boot it to see which is installed). 

Ubuntu is generally easier (more support options, easier to setup etc) than Debian, but if you start with the debian non-free ISO's, debian on most boxes is pretty easy too. i have two boxes (2 of 17) both with same video card that do better with Ubuntu on initial boot or *out-of-the-box* thus I consider Ubuntu more newbie-friendly; I test Debian as well as Ubuntu.  I would go with Debian if you want support beyond 2021-April (re: Ubuntu & those downstream of Ubuntu)

---

### Post by david-sen on 2019-12-29
Thank you very much for all hints. In the end, I installed **Porteus** on my old notebook. **TinyCore** worked also fine. Lubuntu and Debian didn't work (both, live version and install process) probably because of old HW. I can run Lubuntu Live on my new notebook.

---

### Post by mörgæs on 2019-12-30
Congratulations and thanks for marking the thread solved.
Generally speaking people should not try to install from a live boot with 1 GB of memory or less. Better to install in a text-only environment like [described]("https://ubuntuforums.org/showthread.php?t=2130640&page=22&p=13902890&viewfull=1#post13902890") here.

You have two good options already so it's probably a moot point. Just in case other people see the thread.

---

