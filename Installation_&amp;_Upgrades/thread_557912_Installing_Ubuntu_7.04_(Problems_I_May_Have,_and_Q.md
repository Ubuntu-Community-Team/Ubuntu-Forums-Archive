---
title: "Installing Ubuntu 7.04 (Problems I May Have, and Questions)"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by AMT on 2007-09-23
Alright, well I got a new hard drive recently and I found that Windows was only able to detect it when I connected the HDD to the single SATA_RAID2 connector near the processor. Even then, I had to use a floppy to load the Silicon 3132 Controller during installation of Windows. I'm guessing this is because the drive is SATAII, and I don't think the southbridge connectors support it?

So, having had issues with using proprietary controllers before (ITE8211), I wanted to make 101% sure that Ubuntu 7.04 would work when I try to install it with the Live CD. I've done some research myself, and I found out that the problem I was having before when I was trying to install Ubuntu wasn't actually caused by the hard drive (sense Ubuntu Live CD should only have loaded stuff to the RAM). At least, it shouldn't have...

When I tried to install Ubuntu before, it would lock up when loading the Live CD. It would be unresponsive, and the screen was all screwed up, so I was forced to restart manually. When I did so, the hard drive boot had somehow been corrupted, and the only way I could recover the drive was to take it out, get my data, and reformat it using Windows on another computer. I'm curious as to why the Ubuntu Live CD even thinks about looking at the hard drive. The whole point of using a Live CD is for the sole purpose of keeping the users previous installation in tact while exploring the OS! Isn't it? Oh well ...

So, not wanting to do that again, I need to be sure if I can install Ubuntu before I go and and have linux screw up my hard drive. Here are my specs...

ASUS P5LD2 Deluxe Motherboard
Intel Pentium D 920 2.8 GHz Processor
WD3200AAKS 320 GB SATAII Hard Drive
2 Gigs of DDR2 DIMM Enabled RAM
eVGA GeForce 7800GT Video Card
Sound Blaster Audigy 2 Sound Card
Sony DVD Burner
ASUS DVD-ROM Drive
3.5" Floppy Drive

Thanks in advanced. If I'm missing anything from the list above that could help you help me, let me know!

---

### Post by banewman on 2007-09-23
This how to might help - [http://ubuntuforums.org/showthread.php?t=2557](http://ubuntuforums.org/showthread.php?t=2557) :lolflag:

---

### Post by AMT on 2007-09-23
> **banewman said:**
> This how to might help - [http://ubuntuforums.org/showthread.php?t=2557](http://ubuntuforums.org/showthread.php?t=2557) :lolflag:

Well, that would help the hard drive not getting detected during installation, but I'm not sure that would help when loading the Live CD.

---

### Post by Pumalite on 2007-09-23
This would help to load the Live CD:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

---

### Post by AMT on 2007-09-23
> **Pumalite said:**
> This would help to load the Live CD:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit
Thanks! So this should at least get me into the Live CD and allow me to restart safely back into my Windows installation? Just curious, what exactly does this do other than present a command prompt?

---

### Post by Pumalite on 2007-09-23
What I posted above is to boot Ubuntu Live CD for people that have trouble booting it and nevertheless want to try it.
You have to restate your Windows problem.

---

### Post by AMT on 2007-09-23
> **Pumalite said:**
> You have to restate your Windows problem.

Well, when I tried installing Ubuntu 7.04 before, it would lock up when trying to load the Live CD (after orange loading bar). I was forced to reboot manually. When I did that, the hard drive could no longer boot to my Windows installation and I could only fix it by reformatting the Hard Drive using another Windows computer.

I'm going to try what you suggested, I've barely got anything reinstalled on this hard drive yet, and I can always get any data I need using another computer.

---

### Post by Pumalite on 2007-09-23
If the Ubuntu installation goes bad, you can always get into Windows with your installation CD: hit 'r' for Recovery>FIXMBR>FIXBOOT.

---

### Post by AMT on 2007-09-23
> **Pumalite said:**
> If the Ubuntu installation goes bad, you can always get into Windows with your installation CD: hit 'r' for Recovery>FIXMBR>FIXBOOT.
That never worked unfortunately...

But I just found out that by pressing the power button on my case instead of the the restart button Ubuntu will unload itself and Windows will boot fine. I wish I had known that earlier.

Anyways, I tried what you suggested, but it didn't work. Once it got to the splash screen where all the icons show up, it just locked up. I could move the mouse around, but the the splash screen was all screwed up (like someone cut the image 100 times horizontally and moved all the pieces left or right).

---

### Post by Pumalite on 2007-09-23
Try the Alternate CD then. It's easier to install and you have more control over the installation.

---

### Post by AMT on 2007-09-23
> **Pumalite said:**
> Try the Alternate CD then. It's easier to install and you have more control over the installation.
Well, I've got it installed and GRUB is setup and working fine with Windows and Ubuntu. Ubuntu loads and I can even view the login screen. Unfortunately, as soon as I log in, the same problem with the splash screen occurs. I'm guessing its a video card issue. Any suggestions?

Regardless, I'm happy I got further than I did before! Thanks for all your help! :KS

---

### Post by Pumalite on 2007-09-23
Ctrl+Alr+F1 to get a command line if you don't have one.
At the command line:

sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by AMT on 2007-09-23
It's working now! Thanks so much!

[http://www.amtstudios.com/announcements/ubuntu/](http://www.amtstudios.com/announcements/ubuntu/)

---

### Post by Pumalite on 2007-09-23
You are welcome. Happy Ubuntuing!

---

### Post by AMT on 2007-09-23
Everything is running great so far, but there are a few things I'm stuck on...

1. The nVidia "non-free" drivers were supposedly included with Ubuntu 7.04, how am I sure they are using the latest version (released Sept 18, 2007).

2. How do I get Beryl to load when I start Ubuntu?

3. I have the linux version of Teamspeak installed. I can hear everyone great, but I echo when I don't have my mic muted. I know how to fix this in Windows, but I can't find a place to select the recording device in Ubuntu.

---

### Post by Pumalite on 2007-09-23
Post:
lshw

---

### Post by AMT on 2007-09-23
> **Pumalite said:**
> Post:
lshw

I was wondering what the "dxdiag" tool for Linux was! Anyways, I can now talk on Teamspeak if I set the capture device to ADC Capture/Standard PCM Playback, only thing is I'm really quiet. How do I enable +20 db Mic boost in Ubuntu?

```
 description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2026MB
     *-cpu
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.6.2
          serial: 0000-0F62-0000-0000-0000-0000
          size: 18EHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc pni monitor ds_cpl vmx cid cx16 xtpr lahf_lm
          configuration: id=1
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
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 81
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G70 [GeForce 7800 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@05:00.0
                version: a1
                size: 256MB
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: iomemory:df000000-dfffffff iomemory:e0000000-efffffff iomemory:de000000-deffffff ioport:e800-e87f irq:16
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@00:1c.4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8053 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@03:00.0
                logical name: eth0
                version: 15
                serial: 00:13:d4:1a:42:f3
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A ip=192.168.0.4 latency=0 multicast=yes
                resources: iomemory:ddefc000-ddefffff ioport:c800-c8ff irq:16
        *-pci:3
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@00:1c.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: Mass storage controller
                product: SiI 3132 Serial ATA Raid II Controller
                vendor: Silicon Image, Inc.
                physical id: 0
                bus info: pci@02:00.0
                logical name: scsi2
                logical name: scsi3
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list scsi-host
                configuration: driver=sata_sil24 latency=0
                resources: iomemory:dddffc00-dddffc7f iomemory:dddf8000-dddfbfff ioport:b800-b87f irq:17
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:7000-701f irq:20
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Mouse
                   product: USB-PS/2 Optical Mouse
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@1:1
                   version: 18.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
              *-usb:1
                   description: Keyboard
                   product: HID compliant keyboard
                   vendor: Logitech
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.80
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:7400-741f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Human interface device
                   product: Logitech Extreme 3D
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@2:1
                   version: 2.04
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=30mA speed=1.5MB/s
              *-usb:1
                   description: Printer
                   product: Dell Photo Printer 720
                   vendor: Dell
                   physical id: 2
                   bus info: usb@2:2
                   version: 1.00
                   serial: 9NP5F71
                   capabilities: usb-2.00 bidirectional
                   configuration: driver=usblp maxpower=4mA speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:7800-781f irq:21
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:8000-801f irq:22
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:ddbff800-ddbffbff irq:20
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-multimedia
                description: Multimedia audio controller
                product: SB0400 Audigy2 Value
                vendor: Creative Labs
                physical id: 2
                bus info: pci@01:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2
                resources: ioport:a800-a83f irq:23
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@01:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: iomemory:ddcff800-ddcfffff iomemory:ddcf8000-ddcfbfff irq:19
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
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
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:ffa0-ffaf irq:18
           *-cdrom:0
                description: DVD-RAM writer
                product: DVD RW AD-7170A
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                serial: [Optiarc DVD RW AD-7170A 1.02 Jul14,2006
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
           *-cdrom:1
                description: DVD reader
                product: DVD-E616P2
                vendor: ASUS
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.03
                capabilities: removable audio dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/scd1
        *-storage
             description: SATA controller
             product: 82801GR/GH (ICH7 Family) Serial ATA Storage Controller AHCI
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi4
             logical name: scsi5
             logical name: scsi6
             logical name: scsi7
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list scsi-host
             configuration: driver=ahci latency=0
             resources: ioport:9800-9807 ioport:9400-9403 ioport:9000-9007 ioport:8800-8803 ioport:8400-840f iomemory:ddbffc00-ddbfffff irq:23
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400-41f
```

---

### Post by Pumalite on 2007-09-23
Check System>Administration and see if you have a Restricted drivers Manager.

---

### Post by AMT on 2007-09-23
> **Pumalite said:**
> Check System>Administration and see if you have a Restricted drivers Manager.
Yes for nVidia. I knew that the drivers were there, but I wasn't sure if those were the latest ones...

So how to enable Mic Boost?

---

### Post by Pumalite on 2007-09-23
Check Mutimedia & Video.

---

### Post by AMT on 2007-09-23
> **Pumalite said:**
> Check Mutimedia & Video.
I don't see anything there that would help...

---

### Post by Pumalite on 2007-09-23
Post your question.

---

### Post by Pumalite on 2007-09-23
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by AMT on 2007-09-23
Alright, well I got that working. And looks like the latest drivers are being used for my video card. Just a shame that Wine doesn't have support for DirectX 9 yet.

So last on my list: How do I get Beryl Manager to load when I login to my account on Ubuntu?

---

