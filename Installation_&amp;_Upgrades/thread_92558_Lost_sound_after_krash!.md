---
title: "Lost sound after krash!"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by xip on 2005-11-19
Hi all, first post, not shure this is the right thread, but i hope it will do :)

sorry for my bad english, my home language is crapy cus of dyslexia, so a secondary language tends to get messy, pleas bear with me.

I had a fiew hard rebots after some problems with my pc not booting from cd(aperently its broken now) ... anyway.... it dosent mather, but when i finnaly started up ubunti again, the speaker whas gone from "system tray?" (i am an hardcore windows user, and a real noob at linux), evry media application i tryed complained on problems with sound, after some messing around i asked my friend to remotly try to work it out(he knows alot more than me about linux) ... after a while he found out that ALL files/directorys for sound files was gone ... but he did not know how to solve it.

/dev/dsp
/dev/sound
/dev/sound0

is all gone.

i cant work like this, and i Realy REALY need to get things working again, so if anyone with some skills whod explain in a linux-noob-friendly way how i can solve this, i whod be a very happy boy ;)

like i wrote alredy, i suck hard on linux, and evry thing around it, but i think i have a SIS(Silicon Integreated systems) (that i gues is the one since i have an integreated sound card) into my mainboard.

we have tryed search for drivers and SIS key words with synoptic and google, but i dont found what i need.

anyone ho can help me find what i need, and explain how i can install/restore(?) it? i have only used synoptic for installing stuff on linux before.

im very happy for any help anyone can give me:)
tanx

/Xip

---

### Post by xip on 2005-11-21
if this can help anyone:
------------------------------------------------


pingu
    description: Computer
    capabilities: smbios-2.2 dmi-2.2
  *-core
       description: Motherboard
       product: SiS-745
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG (11/25/2002)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 1500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          version: 6.8.1
          slot: Socket A
          size: 1300MHz
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse pni syscall mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 256KB
             capacity: 256KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1f
          slot: System board or motherboard
          size: 768MB
          capacity: 1536MB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 256MB
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
        *-bank:2
             description: DIMM
             physical id: 2
             slot: A2
             size: 512MB
     *-pci
          physical id: e0000000
          bus info: pci@00:00.0
          version: 01
          clock: 33MHz
        *-pci
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             clock: 33MHz
             capabilities: pci bus_master
           *-display:0 UNCLAIMED
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 256MB
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: irq=5
           *-display:1 UNCLAIMED
                physical id: 0.1
                bus info: pci@01:00.1
                version: 00
                size: 256MB
                clock: 66MHz
                capabilities: bus_master cap_list
        *-isa UNCLAIMED
             physical id: 2
             bus info: pci@00:02.0
             version: 00
             clock: 33MHz
             capabilities: isa bus_master
        *-serial
             physical id: 2.1
             bus info: pci@00:02.1
             version: 00
             clock: 33MHz
             configuration: driver=sis96x_smbus
        *-usb:0
             physical id: 2.2
             bus info: pci@00:02.2
             version: 07
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd irq=11
        *-usb:1
             physical id: 2.3
             bus info: pci@00:02.3
             version: 07
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd irq=11
        *-ide
             physical id: 2.5
             bus info: pci@00:02.5
             version: d0
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=SIS_IDE
        *-network
             physical id: d
             bus info: pci@00:0d.0
             version: 10
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=8139too irq=11
  *-scsi
       physical id: 1
       bus info: scsi@0
       logical name: scsi0
       configuration: driver=usb-storage
  *-network:0
       description: Ethernet controller
       physical id: 2
       logical name: eth0
       serial: 00:50:22:c8:06:8a
       capabilities: mii autonegotiation 100bt-fd 100bt 10bt-fd 10bt ethernet
       configuration: autonegociated=100bt broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=217.210.6.47 link=yes multicast=yes
  *-network:1 DISABLED
       description: controller
       physical id: 3
       logical name: sit0

---

