---
title: "Live CD doesn't detect hard drives"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by renegade1029 on 2008-05-17
I've got an old machine here that I'd like to salvage using Xubuntu. It's a PIII 500 MHz with 384 MB RAM with two SCSI hard drives. 

First drive : Maxtor 6 Y060L0 SCSI (60 GB), with two FAT32 partitions (15 GB and 43 GB)
Second drive : Quantum Fireball 20 GB SCSI, unpartionned, FAT32

The computer is currently running Windows XP, which detects all drives/partitions without problem.

I downloaded and burned the Xubuntu Live CD, which my computer runs without any problems.

When I start the installation process, I can select my language and time zone without any problem. When I get to the partitionner, the list of devices is empty. I ran Gparted on the Live CD, same problem. GParted doesn't detect my hard drives.

Any hints? Don't hesitate to ask me more info if you need it. Thanks in advance.

---

### Post by Pumalite on 2008-05-17
Post:
lshw

---

### Post by renegade1029 on 2008-05-17
Here are the results :

```

ubuntu@ubuntu:~$ sudo lshw
ubuntu                    
    description: Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
  *-core
       description: Motherboard
       product: i440BX-W83977 (BE6)
       vendor: <http://www.abit.com.tw>
       physical id: 0
       slot: PCI
     *-firmware
          description: BIOS
          physical id: 0
          version: Award Software International, Inc. (07/05/2000)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: Pentium III (Katmai)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.3
          slot: SLOT 1
          size: 500MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back
     *-memory
          description: System memory
          physical id: 1
          size: 384MiB
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel latency=32 module=intel_agp
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Rage 128 RL/VR AGP
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=32 mingnt=8
        *-isa
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=32 module=ata_piix
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM DVD-114
                vendor: PIONEER
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: 1.10
                capabilities: removable audio dvd
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted
           *-cdrom:1
                description: DVD writer
                product: DVD RW DRU-510A
                vendor: SONY
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.0c
                serial: [SONY    DVD RW DRU-510A 1.0c Aug06 ,2003
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-network
             description: Ethernet interface
             product: RTL-8029(AS)
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: eth0
             version: 00
             serial: 00:e0:29:3a:01:b3
             width: 32 bits
             clock: 33MHz
             capabilities: ethernet physical
             configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 latency=0 module=ne2k_pci multicast=yes
        *-multimedia
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: d
             bus info: pci@0000:00:0d.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
        *-input
             description: Input device controller
             product: SB Live! Game Port
             vendor: Creative Labs
             physical id: d.1
             bus info: pci@0000:00:0d.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Emu10k1_gameport latency=32 module=emu10k1_gp
        *-storage:0
             description: Mass storage controller
             product: HPT366/368/370/370A/372/372N
             vendor: HighPoint Technologies, Inc.
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: storage bus_master
             configuration: driver=HPT366_IDE latency=120 maxlatency=8 mingnt=8 module=hpt366
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: Maxtor 6Y060L0
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 57GiB (61GB)
        *-storage:1
             description: Mass storage controller
             product: HPT366/368/370/370A/372/372N
             vendor: HighPoint Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: storage bus_master
             configuration: latency=120 maxlatency=8 mingnt=8
           *-ide
                description: IDE Channel 0
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-disk
                   product: QUANTUM FIREBALLP KX20.5
                   vendor: Quantum
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 19GiB (20GB)

```

---

### Post by Pumalite on 2008-05-17
This is the only problem I encounter:
'*-display UNCLAIMED
                description: VGA compatible controller
                product: Rage 128 RL/VR AGP
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=32 mingnt=8'

Try Gparted Live CD and check if it sees your drives:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.

---

### Post by renegade1029 on 2008-05-17
Same problem, GParted Live CD says "No devices detected" in its status bar. I tried refreshing (Ctrl+R) to no effect.

---

### Post by Pumalite on 2008-05-17
Does your BIOS recognize the drives? Are they well configured? Try different options. If none of that works; go and revciew connections and cables. As a last option: TestDisk:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by renegade1029 on 2008-05-17
Well since Windows XP runs without problem I think my BIOS detects them correctly.

I'll try to erase the partitions on the first disk or physically remove one of the disks.

---

### Post by Pumalite on 2008-05-17
Check IDE Configuration in BIOS. Sometimes Windows works with one, but Ubuntu or Linux needs a different one.

---

### Post by renegade1029 on 2008-05-17
I'm not too familiar with BIOS and everything that happens before the OS is loaded, but I seem to have a strange thing installed on this computer. It seems to be some sort of memory controller, called HPT366. From a (very) quick Google search, I found out there seems to be problems with this thing. Could this cause my problem? And if so, is there a way to uninstall this HPT366?

EDIT : Also, when I boot the Live CD, I have a FAIL at "Detecting Hardware configuration" (or something along those lines, I didn't have time to take note). WOuld it be my video card like you detected or is it my hard drives?

---

### Post by Pumalite on 2008-05-17
Try the Alternate CD. Usually avoids hardware and/or video problems.

---

### Post by renegade1029 on 2008-05-18
Thanks a lot for your help, I've got Xubuntu up and running. I physically removed the 20 GB hard drive and was able to install Xubuntu and run it. I then tried to replug the 20 GB HD, but Xubuntu refused to boot. So I guess this was a bard hard drive...

Time to get the magnets out of this one :P

---

### Post by Pumalite on 2008-05-18
You are welcome. Good luck.

---

