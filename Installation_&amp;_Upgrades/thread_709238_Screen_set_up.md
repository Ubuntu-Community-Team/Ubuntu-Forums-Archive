---
title: "Screen set up"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by timswait on 2008-02-27
I've not been able to get my screen set up quite the way I like it since installing Ubuntu. Basically the colours look washed out, and I can barely see anything which is faint, Ie light grey writing on a white background is pretty much illegible. I've tried fiddling with the contrast and brightness settings on the monitor but can't really improve it. I'm not sure if it's displaying a full depth of colours and can't find the settings for adjusting that in Linux like I can in windows. The computer is based on an ASUS motherboard with on board graphics. I've also got Win XP on this computer and I initially had the same problem on that, but once I had installed the drivers which came with the motherboard and then fiddled about with catalyst control centre (an application which came on the CD with the mother board for adjusting screen settings) I got it looking good. I can't find a version of Catalyst for Linux on the ASUS website, is there anything similar I can use? I just can't seem to find very many adjustments for my screen in the System menu on Ubuntu.
I've tried installing the Monitor Settings Application but it says "No monitor supporting CCD/CI available. If your graphics card needs it please check all the required kernel modules are loaded (i2c-dev and your framebuffer driver).
What are these required kernel modules and how do I load them?

---

### Post by Pumalite on 2008-02-27
Post:
lshw

---

### Post by timswait on 2008-02-27
> **Pumalite said:**
> Post:
lshw

What does that mean?

---

### Post by Pumalite on 2008-02-27
Applications>Accessories>Terminal. Type lshw. Press 'Enter'.Copy and paste the output here.

---

### Post by timswait on 2008-02-27
Does this help? There's lots of it!
tims                      
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=desktop uuid=00CD7799-0188-DC11-A191-001BFCFFD68B
  *-core
       description: Motherboard
       product: M2A-VM HDMI
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.XX
       serial: 123456789000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS M2A-VM HDMI ACPI BIOS Revision 1404 (10/11/2007)
          size: 128KB
          capacity: 960KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Processor LE-1600
          vendor: Advanced Micro Devices [AMD]
          physical id: 5
          bus info: cpu@0
          version: AMD Athlon(tm) Processor LE-1600
          slot: Socket AM2
          size: 2200MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up pni cx16 lahf_lm svm extapic cr8_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: b
             slot: L1 Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: c
             slot: L2 Cache
             size: 1MB
             capacity: 1MB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 30
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM 667 MHz (1.5 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM 667 MHz (1.5 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: Radeon X1200 Series
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi vga bus_master cap_list
                configuration: driver=fglrx_pci latency=64 module=fglrx
        *-pci:1
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 3)
             vendor: ATI Technologies Inc
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:1b:fc:ff:d6:8b
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.101 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64 module=ahci
           *-disk
                description: SCSI Disk
                product: WDC WD2500AAJS-0
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WMART0421246
                size: 232GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 48GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 48GB
                   capabilities: primary
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 5530MB
                   capacity: 5530MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5530MB
                      capabilities: nofs
              *-volume:3
                   description: W95 FAT32 partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 129GB
                   capabilities: primary
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht bus_master vga_palette cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ATIIXP_IDE latency=64 module=atiixp
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-cdrom
                   description: DVD writer
                   product: PIONEER DVD-RW DVR-110D
                   vendor: Pioneer
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 1.17
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r
                   configuration: mode=udma4 status=nodisc
              *-disk
                   description: ATA Disk
                   product: Maxtor 6G160P0
                   vendor: Maxtor
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: KA201V00
                   serial: G20H1J0G
                   size: 149GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume
                      description: W95 FAT32 partition
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      capacity: 149GB
                      capabilities: primary
        *-multimedia
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
           *-firewire:0
                description: FireWire (IEEE 1394)
                product: uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr
                vendor: NEC Corporation
                physical id: 6
                bus info: pci@0000:03:06.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=44 mingnt=20 module=ohci1394
           *-firewire:1
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 7
                bus info: pci@0000:03:07.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp

---

### Post by Pumalite on 2008-02-27
You have to install with the Ubuntu Alternate CD:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
After choosing your flavor, mark the box below the sign 'Start Download'

---

### Post by timswait on 2008-02-28
Really why is that? Is there no other way, I don't really want to have to go all through installing it again.

---

### Post by Pumalite on 2008-02-28
Post:
sudo fdisk -lu
cat /etc/X11/xorg.conf

---

### Post by intel on 2008-02-28
Try the following guide for correctly configuring X1200

https://groups.google.com/group/x1250/web/drivers4linux

this will definitely work out for you.

---

### Post by timswait on 2008-02-28
> **intel said:**
> Try the following guide for correctly configuring X1200

[https://groups.google.com/group/x1250/web/drivers4linux](https://groups.google.com/group/x1250/web/drivers4linux)

this will definitely work out for you.

I went to that groups page and followed the link to the ATi proprietary Linux installer. I'd like to try and install that because it includes Catalyst Control Centre, and that sorted out my Windows installation when I ran it on that. I've downloaded it, saved it into the /usr directory, but I can't get the bloody thing to run. I disabled my old fglx driver then I go to terminal, type *cd /usr* then type *sudo ati-driver-installer-8.35.5-x86.x86_64.run* enter my password and then it tells me command not found. How can it not find the bloody command! I'm in the right directory, damn sure I'm typing it correctly, I know it's probably just me being a numpty not knowing how use Linux but it's really annoying me! :mad: When I type *dir* it lists the file so it must be there, how do I run a *.run file?

---

### Post by timswait on 2008-02-28
This is getting worse. :( I've finally got the ATi proprietry installer to run (seemed to need an sh between sudo and the filename), and have installed the driver files, and catalyst  but still no joy catalyst says the drivers  are not installed and I can't run aticonfig. There doesn't seem to be an xorg.conf file, which I'm guessing is a bit of a problem. How do I get one?

Reply to Pumalite:

 sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102398309    51199123+   7  HPFS/NTFS
/dev/sda2       102398310   205053659    51327675   83  Linux
/dev/sda3       477066240   488392064     5662912+   5  Extended
/dev/sda4       205053660   477066239   136006290    b  W95 FAT32
/dev/sda5       477066303   488392064     5662881   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd99f482c

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63   312576704   156288321    b  W95 FAT32
tim@tims:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
tim@tims:~$

---

### Post by Pumalite on 2008-02-28
Try:
gksudo gedit /etc/X11/xorg.conf

---

### Post by timswait on 2008-02-28
It's a blank document. There was no xorg.conf file at all until I typed that.

---

### Post by Pumalite on 2008-02-28
If you are posting from the computer we are talking about, I doubt you could have booted without an xorg.conf file.

---

### Post by timswait on 2008-02-28
I am, and there's not. It's not very happy though. There was a list of problems at the start about unrecognised things like keyboards and it's in safe graphics mode so everything looks very blocky. In fact I can barely read what I'm typing now! It's looking like I might have to reinstall and start again.

---

### Post by Pumalite on 2008-02-28
Probably the best thing to do. Be careful when you install video drivers. Backup menu.lst, fstab and xorg.conf to start with after the reinstall.

---

### Post by timswait on 2008-02-29
Right now I've got a problem. I'd like to reinstall Linux using the alternate CD like you said at the beginning. The problem is now that the screen goes black when I try to start Ubuntu, so I can't see anything. I get the Ubuntu loading bar, but then instead of going to the login screen the screen switches to power saving mode, presumably the settings are very wrong. But I can't see anything on the screen, so I can't set them back. Is there some way to force Ubuntu to start in low graphics mode. Luckily my computer is dual boot, so I'm writing this in Windows.

---

### Post by Pumalite on 2008-02-29
Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Partition your drive, then use Alternate CD for installation

---

### Post by timswait on 2008-03-03
I'm now basically back to where I was, ie a working Linux installation, but with the wrong video drivers.  Before I start fiddling again I'd like to back up those files you said. I know where xorg.conf is, what about the other two? Should I copy them to a safe place and then if it goes tits up again I copy them back to their original locations? Does Linux have a system of system restore points like Windows?

---

### Post by Pumalite on 2008-03-03
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
sudo cp /etc/fstab /etc/fstab.old
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old

---

### Post by timswait on 2008-03-03
Well, it's a whole lot better now:), but still not perfect and what a lot of effort :( Tried manually installing the ATi drivers, but couldn't get the packages to build. No idea why, that was one thing that did work OK previously before reinstallling Ubuntu. Tried the open source version, but couldn't get that to install either. Then tried installing Envy, an application to detect your graphics card and install the latest driver. First time round this didn't work, from what I saw of the screen it seemed to have trouble building the package again. Then I tried it again, manually choosing an older version of the driver (8.40.4). This worked, I've now got the display displaying correctly and catalyst control centre working, so I've been able to adjust the Gamma so everything can be clearly seen. That's the good bit, I've still got the following problems:
-Can't use MPlayer comes up with an error, unable to initialise video_out. Totem Media player works though.
-Can't use any visual effects in the desktop prefences ("desktop effects could not be enabled")
To be honest these aren't particularly major problems, but if anyone's got any suggestions that don't involve wrecking everything all over again I'd like to get them sorted.

---

