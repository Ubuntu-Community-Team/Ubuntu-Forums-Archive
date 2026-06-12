---
title: "audigy camera ICH5"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by panaretos22 on 2007-12-13
i have recently install ubuntu i have serache to find whicdh sound cart i have and shows this:
audigy camera ICH5
i dont have any audio in my pc how can i fix it?

---

### Post by Pumalite on 2007-12-13
Post:
lshw -C sound

---

### Post by panaretos22 on 2007-12-13
hardware lister B.02.08.01

---

### Post by Pumalite on 2007-12-13
Copy and paste the output.

---

### Post by panaretos22 on 2007-12-13
B.02.08.01
this?sorry but i am new in ubuntu

---

### Post by Pumalite on 2007-12-13
Type the following in your Applications>Accessories>Terminal:
lshw -C sound
Press 'Enter'
Copy and paste the output here.

---

### Post by panaretos22 on 2007-12-13
*-usb                   
       
description: Audio device
       
product: USB camera
       
physical id: 2
       
bus info: usb@3:2
      
version: 1.01
       
capabilities: usb-1.10 audio-control
       
configuration: driver=snd-usb-audio maxpower=500mA speed=12.0MB/s
  
*-multimedia
       
description: Multimedia audio controller
       
product: SB Audigy
       
vendor: Creative Labs
       
physical id: 3
       
bus info: pci@02:03.0
       
version: 03
       
width: 32 bits
       
clock: 33MHz
       
capabilities: bus_master cap_list
      
configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
       
resources: ioport:b400-b41f irq:18
  
*-multimedia
       
description: Multimedia audio controller
       
product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       
vendor: Intel Corporation
       
physical id: 1f.5
       
bus info: pci@00:1f.5
       
version: 02
       
width: 32 bits
       
clock: 33MHz
       
capabilities: bus_master cap_list
       
configuration: driver=Intel ICH latency=0
       
resources: ioport:c800-c8ff ioport:c400-c43f iomemory:ffeffa00-ffeffbff iomemory:ffeff900-ffeff9ff irq:20

---

### Post by Pumalite on 2007-12-13
Post:
lshw

---

### Post by panaretos22 on 2007-12-13
description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1011MB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.3.3
          serial: 0000-0F33-0000-0000-0000-0000
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pni monitor ds_cpl cid
          configuration: id=0
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
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: f8000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f8000000-fbffffff
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display:0
                description: VGA compatible controller
                product: RV530LE [Radeon X1600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 256MB
                width: 64 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=32 mingnt=8
                resources: iomemory:e0000000-efffffff iomemory:ffcf0000-ffcfffff ioport:a800-a8ff irq:11
           *-display:1 UNCLAIMED
                description: Display controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 00
                size: 64KB
                width: 64 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=32 mingnt=8
                resources: iomemory:ffce0000-ffceffff
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:cc00-cc1f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d000-d01f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Audio device
                   product: USB camera
                   physical id: 2
                   bus info: usb@3:2
                   version: 1.01
                   capabilities: usb-1.10 audio-control
                   configuration: driver=snd-usb-audio maxpower=500mA speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d400-d41f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d800-d81f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:ffeffc00-ffefffff irq:16
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k HSFi Modem
                vendor: Conexant
                physical id: 2
                bus info: pci@02:02.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32
                resources: iomemory:ffdf0000-ffdfffff ioport:b800-b807 irq:10
           *-multimedia
                description: Multimedia audio controller
                product: SB Audigy
                vendor: Creative Labs
                physical id: 3
                bus info: pci@02:03.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
                resources: ioport:b400-b41f irq:18
           *-input
                description: Input device controller
                product: SB Audigy Game Port
                vendor: Creative Labs
                physical id: 3.1
                bus info: pci@02:03.1
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=32
                resources: ioport:bc00-bc07
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: b
                bus info: pci@02:0b.0
                logical name: eth0
                version: 10
                serial: 00:11:09:60:37:46
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.100 latency=32 maxlatency=64 mingnt=32 multicast=yes
                resources: ioport:b000-b0ff iomemory:ffdeff00-ffdeffff irq:16
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:fc00-fc0f iomemory:50100000-501003ff irq:19
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:ec00-ec07 ioport:e800-e803 ioport:e400-e407 ioport:e000-e003 ioport:dc00-dc0f irq:19
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:c00-c1f irq:10
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: ioport:c800-c8ff ioport:c400-c43f iomemory:ffeffa00-ffeffbff iomemory:ffeff900-ffeff9ff irq:20

---

### Post by Pumalite on 2007-12-13
Do this first(at the Terminal):
sudo apt-get install linux-backports-modules-generic
'Enter'
Then type:
alsamixer
'Enter'
Post the results.

---

### Post by panaretos22 on 2007-12-13
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Pumalite on 2007-12-13
Is Synaptic open? Have to close it before you run the command.

---

### Post by panaretos22 on 2007-12-13
what is synaptic ??

---

### Post by panaretos22 on 2007-12-13
Card: Audigy 1 ES [SB0160]                                                   &#9474;
&#9474; Chip: SigmaTel STAC9721,23                                                   &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00]                                                  &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;               &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;               &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;               &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;               &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;               &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;               &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9484;&#9472;&#9472;&#9488;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9484;&#9472;&#9472;&#9488;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;             &#9474;MM&#9474;                        &#9474;MM&#9474;                                 &#9474;
&#9474;             &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;                                 &#9474;
&#9474;     100              50<>50   50<>50                0     80<>80     100     &#9474;
&#9474; < Master >  Tone      Bass    Treble  3D Contr  3D Contr   PCM    PCM Cent

---

### Post by Pumalite on 2007-12-13
[http://ubuntuforums.org/showthread.php?t=616846](http://ubuntuforums.org/showthread.php?t=616846)
[http://ubuntuforums.org/showthread.php?t=604084](http://ubuntuforums.org/showthread.php?t=604084)
[http://ubuntuforums.org/showthread.php?t=569280](http://ubuntuforums.org/showthread.php?t=569280)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound)
[http://ubuntuforums.org/showthread.p...ght=sound+will](http://ubuntuforums.org/showthread.p...ght=sound+will)
[http://ubuntuforums.org/showpost.php?p=3588321&postcount=5](http://ubuntuforums.org/showpost.php?p=3588321&postcount=5)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/#comment-6](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/#comment-6)
[http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage)

---

