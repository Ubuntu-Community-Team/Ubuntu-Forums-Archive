---
title: "Graphics card"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by joeleeg on 2008-02-07
How can I tell which graphics card I am using and which ones have their drivers installed/which other graphic cards are detected by my computer?

And here is my main problem.

I have my cord from my monitor to my secondary graphics card. Everything works fine. Now when I move my monitors cord to my primary graphics card (a NVIDIA GeForce 5500 fx) the screen is just black.

Ah yes, the most important detail. My primary graphics card is in a PCI slot. I am currently booting off the onboard graphics card. Now when I boot off the PCI bus and move my monitor's cord to my primary graphics card the screen on my monitor is just black, even though I switched the settings.

Do you people have any idea of what is wrong?

---

### Post by jan quark on 2008-02-07
you can run in terminal to display all detected hardware on your computer

```
sudo lshw
```

---

### Post by joeleeg on 2008-02-07
That is what I got. My computer's model is an HP Pavilion a705w.

```
    description: Desktop Computer
    product: PJ562AA-ABA a705w
    vendor: HP Pavilion 061
    version: 0n41211RE101GIOVA00
    serial: CNC4440KXJ NA440
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=60B96BDC-D628-D911-A29E-8936A17F0722
  *-core
       description: Motherboard
       product: Gamila/Giovani/Neon series
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       version: 030
       serial: 4911265922
       slot: PRIMARY IDE
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.15 (08/05/2004)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.93GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: Socket 478
          size: 2933MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pni monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 32KB
             capacity: 32KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 256KB
             capacity: 256KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 1280MB
          capacity: 2GB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 256MB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5500]
                vendor: nVidia Corporation
                physical id: a
                bus info: pci@0000:01:0a.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga cap_list
                configuration: latency=32 maxlatency=1 mingnt=5
           *-communication UNCLAIMED
                description: Communication controller
                product: V.92 56K WinModem
                vendor: Agere Systems
                physical id: b
                bus info: pci@0000:01:0b.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 maxlatency=14 mingnt=252
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: c
                bus info: pci@0000:01:0c.0
                logical name: eth0
                version: 10
                serial: 00:11:09:75:0a:c7
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.100 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
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
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: ST340015A
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.15
                serial: 5LAH1CTF
                size: 37GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 35GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1608MB
                   capacity: 1608MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1608MB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: COMBO SOHC-4832K
                vendor: LITE-ON
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: OPK3
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=ready
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
                   capabilities: partitioned partitioned:mac
                 *-volume:0 UNCLAIMED
                      description: Apple partition map
                      physical id: 1
                      capacity: 1KB
                 *-volume:1 UNCLAIMED
                      description: Apple HFS
                      physical id: 2
                      capacity: 591MB
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
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
     *-scsi:0
          physical id: 1
          bus info: usb@4:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Photosmart C4240
             vendor: HP
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
             configuration: ansiversion=5
           *-disc
                physical id: 0
                logical name: /dev/sdb
     *-scsi:1
          physical id: 2
          bus info: usb@3:1
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: USB SD Reader
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdc
             version: 1.00
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             product: USB CF Reader
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@5:0.0.1
             logical name: /dev/sdd
             version: 1.01
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             product: USB SM Reader
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@5:0.0.2
             logical name: /dev/sde
             version: 1.02
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             product: USB MS Reader
             vendor: Generic
             physical id: 0.0.3
             bus info: scsi@5:0.0.3
             logical name: /dev/sdf
             version: 1.03
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdf

```

---

### Post by bwtranch on 2008-02-07
lspci is good enough for your graphics card, you don't have to list all your hardware.

---

### Post by ajgreeny on 2008-02-07
Your secondary graphics card that works is an intel:-
display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810

The primary is an nvidia as you say, but it would appear that you dont have the correct driver for that as you gat no visible output.  Or do you mean you get a console output, ie a blinking cursor?

Try booting with onboard graphics temporarily disabled and the monitor attached to the primary nvidia card.  If you get a console output from that try logging in and then ```
sudo dpkg-reconfigure xservsr-xorg
```to at least get a display using the nv driver or if that doesn't work, the vesa.  Once you have a display ypou can try to get the restricted driver working.

---

### Post by joeleeg on 2008-02-07
Alright, so here is the deal. When I boot my computer with the other graphics card and the cable plugged into the other graphics card i get the ubuntu boot-up screen. However it does not boot up all the way, instead it just freezes at the third bar. I had this problem before and I resolved it by switching to my onboard graphics card. I am making the assumption that the problem is in my drivers for my graphics card with regards to those of you who mentioned it. Now can one of you people give me a link or something to the exact download that would be required by my computer?

Statistics to my computer are in one of the above posts.

---

### Post by joeleeg on 2008-02-07
Alright, so I am linking my problem to this problem. [http://ubuntuforums.org/showthread.php?t=637365]("http://ubuntuforums.org/showthread.php?t=637365")

When I follow the steps of the other person's problem I get led to this guy's solution:

```
I found the fix. I installed Ubuntu on the HHD using the onboard graphics. Then I installed the PCI card (An FX5500, as it happens). I booted into the graphics mode from GRUB, and did a lspci | grep xorg.conf, and determined the address of my PCI card, 00:08:0. I had to move the card to the first slot before it generated a usable PCI address. Then, I did a sudo dpkg-reconfigure xserver-xorg, and set the card address to 00:08:0, and rebooted. After that, the nVidia drivers installed normally and glxinfo | grep rendering shows 3D acceleration.
```

I can now use my NVIDIA card BUT! The resolution is 640x480, how do I fix this? I have no options to increase the resolution.

---

### Post by joeleeg on 2008-02-07
nevermind, problem solved, i ended up installing envy to help me.

---

