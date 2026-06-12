---
title: "No network interfaces detected"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by Gadgetboy on 2008-05-17
I have a very old Compaq Presario computer and when I install Ubuntu it says "No network interfaces detected" and we put a Kingston kne20t network card  and both the card and the switch lights are lit.

How do we get it to detect?

Sincerely,
Gadgetboy

---

### Post by Pumalite on 2008-05-17
How do you get your signal?

---

### Post by Gadgetboy on 2008-05-17
Wired network

---

### Post by Pumalite on 2008-05-17
Best way is with a router providing you DHCP at boot with dynamic IP

---

### Post by Gadgetboy on 2008-05-17
The network is connecting and working we have many other computers on the network.

The problem is during the install the install does not find the network card.

How do I get the install to find my network card?

Its a Kingston

---

### Post by Pumalite on 2008-05-17
Have you installed already?

---

### Post by Gadgetboy on 2008-05-17
We can't get it installed because of this network issue.

---

### Post by jlbprof on 2008-05-18
[bump]

Gadget and I are working on this.

How do we deal with the install not finding the network card when you know it is there and is a good card?

Thanx

Bodger

---

### Post by Pumalite on 2008-05-18
Boot the Live CD and post:
lshw

---

### Post by jlbprof on 2008-05-18
Here is the output from lshw

I do not see it in the lshw response.

```

jules-linux
    description: Mini Tower Computer
    width: 32 bits
    capabilities: smbios-2.1 dmi-2.1
    configuration: chassis=mini-tower uuid=36393135-434D-585A-4130-343900000000
  *-core
       description: Motherboard
       physical id: 0
     *-firmware:0
          description: BIOS
          vendor: Compaq
          physical id: 0
          version: 686S5 (03/10/99)
          size: 64KiB
          capacity: 192KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot biosbootspecification netboot
     *-firmware:1
          description: BIOS
          physical id: 3
          version: None
          size: 1023KiB
          capabilities: apm bootselect socketedrom int13floppy360 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video
     *-firmware:2
          description: BIOS
          physical id: 802
          size: 1015KiB
          capabilities: eisa pcmcia pnp apm upgrade vesa escd bootselect pcmciaboot edd int13floppytoshiba int13floppy360 int14serial int17printer int10video
     *-cpu
          description: CPU
          product: AMD-K6(tm) 3D+ Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 5.9.1
          slot: U1
          size: 400MHz
          capacity: 600MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr cx8 pge mmx syscall 3dnow k6_mtrr up
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: CACHE1
             size: 64KiB
             capacity: 64KiB
             capabilities: internal varies
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: CACHE2
             size: 256KiB
             capacity: 256KiB
             capabilities: internal varies
     *-cache DISABLED
          description: L3 cache
          physical id: 7
          slot: CACHE3
          size: 1MiB
          capacity: 1MiB
          capabilities: external write-through
     *-firmware:3
          description: BIOS
          physical id: 5
          size: 1MiB
     *-firmware:4
          description: BIOS
          physical id: 6
          size: 1MiB
     *-firmware:5
          description: BIOS
          physical id: 8
          size: 1MiB
     *-firmware:6
          description: BIOS
          physical id: 9
          size: 1MiB
     *-firmware:7
          description: BIOS
          physical id: a
          size: 1MiB
     *-firmware:8
          description: BIOS
          physical id: b
          size: 1MiB
     *-firmware:9
          description: BIOS
          physical id: c
          size: 1MiB
     *-firmware:10
          description: BIOS
          physical id: d
          size: 1MiB
     *-firmware:11
          description: BIOS
          physical id: e
          size: 1MiB
     *-firmware:12
          description: BIOS
          physical id: f
          size: 1MiB
     *-firmware:13
          description: BIOS
          physical id: 10
          size: 1MiB
     *-firmware:14
          description: BIOS
          physical id: 11
          size: 1MiB
     *-firmware:15
          description: BIOS
          physical id: 12
          size: 1MiB
     *-firmware:16
          description: BIOS
          physical id: 13
          size: 1MiB
     *-firmware:17
          description: BIOS
          physical id: 14
          size: 1MiB
     *-firmware:18
          description: BIOS
          physical id: 15
          size: 1MiB
     *-firmware:19
          description: BIOS
          physical id: 16
          size: 1MiB
     *-firmware:20
          description: BIOS
          physical id: 17
          size: 1MiB
     *-firmware:21
          description: BIOS
          physical id: 18
          size: 1MiB
     *-firmware:22
          description: BIOS
          physical id: 19
          size: 1MiB
     *-firmware:23
          description: BIOS
          physical id: 1a
          size: 1MiB
     *-firmware:24
          description: BIOS
          physical id: 1b
          size: 1MiB
     *-firmware:25
          description: BIOS
          physical id: 1c
          size: 1MiB
     *-firmware:26
          description: BIOS
          physical id: 1d
          size: 1MiB
     *-firmware:27
          description: BIOS
          physical id: 1e
          size: 1MiB
     *-firmware:28
          description: BIOS
          physical id: 1f
          size: 1MiB
     *-firmware:29
          description: BIOS
          physical id: 20
          size: 1MiB
     *-firmware:30
          description: BIOS
          physical id: 21
          size: 1MiB
     *-firmware:31
          description: BIOS
          physical id: 22
          size: 1MiB
     *-firmware:32
          description: BIOS
          physical id: 23
          size: 1MiB
     *-firmware:33
          description: BIOS
          physical id: 24
          size: 1MiB
     *-firmware:34
          description: BIOS
          physical id: 25
          size: 1MiB
     *-firmware:35
          description: BIOS
          physical id: 26
          size: 1MiB
     *-firmware:36
          description: BIOS
          physical id: 27
          size: 1MiB
     *-firmware:37
          description: BIOS
          physical id: 28
          size: 1MiB
     *-firmware:38
          description: BIOS
          physical id: 29
          size: 1MiB
     *-firmware:39
          description: BIOS
          physical id: 2a
          size: 1MiB
     *-firmware:40
          description: BIOS
          physical id: 2b
          size: 1MiB
     *-firmware:41
          description: BIOS
          physical id: 2c
          size: 1MiB
     *-firmware:42
          description: BIOS
          physical id: 2d
          size: 1MiB
     *-firmware:43
          description: BIOS
          physical id: 2e
          size: 1MiB
     *-firmware:44
          description: BIOS
          physical id: 2f
          size: 1MiB
     *-firmware:45
          description: BIOS
          physical id: 30
          size: 1MiB
     *-firmware:46
          description: BIOS
          physical id: 31
          size: 1MiB
     *-firmware:47
          description: BIOS
          physical id: 32
          size: 1MiB
     *-firmware:48
          description: BIOS
          physical id: 33
          size: 1MiB
     *-firmware:49
          description: BIOS
          physical id: 34
          size: 1MiB
     *-firmware:50
          description: BIOS
          physical id: 35
          size: 1MiB
     *-firmware:51
          description: BIOS
          physical id: 36
          size: 1MiB
     *-firmware:52
          description: BIOS
          physical id: 37
          size: 1MiB
          capabilities: int5printscreen
     *-firmware:53
          description: BIOS
          physical id: 38
          size: 1MiB
          capabilities: apm
     *-firmware:54
          description: BIOS
          physical id: 39
          size: 1MiB
     *-firmware:55
          description: BIOS
          physical id: 3a
          size: 1008KiB
     *-firmware:56
          description: BIOS
          physical id: 3b
          size: 1MiB
     *-firmware:57
          description: BIOS
          physical id: 400
          size: 1MiB
     *-firmware:58
          description: BIOS
          physical id: 3c
          size: 1MiB
     *-firmware:59
          description: BIOS
          physical id: 3d
          size: 1MiB
     *-firmware:60
          description: BIOS
          physical id: 3e
          size: 1MiB
     *-firmware:61
          description: BIOS
          physical id: 3f
          size: 1MiB
     *-firmware:62
          description: BIOS
          physical id: 40
          size: 1MiB
     *-firmware:63
          description: BIOS
          physical id: 41
          size: 1MiB
     *-firmware:64
          description: BIOS
          physical id: 42
          size: 1MiB
     *-firmware:65
          description: BIOS
          physical id: 43
          size: 1MiB
          capabilities: bootselect
     *-firmware:66
          description: BIOS
          physical id: 44
          size: 1MiB
     *-firmware:67
          description: BIOS
          physical id: 45
          size: 1MiB
     *-firmware:68
          description: BIOS
          physical id: 46
          size: 1023KiB
     *-firmware:69
          description: BIOS
          physical id: 47
          size: 1MiB
     *-firmware:70
          description: BIOS
          physical id: 1
          size: 1MiB
     *-firmware:71
          description: BIOS
          physical id: 48
          size: 1MiB
     *-firmware:72
          description: BIOS
          physical id: 49
          size: 1MiB
     *-firmware:73
          description: BIOS
          physical id: 4a
          size: 1MiB
     *-firmware:74
          description: BIOS
          physical id: 4b
          size: 1MiB
     *-firmware:75
          description: BIOS
          physical id: 4c
          size: 1MiB
     *-firmware:76
          description: BIOS
          physical id: 4d
          size: 1MiB
     *-firmware:77
          description: BIOS
          physical id: 4e
          size: 1MiB
     *-firmware:78
          description: BIOS
          physical id: 4f
          size: 1MiB
     *-firmware:79
          description: BIOS
          physical id: 50
          size: 1MiB
     *-firmware:80
          description: BIOS
          physical id: 51
          size: 1MiB
     *-firmware:81
          description: BIOS
          physical id: 52
          size: 1MiB
     *-firmware:82
          description: BIOS
          physical id: 53
          size: 1MiB
     *-firmware:83
          description: BIOS
          physical id: 54
          size: 1MiB
     *-firmware:84
          description: BIOS
          physical id: 55
          size: 1MiB
     *-firmware:85
          description: BIOS
          physical id: 56
          size: 1MiB
     *-firmware:86
          description: BIOS
          physical id: 57
          size: 1MiB
     *-firmware:87
          description: BIOS
          physical id: 58
          size: 1MiB
     *-firmware:88
          description: BIOS
          physical id: 59
          size: 1MiB
     *-firmware:89
          description: BIOS
          physical id: 5a
          size: 1MiB
     *-firmware:90
          description: BIOS
          physical id: 5b
          size: 1MiB
     *-firmware:91
          description: BIOS
          physical id: 5c
          size: 1MiB
     *-firmware:92
          description: BIOS
          physical id: 5d
          size: 1MiB
     *-firmware:93
          description: BIOS
          physical id: 5e
          size: 1MiB
     *-firmware:94
          description: BIOS
          physical id: 5f
          size: 1MiB
     *-firmware:95
          description: BIOS
          physical id: 60
          size: 1MiB
     *-firmware:96
          description: BIOS
          physical id: 61
          size: 1MiB
     *-firmware:97
          description: BIOS
          physical id: 62
          size: 1MiB
     *-firmware:98
          description: BIOS
          physical id: 63
          size: 1MiB
     *-firmware:99
          description: BIOS
          physical id: 64
          size: 1MiB
     *-firmware:100
          description: BIOS
          physical id: 65
          size: 1MiB
     *-firmware:101
          description: BIOS
          physical id: 66
          size: 1MiB
     *-firmware:102
          description: BIOS
          physical id: 67
          size: 1MiB
     *-firmware:103
          description: BIOS
          physical id: 68
          size: 1MiB
     *-firmware:104
          description: BIOS
          physical id: 69
          size: 1MiB
     *-firmware:105
          description: BIOS
          physical id: 6a
          size: 1MiB
     *-firmware:106
          description: BIOS
          physical id: 6b
          size: 1MiB
     *-firmware:107
          description: BIOS
          physical id: 6c
          size: 1MiB
     *-firmware:108
          description: BIOS
          physical id: 6d
          size: 1MiB
     *-firmware:109
          description: BIOS
          physical id: 6e
          size: 1MiB
     *-firmware:110
          description: BIOS
          physical id: 6f
          size: 1MiB
     *-firmware:111
          description: BIOS
          physical id: 70
          size: 1MiB
     *-firmware:112
          description: BIOS
          physical id: 71
          size: 1MiB
     *-firmware:113
          description: BIOS
          physical id: 72
          size: 1MiB
          capabilities: int10video
     *-firmware:114
          description: BIOS
          physical id: 73
          size: 1MiB
          capabilities: escd
     *-firmware:115
          description: BIOS
          physical id: 74
          size: 1MiB
          capacity: 4MiB
     *-firmware:116
          description: BIOS
          physical id: 75
          size: 768KiB
     *-firmware:117
          description: BIOS
          physical id: 76
          size: 1MiB
     *-firmware:118
          description: BIOS
          physical id: 4000
          size: 1MiB
     *-firmware:119
          description: BIOS
          physical id: 77
          size: 1MiB
     *-firmware:120
          description: BIOS
          physical id: 78
          size: 1MiB
     *-firmware:121
          description: BIOS
          physical id: 79
          size: 1MiB
     *-firmware:122
          description: BIOS
          physical id: 7a
          size: 1MiB
     *-firmware:123
          description: BIOS
          physical id: 7b
          size: 1MiB
     *-firmware:124
          description: BIOS
          physical id: 7c
          size: 1MiB
     *-firmware:125
          description: BIOS
          physical id: 7d
          size: 1MiB
     *-firmware:126
          description: BIOS
          physical id: 7e
          size: 1MiB
     *-firmware:127
          description: BIOS
          physical id: 7f
          size: 1MiB
     *-firmware:128
          description: BIOS
          physical id: 80
          size: 1MiB
     *-firmware:129
          description: BIOS
          physical id: 81
          size: 1MiB
     *-firmware:130
          description: BIOS
          physical id: 82
          size: 1MiB
     *-firmware:131
          description: BIOS
          physical id: 83
          size: 1MiB
     *-firmware:132
          description: BIOS
          physical id: 84
          size: 1MiB
     *-firmware:133
          description: BIOS
          physical id: 85
          size: 1MiB
     *-firmware:134
          description: BIOS
          physical id: 86
          size: 1MiB
     *-firmware:135
          description: BIOS
          physical id: 87
          size: 1MiB
     *-firmware:136
          description: BIOS
          physical id: 88
          size: 1MiB
     *-firmware:137
          description: BIOS
          physical id: 89
          size: 1MiB
     *-firmware:138
          description: BIOS
          physical id: 8a
          size: 1MiB
     *-firmware:139
          description: BIOS
          physical id: 8b
          size: 1MiB
     *-firmware:140
          description: BIOS
          physical id: 8c
          size: 1MiB
     *-firmware:141
          description: BIOS
          physical id: 8d
          size: 1MiB
     *-firmware:142
          description: BIOS
          physical id: 8e
          size: 1MiB
     *-firmware:143
          description: BIOS
          physical id: 8f
          size: 1MiB
     *-firmware:144
          description: BIOS
          physical id: 90
          size: 1MiB
     *-firmware:145
          description: BIOS
          physical id: 91
          size: 1MiB
     *-firmware:146
          description: BIOS
          physical id: 92
          size: 1MiB
     *-firmware:147
          description: BIOS
          physical id: 93
          size: 1MiB
     *-firmware:148
          description: BIOS
          physical id: 94
          size: 1MiB
     *-firmware:149
          description: BIOS
          physical id: 95
          size: 1MiB
          capabilities: int13floppy2880 int5printscreen int14serial int17printer
     *-firmware:150
          description: BIOS
          physical id: 96
          size: 1MiB
          capabilities: pnp apm shadowing vesa bootselect edd int13floppynec int13floppytoshiba int13floppy720 int14serial int17printer
     *-firmware:151
          description: BIOS
          physical id: 97
          size: 1MiB
          capacity: 3456KiB
     *-firmware:152
          description: BIOS
          physical id: 98
          size: 808KiB
          capacity: 3136KiB
          capabilities: isa mca pcmcia pnp escd bootselect pcmciaboot edd int13floppy360 int9keyboard int14serial int10video
     *-firmware:153
          description: BIOS
          physical id: 99
          size: 827KiB
          capacity: 4288KiB
     *-firmware:154
          description: BIOS
          physical id: 3600
          size: 755KiB
          capacity: 5632KiB
     *-firmware:155
          description: BIOS
          physical id: 3139
          size: 670KiB
          capacity: 4160KiB
          capabilities: isa mca apm shadowing vesa bootselect edd int13floppynec int13floppytoshiba
     *-firmware:156
          description: BIOS
          physical id: 9a
          size: 1MiB
     *-firmware:157
          description: BIOS
          physical id: 9b
          size: 1MiB
     *-firmware:158
          description: BIOS
          physical id: 9c
          size: 1MiB
     *-firmware:159
          description: BIOS
          physical id: 9d
          size: 1MiB
     *-firmware:160
          description: BIOS
          physical id: 9e
          size: 1MiB
     *-firmware:161
          description: BIOS
          physical id: 9f
          size: 1MiB
     *-firmware:162
          description: BIOS
          physical id: a0
          size: 1MiB
     *-firmware:163
          description: BIOS
          physical id: a1
          size: 1MiB
     *-firmware:164
          description: BIOS
          physical id: a2
          size: 1MiB
     *-firmware:165
          description: BIOS
          physical id: a3
          size: 1MiB
     *-firmware:166
          description: BIOS
          physical id: a4
          size: 1MiB
     *-firmware:167
          description: BIOS
          physical id: a5
          size: 1MiB
     *-firmware:168
          description: BIOS
          physical id: a6
          size: 1MiB
     *-firmware:169
          description: BIOS
          physical id: a7
          size: 1MiB
     *-firmware:170
          description: BIOS
          physical id: a8
          size: 1MiB
     *-firmware:171
          description: BIOS
          physical id: a9
          size: 1MiB
     *-firmware:172
          description: BIOS
          physical id: aa
          size: 1MiB
     *-firmware:173
          description: BIOS
          physical id: ab
          size: 1MiB
     *-firmware:174
          description: BIOS
          physical id: ac
          size: 1MiB
     *-firmware:175
          description: BIOS
          physical id: ad
          size: 1MiB
     *-firmware:176
          description: BIOS
          physical id: ae
          size: 1MiB
     *-firmware:177
          description: BIOS
          physical id: af
          size: 1MiB
     *-firmware:178
          description: BIOS
          physical id: b0
          size: 1MiB
          capabilities: socketedrom
     *-firmware:179
          description: BIOS
          physical id: b1
          size: 1MiB
     *-firmware:180
          description: BIOS
          physical id: b2
          size: 1MiB
     *-firmware:181
          description: BIOS
          physical id: b3
          size: 1023KiB
     *-firmware:182
          description: BIOS
          physical id: b4
          size: 1MiB
     *-firmware:183
          description: BIOS
          physical id: 2
          size: 1MiB
     *-firmware:184
          description: BIOS
          physical id: b5
          size: 1MiB
     *-firmware:185
          description: BIOS
          physical id: b6
          size: 1MiB
     *-firmware:186
          description: BIOS
          physical id: b7
          size: 1MiB
     *-firmware:187
          description: BIOS
          physical id: b8
          size: 1MiB
          capabilities: int13floppy720 int9keyboard int14serial
     *-firmware:188
          description: BIOS
          physical id: b9
          size: 1MiB
          capabilities: pcmcia upgrade shadowing
     *-firmware:189
          description: BIOS
          physical id: ba
          size: 1MiB
          capacity: 1600KiB
          capabilities: int13floppy2880 int5printscreen
     *-firmware:190
          description: BIOS
          physical id: bb
          size: 924KiB
          capabilities: pnp apm
     *-memory
          description: System memory
          physical id: bc
          size: 128MiB
     *-pci
          description: Host bridge
          product: VT82C598 [Apollo MVP3]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=16 module=via_agp
        *-pci
             description: PCI bridge
             product: VT82C598/694x [Apollo MVP3/Pro133x AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 3D Rage LT Pro AGP-133
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: dc
                width: 32 bits
                clock: 33MHz
                capabilities: agp agp-1.0 pm vga_controller bus_master cap_list
                configuration: latency=66 mingnt=8
        *-communication UNCLAIMED
             description: Serial controller
             product: HCF 56k Data/Fax Modem
             vendor: Rockwell International
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm 8250 cap_list
             configuration: latency=64
        *-multimedia
             description: Multimedia audio controller
             product: Vortex 1
             vendor: Aureal Semiconductor
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=au8820 latency=64 maxlatency=12 mingnt=2 module=snd_au8820
        *-firewire
             description: FireWire (IEEE 1394)
             product: FireWire Controller
             vendor: Texas Instruments
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=66 maxlatency=4 mingnt=3 module=ohci1394
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_via latency=66 module=pata_via
           *-disk:0
                description: ATA Disk
                product: IBM-DTTA-351350
                vendor: IBM
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: T5RC
                serial: WG2WGFA0224
                size: 12GiB (13GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00018e1a
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 59e47b12-bf12-4cfa-88ec-a5c7bf78dbee
                   size: 12GiB
                   capacity: 12GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-04-28 10:40:15 filesystem=ext3 modified=2008-05-18 08:29:34 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-05-04 08:44:06 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 352MiB
                   capacity: 352MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 352MiB
                      capabilities: nofs
           *-cdrom
                description: SCSI CD-ROM
                product: CRD-8322B
                vendor: COMPAQ
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: 1.06
                capabilities: removable audio
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
           *-disk:1
                description: SCSI Disk
                product: ZIP 100
                vendor: IOMEGA
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/sdb
                version: 12.A
                capabilities: removable
                configuration: ansiversion=5
              *-medium
                   physical id: 0
                   logical name: /dev/sdb
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=66 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=66 module=uhci_hcd
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: latency=0


```

---

### Post by jlbprof on 2008-05-18
After reading about lshw, we found the command lshw -enable isapnp

see:

[http://www.ducea.com/2006/06/03/use-lshw-hardware-lister-to-get-detailed-information-on-the-hardware-configuration-of-your-linux-system/]("http://www.ducea.com/2006/06/03/use-lshw-hardware-lister-to-get-detailed-information-on-the-hardware-configuration-of-your-linux-system/")

Anyway doing that the Kingston card shows up.  But I still do not know how to get it activated.

```

jules-linux
    description: Mini Tower Computer
    width: 32 bits
    capabilities: smbios-2.1 dmi-2.1
    configuration: chassis=mini-tower uuid=36393135-434D-585A-4130-343900000000
  *-core
       description: Motherboard
       physical id: 0
     *-firmware:0
          description: BIOS
          vendor: Compaq
          physical id: 0
          version: 686S5 (03/10/99)
          size: 64KiB
          capacity: 192KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot biosbootspecification netboot
     *-firmware:1
          description: BIOS
          physical id: 3
          version: None
          size: 1023KiB
          capabilities: apm bootselect socketedrom int13floppy360 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video
     *-firmware:2
          description: BIOS
          physical id: 802
          size: 1015KiB
          capabilities: eisa pcmcia pnp apm upgrade vesa escd bootselect pcmciaboot edd int13floppytoshiba int13floppy360 int14serial int17printer int10video
     *-cpu
          description: CPU
          product: AMD-K6(tm) 3D+ Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 5.9.1
          slot: U1
          size: 400MHz
          capacity: 600MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr cx8 pge mmx syscall 3dnow k6_mtrr up
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: CACHE1
             size: 64KiB
             capacity: 64KiB
             capabilities: internal varies
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: CACHE2
             size: 256KiB
             capacity: 256KiB
             capabilities: internal varies
     *-cache DISABLED
          description: L3 cache
          physical id: 7
          slot: CACHE3
          size: 1MiB
          capacity: 1MiB
          capabilities: external write-through
     *-firmware:3
          description: BIOS
          physical id: 5
          size: 1MiB
     *-firmware:4
          description: BIOS
          physical id: 6
          size: 1MiB
     *-firmware:5
          description: BIOS
          physical id: 8
          size: 1MiB
     *-firmware:6
          description: BIOS
          physical id: 9
          size: 1MiB
     *-firmware:7
          description: BIOS
          physical id: a
          size: 1MiB
     *-firmware:8
          description: BIOS
          physical id: b
          size: 1MiB
     *-firmware:9
          description: BIOS
          physical id: c
          size: 1MiB
     *-firmware:10
          description: BIOS
          physical id: d
          size: 1MiB
     *-firmware:11
          description: BIOS
          physical id: e
          size: 1MiB
     *-firmware:12
          description: BIOS
          physical id: f
          size: 1MiB
     *-firmware:13
          description: BIOS
          physical id: 10
          size: 1MiB
     *-firmware:14
          description: BIOS
          physical id: 11
          size: 1MiB
     *-firmware:15
          description: BIOS
          physical id: 12
          size: 1MiB
     *-firmware:16
          description: BIOS
          physical id: 13
          size: 1MiB
     *-firmware:17
          description: BIOS
          physical id: 14
          size: 1MiB
     *-firmware:18
          description: BIOS
          physical id: 15
          size: 1MiB
     *-firmware:19
          description: BIOS
          physical id: 16
          size: 1MiB
     *-firmware:20
          description: BIOS
          physical id: 17
          size: 1MiB
     *-firmware:21
          description: BIOS
          physical id: 18
          size: 1MiB
     *-firmware:22
          description: BIOS
          physical id: 19
          size: 1MiB
     *-firmware:23
          description: BIOS
          physical id: 1a
          size: 1MiB
     *-firmware:24
          description: BIOS
          physical id: 1b
          size: 1MiB
     *-firmware:25
          description: BIOS
          physical id: 1c
          size: 1MiB
     *-firmware:26
          description: BIOS
          physical id: 1d
          size: 1MiB
     *-firmware:27
          description: BIOS
          physical id: 1e
          size: 1MiB
     *-firmware:28
          description: BIOS
          physical id: 1f
          size: 1MiB
     *-firmware:29
          description: BIOS
          physical id: 20
          size: 1MiB
     *-firmware:30
          description: BIOS
          physical id: 21
          size: 1MiB
     *-firmware:31
          description: BIOS
          physical id: 22
          size: 1MiB
     *-firmware:32
          description: BIOS
          physical id: 23
          size: 1MiB
     *-firmware:33
          description: BIOS
          physical id: 24
          size: 1MiB
     *-firmware:34
          description: BIOS
          physical id: 25
          size: 1MiB
     *-firmware:35
          description: BIOS
          physical id: 26
          size: 1MiB
     *-firmware:36
          description: BIOS
          physical id: 27
          size: 1MiB
     *-firmware:37
          description: BIOS
          physical id: 28
          size: 1MiB
     *-firmware:38
          description: BIOS
          physical id: 29
          size: 1MiB
     *-firmware:39
          description: BIOS
          physical id: 2a
          size: 1MiB
     *-firmware:40
          description: BIOS
          physical id: 2b
          size: 1MiB
     *-firmware:41
          description: BIOS
          physical id: 2c
          size: 1MiB
     *-firmware:42
          description: BIOS
          physical id: 2d
          size: 1MiB
     *-firmware:43
          description: BIOS
          physical id: 2e
          size: 1MiB
     *-firmware:44
          description: BIOS
          physical id: 2f
          size: 1MiB
     *-firmware:45
          description: BIOS
          physical id: 30
          size: 1MiB
     *-firmware:46
          description: BIOS
          physical id: 31
          size: 1MiB
     *-firmware:47
          description: BIOS
          physical id: 32
          size: 1MiB
     *-firmware:48
          description: BIOS
          physical id: 33
          size: 1MiB
     *-firmware:49
          description: BIOS
          physical id: 34
          size: 1MiB
     *-firmware:50
          description: BIOS
          physical id: 35
          size: 1MiB
     *-firmware:51
          description: BIOS
          physical id: 36
          size: 1MiB
     *-firmware:52
          description: BIOS
          physical id: 37
          size: 1MiB
          capabilities: int5printscreen
     *-firmware:53
          description: BIOS
          physical id: 38
          size: 1MiB
          capabilities: apm
     *-firmware:54
          description: BIOS
          physical id: 39
          size: 1MiB
     *-firmware:55
          description: BIOS
          physical id: 3a
          size: 1008KiB
     *-firmware:56
          description: BIOS
          physical id: 3b
          size: 1MiB
     *-firmware:57
          description: BIOS
          physical id: 400
          size: 1MiB
     *-firmware:58
          description: BIOS
          physical id: 3c
          size: 1MiB
     *-firmware:59
          description: BIOS
          physical id: 3d
          size: 1MiB
     *-firmware:60
          description: BIOS
          physical id: 3e
          size: 1MiB
     *-firmware:61
          description: BIOS
          physical id: 3f
          size: 1MiB
     *-firmware:62
          description: BIOS
          physical id: 40
          size: 1MiB
     *-firmware:63
          description: BIOS
          physical id: 41
          size: 1MiB
     *-firmware:64
          description: BIOS
          physical id: 42
          size: 1MiB
     *-firmware:65
          description: BIOS
          physical id: 43
          size: 1MiB
          capabilities: bootselect
     *-firmware:66
          description: BIOS
          physical id: 44
          size: 1MiB
     *-firmware:67
          description: BIOS
          physical id: 45
          size: 1MiB
     *-firmware:68
          description: BIOS
          physical id: 46
          size: 1023KiB
     *-firmware:69
          description: BIOS
          physical id: 47
          size: 1MiB
     *-firmware:70
          description: BIOS
          physical id: 1
          size: 1MiB
     *-firmware:71
          description: BIOS
          physical id: 48
          size: 1MiB
     *-firmware:72
          description: BIOS
          physical id: 49
          size: 1MiB
     *-firmware:73
          description: BIOS
          physical id: 4a
          size: 1MiB
     *-firmware:74
          description: BIOS
          physical id: 4b
          size: 1MiB
     *-firmware:75
          description: BIOS
          physical id: 4c
          size: 1MiB
     *-firmware:76
          description: BIOS
          physical id: 4d
          size: 1MiB
     *-firmware:77
          description: BIOS
          physical id: 4e
          size: 1MiB
     *-firmware:78
          description: BIOS
          physical id: 4f
          size: 1MiB
     *-firmware:79
          description: BIOS
          physical id: 50
          size: 1MiB
     *-firmware:80
          description: BIOS
          physical id: 51
          size: 1MiB
     *-firmware:81
          description: BIOS
          physical id: 52
          size: 1MiB
     *-firmware:82
          description: BIOS
          physical id: 53
          size: 1MiB
     *-firmware:83
          description: BIOS
          physical id: 54
          size: 1MiB
     *-firmware:84
          description: BIOS
          physical id: 55
          size: 1MiB
     *-firmware:85
          description: BIOS
          physical id: 56
          size: 1MiB
     *-firmware:86
          description: BIOS
          physical id: 57
          size: 1MiB
     *-firmware:87
          description: BIOS
          physical id: 58
          size: 1MiB
     *-firmware:88
          description: BIOS
          physical id: 59
          size: 1MiB
     *-firmware:89
          description: BIOS
          physical id: 5a
          size: 1MiB
     *-firmware:90
          description: BIOS
          physical id: 5b
          size: 1MiB
     *-firmware:91
          description: BIOS
          physical id: 5c
          size: 1MiB
     *-firmware:92
          description: BIOS
          physical id: 5d
          size: 1MiB
     *-firmware:93
          description: BIOS
          physical id: 5e
          size: 1MiB
     *-firmware:94
          description: BIOS
          physical id: 5f
          size: 1MiB
     *-firmware:95
          description: BIOS
          physical id: 60
          size: 1MiB
     *-firmware:96
          description: BIOS
          physical id: 61
          size: 1MiB
     *-firmware:97
          description: BIOS
          physical id: 62
          size: 1MiB
     *-firmware:98
          description: BIOS
          physical id: 63
          size: 1MiB
     *-firmware:99
          description: BIOS
          physical id: 64
          size: 1MiB
     *-firmware:100
          description: BIOS
          physical id: 65
          size: 1MiB
     *-firmware:101
          description: BIOS
          physical id: 66
          size: 1MiB
     *-firmware:102
          description: BIOS
          physical id: 67
          size: 1MiB
     *-firmware:103
          description: BIOS
          physical id: 68
          size: 1MiB
     *-firmware:104
          description: BIOS
          physical id: 69
          size: 1MiB
     *-firmware:105
          description: BIOS
          physical id: 6a
          size: 1MiB
     *-firmware:106
          description: BIOS
          physical id: 6b
          size: 1MiB
     *-firmware:107
          description: BIOS
          physical id: 6c
          size: 1MiB
     *-firmware:108
          description: BIOS
          physical id: 6d
          size: 1MiB
     *-firmware:109
          description: BIOS
          physical id: 6e
          size: 1MiB
     *-firmware:110
          description: BIOS
          physical id: 6f
          size: 1MiB
     *-firmware:111
          description: BIOS
          physical id: 70
          size: 1MiB
     *-firmware:112
          description: BIOS
          physical id: 71
          size: 1MiB
     *-firmware:113
          description: BIOS
          physical id: 72
          size: 1MiB
          capabilities: int10video
     *-firmware:114
          description: BIOS
          physical id: 73
          size: 1MiB
          capabilities: escd
     *-firmware:115
          description: BIOS
          physical id: 74
          size: 1MiB
          capacity: 4MiB
     *-firmware:116
          description: BIOS
          physical id: 75
          size: 768KiB
     *-firmware:117
          description: BIOS
          physical id: 76
          size: 1MiB
     *-firmware:118
          description: BIOS
          physical id: 4000
          size: 1MiB
     *-firmware:119
          description: BIOS
          physical id: 77
          size: 1MiB
     *-firmware:120
          description: BIOS
          physical id: 78
          size: 1MiB
     *-firmware:121
          description: BIOS
          physical id: 79
          size: 1MiB
     *-firmware:122
          description: BIOS
          physical id: 7a
          size: 1MiB
     *-firmware:123
          description: BIOS
          physical id: 7b
          size: 1MiB
     *-firmware:124
          description: BIOS
          physical id: 7c
          size: 1MiB
     *-firmware:125
          description: BIOS
          physical id: 7d
          size: 1MiB
     *-firmware:126
          description: BIOS
          physical id: 7e
          size: 1MiB
     *-firmware:127
          description: BIOS
          physical id: 7f
          size: 1MiB
     *-firmware:128
          description: BIOS
          physical id: 80
          size: 1MiB
     *-firmware:129
          description: BIOS
          physical id: 81
          size: 1MiB
     *-firmware:130
          description: BIOS
          physical id: 82
          size: 1MiB
     *-firmware:131
          description: BIOS
          physical id: 83
          size: 1MiB
     *-firmware:132
          description: BIOS
          physical id: 84
          size: 1MiB
     *-firmware:133
          description: BIOS
          physical id: 85
          size: 1MiB
     *-firmware:134
          description: BIOS
          physical id: 86
          size: 1MiB
     *-firmware:135
          description: BIOS
          physical id: 87
          size: 1MiB
     *-firmware:136
          description: BIOS
          physical id: 88
          size: 1MiB
     *-firmware:137
          description: BIOS
          physical id: 89
          size: 1MiB
     *-firmware:138
          description: BIOS
          physical id: 8a
          size: 1MiB
     *-firmware:139
          description: BIOS
          physical id: 8b
          size: 1MiB
     *-firmware:140
          description: BIOS
          physical id: 8c
          size: 1MiB
     *-firmware:141
          description: BIOS
          physical id: 8d
          size: 1MiB
     *-firmware:142
          description: BIOS
          physical id: 8e
          size: 1MiB
     *-firmware:143
          description: BIOS
          physical id: 8f
          size: 1MiB
     *-firmware:144
          description: BIOS
          physical id: 90
          size: 1MiB
     *-firmware:145
          description: BIOS
          physical id: 91
          size: 1MiB
     *-firmware:146
          description: BIOS
          physical id: 92
          size: 1MiB
     *-firmware:147
          description: BIOS
          physical id: 93
          size: 1MiB
     *-firmware:148
          description: BIOS
          physical id: 94
          size: 1MiB
     *-firmware:149
          description: BIOS
          physical id: 95
          size: 1MiB
          capabilities: int13floppy2880 int5printscreen int14serial int17printer
     *-firmware:150
          description: BIOS
          physical id: 96
          size: 1MiB
          capabilities: pnp apm shadowing vesa bootselect edd int13floppynec int13floppytoshiba int13floppy720 int14serial int17printer
     *-firmware:151
          description: BIOS
          physical id: 97
          size: 1MiB
          capacity: 3456KiB
     *-firmware:152
          description: BIOS
          physical id: 98
          size: 808KiB
          capacity: 3136KiB
          capabilities: isa mca pcmcia pnp escd bootselect pcmciaboot edd int13floppy360 int9keyboard int14serial int10video
     *-firmware:153
          description: BIOS
          physical id: 99
          size: 827KiB
          capacity: 4288KiB
     *-firmware:154
          description: BIOS
          physical id: 3600
          size: 755KiB
          capacity: 5632KiB
     *-firmware:155
          description: BIOS
          physical id: 3139
          size: 670KiB
          capacity: 4160KiB
          capabilities: isa mca apm shadowing vesa bootselect edd int13floppynec int13floppytoshiba
     *-firmware:156
          description: BIOS
          physical id: 9a
          size: 1MiB
     *-firmware:157
          description: BIOS
          physical id: 9b
          size: 1MiB
     *-firmware:158
          description: BIOS
          physical id: 9c
          size: 1MiB
     *-firmware:159
          description: BIOS
          physical id: 9d
          size: 1MiB
     *-firmware:160
          description: BIOS
          physical id: 9e
          size: 1MiB
     *-firmware:161
          description: BIOS
          physical id: 9f
          size: 1MiB
     *-firmware:162
          description: BIOS
          physical id: a0
          size: 1MiB
     *-firmware:163
          description: BIOS
          physical id: a1
          size: 1MiB
     *-firmware:164
          description: BIOS
          physical id: a2
          size: 1MiB
     *-firmware:165
          description: BIOS
          physical id: a3
          size: 1MiB
     *-firmware:166
          description: BIOS
          physical id: a4
          size: 1MiB
     *-firmware:167
          description: BIOS
          physical id: a5
          size: 1MiB
     *-firmware:168
          description: BIOS
          physical id: a6
          size: 1MiB
     *-firmware:169
          description: BIOS
          physical id: a7
          size: 1MiB
     *-firmware:170
          description: BIOS
          physical id: a8
          size: 1MiB
     *-firmware:171
          description: BIOS
          physical id: a9
          size: 1MiB
     *-firmware:172
          description: BIOS
          physical id: aa
          size: 1MiB
     *-firmware:173
          description: BIOS
          physical id: ab
          size: 1MiB
     *-firmware:174
          description: BIOS
          physical id: ac
          size: 1MiB
     *-firmware:175
          description: BIOS
          physical id: ad
          size: 1MiB
     *-firmware:176
          description: BIOS
          physical id: ae
          size: 1MiB
     *-firmware:177
          description: BIOS
          physical id: af
          size: 1MiB
     *-firmware:178
          description: BIOS
          physical id: b0
          size: 1MiB
          capabilities: socketedrom
     *-firmware:179
          description: BIOS
          physical id: b1
          size: 1MiB
     *-firmware:180
          description: BIOS
          physical id: b2
          size: 1MiB
     *-firmware:181
          description: BIOS
          physical id: b3
          size: 1023KiB
     *-firmware:182
          description: BIOS
          physical id: b4
          size: 1MiB
     *-firmware:183
          description: BIOS
          physical id: 2
          size: 1MiB
     *-firmware:184
          description: BIOS
          physical id: b5
          size: 1MiB
     *-firmware:185
          description: BIOS
          physical id: b6
          size: 1MiB
     *-firmware:186
          description: BIOS
          physical id: b7
          size: 1MiB
     *-firmware:187
          description: BIOS
          physical id: b8
          size: 1MiB
          capabilities: int13floppy720 int9keyboard int14serial
     *-firmware:188
          description: BIOS
          physical id: b9
          size: 1MiB
          capabilities: pcmcia upgrade shadowing
     *-firmware:189
          description: BIOS
          physical id: ba
          size: 1MiB
          capacity: 1600KiB
          capabilities: int5printscreen
     *-firmware:190
          description: BIOS
          physical id: bb
          size: 924KiB
          capabilities: apm
     *-memory
          description: System memory
          physical id: bc
          size: 128MiB
     *-pci
          description: Host bridge
          product: VT82C598 [Apollo MVP3]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=16 module=via_agp
        *-pci
             description: PCI bridge
             product: VT82C598/694x [Apollo MVP3/Pro133x AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 3D Rage LT Pro AGP-133
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: dc
                width: 32 bits
                clock: 33MHz
                capabilities: agp agp-1.0 pm vga_controller bus_master cap_list
                configuration: latency=66 mingnt=8
        *-communication UNCLAIMED
             description: Serial controller
             product: HCF 56k Data/Fax Modem
             vendor: Rockwell International
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm 8250 cap_list
             configuration: latency=64
        *-multimedia
             description: Multimedia audio controller
             product: Vortex 1
             vendor: Aureal Semiconductor
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=au8820 latency=64 maxlatency=12 mingnt=2 module=snd_au8820
        *-firewire
             description: FireWire (IEEE 1394)
             product: FireWire Controller
             vendor: Texas Instruments
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=66 maxlatency=4 mingnt=3 module=ohci1394
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=parport_pc latency=0 module=parport_pc
           *-ktc2000 UNCLAIMED
                product: Kingston EtheRx KNE20 Plug and Play ISA Adapter
                physical id: 1
                bus info: isapnp@1
                version: 10
                serial: -262525810
                capabilities: pnp isapnp pnp-1.0
              *-rtl8019 UNCLAIMED
                   physical id: 0
                   capabilities: pnp80d6-compatible
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_via latency=66 module=pata_via
           *-disk:0
                description: ATA Disk
                product: IBM-DTTA-351350
                vendor: IBM
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: T5RC
                serial: WG2WGFA0224
                size: 12GiB (13GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00018e1a
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 59e47b12-bf12-4cfa-88ec-a5c7bf78dbee
                   size: 12GiB
                   capacity: 12GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-04-28 10:40:15 filesystem=ext3 modified=2008-05-18 08:29:34 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-05-04 08:44:06 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 352MiB
                   capacity: 352MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 352MiB
                      capabilities: nofs
           *-cdrom
                description: SCSI CD-ROM
                product: CRD-8322B
                vendor: COMPAQ
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: 1.06
                capabilities: removable audio
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
           *-disk:1
                description: SCSI Disk
                product: ZIP 100
                vendor: IOMEGA
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/sdb
                version: 12.A
                capabilities: removable
                configuration: ansiversion=5
              *-medium
                   physical id: 0
                   logical name: /dev/sdb
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=66 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=66 module=uhci_hcd
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: latency=0

```

---

### Post by Pumalite on 2008-05-18
Go to Network Tools and configure it. (or Network?)

---

### Post by jlbprof on 2008-05-18
Is there a command line network tools?

The problem is it does not have much memory and so the normal desktop installer just hung.  We then downloaded the server cd and it installs fine, but no network card and is pretty much useless without network.

Thanx

Bodger

---

### Post by galileon on 2008-05-19
[http://linux.derkeiler.com/Newsgroups/comp.os.linux.embedded/2004-03/0162.html](http://linux.derkeiler.com/Newsgroups/comp.os.linux.embedded/2004-03/0162.html)

dunno if this might help you or someone else to help you...i had a quick read thru it, and it mentions pnp support in the kernel, which I guess  Ubuntu has...any ideas anyone?

---

