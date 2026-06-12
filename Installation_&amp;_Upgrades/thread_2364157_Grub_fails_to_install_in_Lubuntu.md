---
title: "Grub fails to install in Lubuntu"
date: 2017-06-19
forum: Installation &amp; Upgrades
---

### Post by mimuwhen on 2017-06-19
Hello all.  

I have encountered this issue while trying to install Lubuntu 6.10 on my computer.  The install goes well up to near the end where i get the error about Grub failing to install.  grub-pc failed to install into /target/ is the message I get after I click OK on the initial error message.  I read around and one of the solutions that is offered is to have the computer hooked up to the internet.  I went ahead and hooked my computer up to the internet through an ethernet cable (working connection confirmed on another computer) but when I try to open up pages on firefox during a live session the pages never actually load though it seems to try.  When I try to install lubuntu the option that tells lubuntu to update itself as it installs is blanked out and I cannot select it.  I want to do this because it is yet another one of the suggestions I have seen around that might help fix my issue.  

What could I do to resolve this issue?

I'm installing from a DVD.  I don't think there is any issue with the DVD itself.  I performed a checksum on the iso file before burning and set the burning software to verify data once it was finished.  

Your advice is appreciated as always.  Thank you!

---

### Post by oldos2er on 2017-06-19
Please install a supported version, see [http://lubuntu.me/downloads/](http://lubuntu.me/downloads/)
6.10 is ridiculously old and not at all safe to run.

---

### Post by ubfan1 on 2017-06-19
Even assuming a type of 16.10, that end of service is next month.  Choose either 16.04 for long term support, or 17.04 if you need the (newer) hardware support.  Is your machine UEFI?  Are you trying to install in UEFI mode?  What partitioning type is your disk (DOS or GPT)?  You're not using logical volumes are you?  No raid either?

---

### Post by mimuwhen on 2017-06-20
> **ubfan1 said:**
> Even assuming a type of 16.10, that end of service is next month.

Aww man really? It was a typo I didn't mean 6.10 but rather 16.10.  That really sucks cuz it actually managed to install.  I didn't realize that wasn't a long term support version.  I downloaded it by clicking on the download link in the "Standard PC" segment of this page. [https://help.ubuntu.com/community/Lubuntu/GetLubuntu#Standard_PC](https://help.ubuntu.com/community/Lubuntu/GetLubuntu#Standard_PC)

What happens if I just keep that version? The thing is the operating system finally managed to install.  I didn't change anything except restarting the PC (which I had done before but perhaps I hadn't done while having the thing connected to the internet from the very beginning of the boot process) and the installation was successful.  

The problem now however is that my display doesn't work properly.  I'm stuck at 640X480 resolution and I have no way of changing it.  Another issue is that the internet still doesn't quite seem to work all the way properly.  When I open firefox and load websites that works fine but when I open up the software center nothing loads.  

First i'd like to tackle the display issue which seems to be driver related.  However I am not sure how to go about downloading the proper drivers.  When I google this issue I get other suggestions but I am unsure if those solutions are the right ones for me.

---

### Post by mörgæs on 2017-06-20
16.10 is fine a month more. Just let it run for now.

Have you applied all updates?

Please post a complete hardware description: Copy the command```
 sudo lshw -sanitize > lshw.txt
``` into the terminal, run it and post the contents from lshw.txt in CODE tags. It will give people a better foundation for helping.

---

### Post by mimuwhen on 2017-06-27
Hey, I had to take a break because my keyboard died.  I went ahead and installed 16.04 from scratch.  Same issue.  Display is screwed up.  All updates have been applied. As before the display worked fine while the computer was booted using the live CD.

Here is the system profile.  Titles are in spanish but I think the majority of it translates over quite easily, in case not please ask.  The part about display says "Not claimed" which I guess would translate to something like not connected or not installed perhaps?  The computer has this graphics card installed. [http://www.suntekpc.com/htm-2/controller-pci-vga-card-xxx-pine-technology-phantom-xp-pci3800.htm](http://www.suntekpc.com/htm-2/controller-pci-vga-card-xxx-pine-technology-phantom-xp-pci3800.htm)

```
[B]computer
    descripción: Equipo de escritorio
    producto: MS-6712
    fabricante: MSI
    versión: 1.0
    serie: [REMOVED]
    anchura: 32 bits
    capacidades: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuración: chassis=desktop cpus=1
  *-core
       descripción: Placa base
       producto: MS-6712
       fabricante: MSI
       id físico: 0
       versión: 1.0
       serie: [REMOVED]
     *-firmware
          descripción: BIOS
          fabricante: American Megatrends Inc.
          id físico: 0
          versión: Version 07.00T
          date: 04/02/01
          tamaño: 64KiB
          capacidad: 192KiB
          capacidades: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          descripción: CPU
          producto: AMD Athlon(tm) XP
          fabricante: Advanced Micro Devices [AMD]
          id físico: 4
          información del bus: cpu@0
          versión: 6.10.0
          ranura: Socket-A
          tamaño: 1150MHz
          capacidad: 3GHz
          anchura: 32 bits
          reloj: 100MHz
          capacidades: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow eagerfpu 3dnowprefetch vmmcall
        *-cache:0
             descripción: L1 caché
             id físico: 5
             ranura: Internal Cache
             tamaño: 128KiB
             capacidad: 1MiB
             capacidades: synchronous internal write-back unified
             configuración: level=1
        *-cache:1
             descripción: L2 caché
             id físico: 6
             ranura: Internal Cache
             tamaño: 512KiB
             capacidad: 1MiB
             capacidades: synchronous internal write-back unified
             configuración: level=2
     *-memory
          descripción: Memoria de sistema
          id físico: 1
          tamaño: 1505MiB
     *-pci
          descripción: Host bridge
          producto: VT8377 [KT400/KT600 AGP] Host Bridge
          fabricante: VIA Technologies, Inc.
          id físico: 100
          información del bus: pci@0000:00:00.0
          versión: 80
          anchura: 32 bits
          reloj: 66MHz
          configuración: driver=agpgart-via latency=8
          recursos: irq:0 memoria:e0000000-e7ffffff
        *-pci
             descripción: PCI bridge
             producto: VT8237/VX700 PCI Bridge
             fabricante: VIA Technologies, Inc.
             id físico: 1
             información del bus: pci@0000:00:01.0
             versión: 00
             anchura: 32 bits
             reloj: 66MHz
             capacidades: pci pm normal_decode bus_master cap_list
        *-display NO RECLAMADO
             descripción: VGA compatible controller
             producto: 315PRO PCI/AGP VGA Display Adapter
             fabricante: Silicon Integrated Systems [SiS]
             id físico: 5
             información del bus: pci@0000:00:05.0
             versión: 00
             anchura: 32 bits
             reloj: 66MHz
             capacidades: pm vga_controller bus_master cap_list
             configuración: latency=39 maxlatency=16 mingnt=3
             recursos: memoria:c0000000-cfffffff memoria:dffc0000-dfffffff ioport:ec00(size=128) memoria:c0000-dffff
        *-communication
             descripción: Communication controller
             producto: PCI 1 port parallel adapter
             fabricante: MosChip Semiconductor Technology Ltd.
             id físico: 7
             información del bus: pci@0000:00:07.0
             versión: 01
             anchura: 32 bits
             reloj: 33MHz
             configuración: driver=parport_pc latency=32
             recursos: irq:18 ioport:e800(size=8) ioport:e400(size=8) ioport:e000(size=8) ioport:dc00(size=8) ioport:d800(size=8) ioport:d400(size=16)
        *-usb:0
             descripción: USB controller
             producto: VT82xx/62xx UHCI USB 1.1 Controller
             fabricante: VIA Technologies, Inc.
             id físico: 10
             información del bus: pci@0000:00:10.0
             versión: 80
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm uhci bus_master cap_list
             configuración: driver=uhci_hcd latency=32
             recursos: irq:21 ioport:c800(size=32)
           *-usbhost
                producto: UHCI Host Controller
                fabricante: Linux 4.8.0-56-generic uhci_hcd
                id físico: 1
                información del bus: usb@2
                nombre lógico: usb2
                versión: 4.08
                capacidades: usb-1.10
                configuración: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             descripción: USB controller
             producto: VT82xx/62xx UHCI USB 1.1 Controller
             fabricante: VIA Technologies, Inc.
             id físico: 10.1
             información del bus: pci@0000:00:10.1
             versión: 80
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm uhci bus_master cap_list
             configuración: driver=uhci_hcd latency=32
             recursos: irq:21 ioport:cc00(size=32)
           *-usbhost
                producto: UHCI Host Controller
                fabricante: Linux 4.8.0-56-generic uhci_hcd
                id físico: 1
                información del bus: usb@3
                nombre lógico: usb3
                versión: 4.08
                capacidades: usb-1.10
                configuración: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             descripción: USB controller
             producto: VT82xx/62xx UHCI USB 1.1 Controller
             fabricante: VIA Technologies, Inc.
             id físico: 10.2
             información del bus: pci@0000:00:10.2
             versión: 80
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm uhci bus_master cap_list
             configuración: driver=uhci_hcd latency=32
             recursos: irq:21 ioport:d000(size=32)
           *-usbhost
                producto: UHCI Host Controller
                fabricante: Linux 4.8.0-56-generic uhci_hcd
                id físico: 1
                información del bus: usb@4
                nombre lógico: usb4
                versión: 4.08
                capacidades: usb-1.10
                configuración: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   descripción: Ratón
                   producto: USB Optical Mouse
                   fabricante: Logitech
                   id físico: 1
                   información del bus: usb@4:1
                   versión: 43.01
                   capacidades: usb-2.00
                   configuración: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-usb:3
             descripción: USB controller
             producto: USB 2.0
             fabricante: VIA Technologies, Inc.
             id físico: 10.3
             información del bus: pci@0000:00:10.3
             versión: 82
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm ehci bus_master cap_list
             configuración: driver=ehci-pci latency=32
             recursos: irq:21 memoria:dffaff00-dffaffff
           *-usbhost
                producto: EHCI Host Controller
                fabricante: Linux 4.8.0-56-generic ehci_hcd
                id físico: 1
                información del bus: usb@1
                nombre lógico: usb1
                versión: 4.08
                capacidades: usb-2.00
                configuración: driver=hub slots=6 speed=480Mbit/s
        *-isa
             descripción: ISA bridge
             producto: VT8235 ISA Bridge
             fabricante: VIA Technologies, Inc.
             id físico: 11
             información del bus: pci@0000:00:11.0
             versión: 00
             anchura: 32 bits
             reloj: 33MHz
             capacidades: isa pm bus_master cap_list
             configuración: latency=0
        *-ide
             descripción: IDE interface
             producto: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             fabricante: VIA Technologies, Inc.
             id físico: 11.1
             información del bus: pci@0000:00:11.1
             versión: 06
             anchura: 32 bits
             reloj: 33MHz
             capacidades: ide pm bus_master cap_list
             configuración: driver=pata_via latency=32
             recursos: irq:255 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
        *-multimedia
             descripción: Multimedia audio controller
             producto: VT8233/A/8235/8237 AC97 Audio Controller
             fabricante: VIA Technologies, Inc.
             id físico: 11.5
             información del bus: pci@0000:00:11.5
             versión: 50
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm cap_list
             configuración: driver=snd_via82xx latency=0
             recursos: irq:22 ioport:c400(size=256)
        *-network
             descripción: Ethernet interface
             producto: VT6102/VT6103 [Rhine-II]
             fabricante: VIA Technologies, Inc.
             id físico: 12
             información del bus: pci@0000:00:12.0
             nombre lógico: enp0s18
             versión: 74
             serie: [REMOVED]
             tamaño: 100Mbit/s
             capacidad: 100Mbit/s
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuración: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=full ip=[REMOVED] latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             recursos: irq:23 ioport:c000(size=256) memoria:dffafe00-dffafeff
     *-scsi:0
          id físico: 2
          nombre lógico: scsi0
          capacidades: emulated
        *-disk
             descripción: ATA Disk
             producto: ST340810A
             fabricante: Seagate
             id físico: 0.0.0
             información del bus: scsi@0:0.0.0
             nombre lógico: /dev/sda
             versión: 3.39
             serie: [REMOVED]
             tamaño: 37GiB (40GB)
             capacidades: partitioned partitioned:dos
             configuración: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=942abb48
           *-volume:0
                descripción: partición EXT4
                fabricante: Linux
                id físico: 1
                información del bus: scsi@0:0.0.0,1
                nombre lógico: /dev/sda1
                nombre lógico: /
                versión: 1.0
                serie: [REMOVED]
                tamaño: 35GiB
                capacidad: 35GiB
                capacidades: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuración: created=2017-06-27 01:36:27 filesystem=ext4 lastmountpoint=/ modified=2017-06-27 02:45:50 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-06-27 02:26:59 state=mounted
           *-volume:1
                descripción: Extended partition
                id físico: 2
                información del bus: scsi@0:0.0.0,2
                nombre lógico: /dev/sda2
                tamaño: 1534MiB
                capacidad: 1534MiB
                capacidades: primary extended partitioned partitioned:extended
              *-logicalvolume
                   descripción: Linux swap / Solaris partition
                   id físico: 5
                   nombre lógico: /dev/sda5
                   capacidad: 1534MiB
                   capacidades: nofs
     *-scsi:1
          id físico: 3
          nombre lógico: scsi1
          capacidades: emulated
        *-cdrom:0
             descripción: DVD writer
             producto: DVD RW DW-Q28A
             fabricante: SONY
             id físico: 0.0.0
             información del bus: scsi@1:0.0.0
             nombre lógico: /dev/cdrom
             nombre lógico: /dev/cdrw
             nombre lógico: /dev/dvd
             nombre lógico: /dev/dvdrw
             nombre lógico: /dev/sr0
             versión: KYS3
             capacidades: removable audio cd-r cd-rw dvd dvd-r
             configuración: ansiversion=5 status=nodisc
        *-cdrom:1
             descripción: CD-R/CD-RW writer
             id físico: 0.1.0
             información del bus: scsi@1:0.1.0
             nombre lógico: /dev/sr1
             capacidades: audio cd-r cd-rw
             configuración: status=nodisc[/B]


```

---

### Post by ubfan1 on 2017-06-27
You have a SIS video card, 315e, so should be supported.  Google SIS video driver Ubuntu  and see what looks like it would help, like the below two:
[http://manpages.ubuntu.com/manpages/trusty/man4/sis.4.html](http://manpages.ubuntu.com/manpages/trusty/man4/sis.4.html)
[https://help.ubuntu.com/community/BinaryDriverHowto/Sis](https://help.ubuntu.com/community/BinaryDriverHowto/Sis)
Try booting in recovery mode, that might drop back to a supported VGA mode.

---

### Post by mimuwhen on 2017-06-27
I tried following the instructions on this thread [I][https://cd-rw.org/t/how-to-install-sis-mirage-661-771-drivers-on-ubuntu-to-get-native-resolution/74](https://cd-rw.org/t/how-to-install-sis-mirage-661-771-drivers-on-ubuntu-to-get-native-resolution/74)


[/I]However when I type in "sudo apt-get install xserver-xorg-video-sisimedia" It tells me it couldnt find the package xserver-xorg-video-sisimedia.


I'm having trouble going into the recovery mode.  Either with the shift key or the esc key.

---

### Post by ubfan1 on 2017-06-28
The recovery mode I was suggesting was from the grub menu, select "advanced ..." and then you get more choices, among them a recovery...  That should boot with a minimum video mode which might work.

---

### Post by mimuwhen on 2017-06-28
Okay when I did that the machine boots up with full resolution.  This happens with any of the options under the advanced menu.  Display settings shows full 1024X768 resolution.  System profile shows "X.org foundation" under vendor and version 1.18.4.  Here is the result of the lshw command under this mode.  What do i do next?  Why will it work here but not in normal boot mode?  Should I make a new thread about this issue or should we keep going here?

```
computer
    descripción: Equipo de escritorio
    producto: MS-6712
    fabricante: MSI
    versión: 1.0
    serie: [REMOVED]
    anchura: 32 bits
    capacidades: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuración: chassis=desktop cpus=1
  *-core
       descripción: Placa base
       producto: MS-6712
       fabricante: MSI
       id físico: 0
       versión: 1.0
       serie: [REMOVED]
     *-firmware
          descripción: BIOS
          fabricante: American Megatrends Inc.
          id físico: 0
          versión: Version 07.00T
          date: 04/02/01
          tamaño: 64KiB
          capacidad: 192KiB
          capacidades: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          descripción: CPU
          producto: AMD Athlon(tm) XP
          fabricante: Advanced Micro Devices [AMD]
          id físico: 4
          información del bus: cpu@0
          versión: 6.10.0
          ranura: Socket-A
          tamaño: 1150MHz
          capacidad: 3GHz
          anchura: 32 bits
          reloj: 100MHz
          capacidades: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow eagerfpu 3dnowprefetch vmmcall
        *-cache:0
             descripción: L1 caché
             id físico: 5
             ranura: Internal Cache
             tamaño: 128KiB
             capacidad: 1MiB
             capacidades: synchronous internal write-back unified
             configuración: level=1
        *-cache:1
             descripción: L2 caché
             id físico: 6
             ranura: Internal Cache
             tamaño: 512KiB
             capacidad: 1MiB
             capacidades: synchronous internal write-back unified
             configuración: level=2
     *-memory
          descripción: Memoria de sistema
          id físico: 1
          tamaño: 1506MiB
     *-pci
          descripción: Host bridge
          producto: VT8377 [KT400/KT600 AGP] Host Bridge
          fabricante: VIA Technologies, Inc.
          id físico: 100
          información del bus: pci@0000:00:00.0
          versión: 80
          anchura: 32 bits
          reloj: 66MHz
          configuración: driver=agpgart-via latency=8
          recursos: irq:0 memoria:e0000000-e7ffffff
        *-pci
             descripción: PCI bridge
             producto: VT8237/VX700 PCI Bridge
             fabricante: VIA Technologies, Inc.
             id físico: 1
             información del bus: pci@0000:00:01.0
             versión: 00
             anchura: 32 bits
             reloj: 66MHz
             capacidades: pci pm normal_decode bus_master cap_list
        *-display NO RECLAMADO
             descripción: VGA compatible controller
             producto: 315PRO PCI/AGP VGA Display Adapter
             fabricante: Silicon Integrated Systems [SiS]
             id físico: 5
             información del bus: pci@0000:00:05.0
             versión: 00
             anchura: 32 bits
             reloj: 66MHz
             capacidades: pm vga_controller bus_master cap_list
             configuración: latency=39 maxlatency=16 mingnt=3
             recursos: memoria:c0000000-cfffffff memoria:dffc0000-dfffffff ioport:ec00(size=128) memoria:c0000-dffff
        *-communication
             descripción: Communication controller
             producto: PCI 1 port parallel adapter
             fabricante: MosChip Semiconductor Technology Ltd.
             id físico: 7
             información del bus: pci@0000:00:07.0
             versión: 01
             anchura: 32 bits
             reloj: 33MHz
             configuración: driver=parport_pc latency=32
             recursos: irq:18 ioport:e800(size=8) ioport:e400(size=8) ioport:e000(size=8) ioport:dc00(size=8) ioport:d800(size=8) ioport:d400(size=16)
        *-usb:0
             descripción: USB controller
             producto: VT82xx/62xx UHCI USB 1.1 Controller
             fabricante: VIA Technologies, Inc.
             id físico: 10
             información del bus: pci@0000:00:10.0
             versión: 80
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm uhci bus_master cap_list
             configuración: driver=uhci_hcd latency=32
             recursos: irq:21 ioport:c800(size=32)
           *-usbhost
                producto: UHCI Host Controller
                fabricante: Linux 4.8.0-56-generic uhci_hcd
                id físico: 1
                información del bus: usb@2
                nombre lógico: usb2
                versión: 4.08
                capacidades: usb-1.10
                configuración: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             descripción: USB controller
             producto: VT82xx/62xx UHCI USB 1.1 Controller
             fabricante: VIA Technologies, Inc.
             id físico: 10.1
             información del bus: pci@0000:00:10.1
             versión: 80
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm uhci bus_master cap_list
             configuración: driver=uhci_hcd latency=32
             recursos: irq:21 ioport:cc00(size=32)
           *-usbhost
                producto: UHCI Host Controller
                fabricante: Linux 4.8.0-56-generic uhci_hcd
                id físico: 1
                información del bus: usb@3
                nombre lógico: usb3
                versión: 4.08
                capacidades: usb-1.10
                configuración: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             descripción: USB controller
             producto: VT82xx/62xx UHCI USB 1.1 Controller
             fabricante: VIA Technologies, Inc.
             id físico: 10.2
             información del bus: pci@0000:00:10.2
             versión: 80
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm uhci bus_master cap_list
             configuración: driver=uhci_hcd latency=32
             recursos: irq:21 ioport:d000(size=32)
           *-usbhost
                producto: UHCI Host Controller
                fabricante: Linux 4.8.0-56-generic uhci_hcd
                id físico: 1
                información del bus: usb@4
                nombre lógico: usb4
                versión: 4.08
                capacidades: usb-1.10
                configuración: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   descripción: Ratón
                   producto: USB Optical Mouse
                   fabricante: Logitech
                   id físico: 1
                   información del bus: usb@4:1
                   versión: 43.01
                   capacidades: usb-2.00
                   configuración: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-usb:3
             descripción: USB controller
             producto: USB 2.0
             fabricante: VIA Technologies, Inc.
             id físico: 10.3
             información del bus: pci@0000:00:10.3
             versión: 82
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm ehci bus_master cap_list
             configuración: driver=ehci-pci latency=32
             recursos: irq:21 memoria:dffaff00-dffaffff
           *-usbhost
                producto: EHCI Host Controller
                fabricante: Linux 4.8.0-56-generic ehci_hcd
                id físico: 1
                información del bus: usb@1
                nombre lógico: usb1
                versión: 4.08
                capacidades: usb-2.00
                configuración: driver=hub slots=6 speed=480Mbit/s
        *-isa
             descripción: ISA bridge
             producto: VT8235 ISA Bridge
             fabricante: VIA Technologies, Inc.
             id físico: 11
             información del bus: pci@0000:00:11.0
             versión: 00
             anchura: 32 bits
             reloj: 33MHz
             capacidades: isa pm bus_master cap_list
             configuración: latency=0
        *-ide
             descripción: IDE interface
             producto: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             fabricante: VIA Technologies, Inc.
             id físico: 11.1
             información del bus: pci@0000:00:11.1
             versión: 06
             anchura: 32 bits
             reloj: 33MHz
             capacidades: ide pm bus_master cap_list
             configuración: driver=pata_via latency=32
             recursos: irq:255 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
        *-multimedia
             descripción: Multimedia audio controller
             producto: VT8233/A/8235/8237 AC97 Audio Controller
             fabricante: VIA Technologies, Inc.
             id físico: 11.5
             información del bus: pci@0000:00:11.5
             versión: 50
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm cap_list
             configuración: driver=snd_via82xx latency=0
             recursos: irq:22 ioport:c400(size=256)
        *-network
             descripción: Ethernet interface
             producto: VT6102/VT6103 [Rhine-II]
             fabricante: VIA Technologies, Inc.
             id físico: 12
             información del bus: pci@0000:00:12.0
             nombre lógico: enp0s18
             versión: 74
             serie: [REMOVED]
             tamaño: 100Mbit/s
             capacidad: 100Mbit/s
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuración: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=full ip=[REMOVED] latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             recursos: irq:23 ioport:c000(size=256) memoria:dffafe00-dffafeff
     *-scsi:0
          id físico: 2
          nombre lógico: scsi0
          capacidades: emulated
        *-disk
             descripción: ATA Disk
             producto: ST340810A
             fabricante: Seagate
             id físico: 0.0.0
             información del bus: scsi@0:0.0.0
             nombre lógico: /dev/sda
             versión: 3.39
             serie: [REMOVED]
             tamaño: 37GiB (40GB)
             capacidades: partitioned partitioned:dos
             configuración: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=942abb48
           *-volume:0
                descripción: partición EXT4
                fabricante: Linux
                id físico: 1
                información del bus: scsi@0:0.0.0,1
                nombre lógico: /dev/sda1
                nombre lógico: /
                versión: 1.0
                serie: [REMOVED]
                tamaño: 35GiB
                capacidad: 35GiB
                capacidades: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuración: created=2017-06-27 01:36:27 filesystem=ext4 lastmountpoint=/ modified=2017-06-28 18:52:50 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-06-28 18:51:53 state=mounted
           *-volume:1
                descripción: Extended partition
                id físico: 2
                información del bus: scsi@0:0.0.0,2
                nombre lógico: /dev/sda2
                tamaño: 1534MiB
                capacidad: 1534MiB
                capacidades: primary extended partitioned partitioned:extended
              *-logicalvolume
                   descripción: Linux swap / Solaris partition
                   id físico: 5
                   nombre lógico: /dev/sda5
                   capacidad: 1534MiB
                   capacidades: nofs
     *-scsi:1
          id físico: 3
          nombre lógico: scsi1
          capacidades: emulated
        *-cdrom:0
             descripción: DVD writer
             producto: DVD RW DW-Q28A
             fabricante: SONY
             id físico: 0.0.0
             información del bus: scsi@1:0.0.0
             nombre lógico: /dev/cdrom
             nombre lógico: /dev/dvd
             nombre lógico: /dev/dvdrw
             nombre lógico: /dev/sr0
             versión: KYS3
             capacidades: removable audio cd-r cd-rw dvd dvd-r
             configuración: ansiversion=5 status=nodisc
        *-cdrom:1
             descripción: CD-R/CD-RW writer
             id físico: 0.1.0
             información del bus: scsi@1:0.1.0
             nombre lógico: /dev/cdrw
             nombre lógico: /dev/sr1
             capacidades: audio cd-r cd-rw
             configuración: status=nodisc


```

---

### Post by ubfan1 on 2017-06-28
You probably would be better off with a new thread with "SIS 315pro video problem" in the title.  I don't know anything about the card myself, or what video you are running since the display still says not claimed.

---

