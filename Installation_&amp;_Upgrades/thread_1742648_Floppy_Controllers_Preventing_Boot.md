---
title: "Floppy Controllers Preventing Boot"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by freeze10108 on 2011-04-29
I tried installing Natty today, but, after installation, it won't boot.  I make it, once I've added a verbose parameter to the boot commands, to:

```
floppy0:  no floppy controllers found
```

I made [a thread]("http://ubuntuforums.org/showthread.php?t=1592859") about this when Maverick came out because the same thing happened, but nothing came from it.

Does anyone know how to remedy this or, perhaps, stop Ubuntu from even looking for the floppy on boot?

---

### Post by dino99 on 2011-04-29
is floppy disabled into bios ?

if you are really using grub2, you should not have this kind of issue:

into /boot/grub/grub.cfg this line tell to boot without checking floppy: "search --no-floppy --fs-uuid --set=root your_uuid"

so i wonder if you use grub2 or if you still have the old grub legacy & menu.lst (they have to be removed then run update-grub)

---

### Post by freeze10108 on 2011-04-29
> **dino99 said:**
> is floppy disabled into bios ?

I'm fairly certain it's disabled.  I've gone through the whole menu and can't find anything about it except disabling booting from it (which I did) and changing its position in the boot order.

> if you are really using grub2, you should not have this kind of issue:

I should be using grub2.  Whatever grub version is installed with Ubuntu is the one on the computer.

> into /boot/grub/grub.cfg this line tell to boot without checking floppy: "search --no-floppy --fs-uuid --set=root your_uuid"

That line's already there.  Is there anything else I need to do to tell it to boot without checking for the floppy?

> so i wonder if you use grub2 or if you still have the old grub legacy & menu.lst (they have to be removed then run update-grub)

I searched the hard drive and couldn't find any menu.lst files, so it should be completely grub2.

Maybe it has something to do with the kernels that Ubuntu uses?  I can boot Fedora just fine, but Ubuntu hangs (though 10.04 didn't).

---

### Post by freeze10108 on 2011-04-30
Okay, I just reinstalled Natty with my laptop hooked up to the Internet so that I could download the updates.  It wouldn't boot a couple times in a row, then it did once and I ran a further update as well as installed the "highly experimental" (Nouveau, right?) 3D drivers, but, after restarting, it won't boot again.  :(

---

### Post by freeze10108 on 2011-04-30
Does anyone have any idea what I need to edit to get Ubuntu to boot up?  Maybe I need to blacklist something?

PS, are the forums usually so busy that threads fall back to the tenth page after a few hours?

---

### Post by freeze10108 on 2011-05-01
So, I've tried adding "blacklist floppy" to /etc/modprobe.d/blacklist, "alias floppy off" to /etc/modules, disabling boot from floppy in BIOS, and moving the floppy down as far as possible.  Nothing has worked yet. :(  Any advice?

---

### Post by edgardol on 2011-05-30
I'm experiencing a very similar problem.
freeze10108: Did you find a solution ?

In my case, I tried installing Ubuntu 11.04 and also Edubuntu 11.04, on a home made desktop, and on an old Compaq R3000 laptop.
I got the black screen at boot on both computers with both disks, so I powered off, powered on, at the grub menu I selected: recovery mode (2nd in the list), and click Enter.
It always stops at: floppy0: no controllers found.
I tried hitting: e, when the grub menu shows up, and I confirmed the presence of the option: search --no-floppy ...
I also tried deleting --no-floppy from that line.

Any suggestion is welcome !
Otherwise, I may go back to 10.04

Thanks in advance,
Edgardo.

---

### Post by freeze10108 on 2011-05-30
^No, I haven't found a solution yet.  I've created a question in LaunchPad and on LinuxQuestions and neither has produced a solution yet.  Someone on LaunchPad however did say that the problem isn't with the floppy because the floppy message is just a warning, so there must be something else.

Just out of curiosity, what kind of computer are you using (style, make, and model)?

---

### Post by edgardol on 2011-05-30
The laptop is a Compaq Presario R3000, part number: DP533AV, with an AMD Athlon 64 2200 MHz processor and 512 MB RAM, 80GB HDD, 15.4-inch WXGA display 1920x1600, the video card is NVIDIA but I don't remember the model. It has a Phoenix BIOS version F.12. It also has a bunch of ports: PCMCIA, USB, memory card readers, sound, Firewire, and WiFi (B version).

---

### Post by freeze10108 on 2011-05-30
Would you be able to run
```
lshw > hardwareinfo.txt
```
on either another Linux partition or from the LiveCD (both may require installing lshw) and copying and pasting the the results in the text file into [ code ] [ /code ] tags (minus the spaces) here?  That way, I can look at the two and see if there's a common piece of hardware between the two that could be causing the problem.

---

### Post by edgardol on 2011-05-30
I was able to run lshw from a terminal window, by booting with the "try" option of 10.04.
(I also tried with 11.04 first, but it got stacked before even starting.)

The output of lshw is attached. I'm not sure how to use the "CODE" tags, but I'm trying below:

```
ubuntu
    description: Notebook
    product: Presario R3200 (DP533AV)
    vendor: Hewlett-Packard
    version: F.12
    serial: CND4280CFP
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=oem-specific chassis=notebook uuid=B570FE79-C7A6-11D8-BA5A-000FB003B1CA
  *-core
       description: Motherboard
       product: 08A0
       vendor: Compal
       physical id: 0
       version: 32.22
       serial: CND4280CFP
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.12 (06/08/2004)
          size: 114KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.4.10
          slot: Socket A
          size: 800MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 1MiB
             capabilities: synchronous internal write-through unified
     *-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: S1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
             slot: S2
     *-pci:0
          description: Host bridge
          product: nForce3 Host Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a4
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-amd64
          resources: irq:0 memory:e8000000-efffffff(prefetchable)
        *-isa
             description: ISA bridge
             product: nForce3 LPC Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a6
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce3 SMBus
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
             resources: irq:10 ioport:2040(size=64) ioport:2000(size=64)
        *-usb:0
             description: USB Controller
             product: nForce3 USB 1.1
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a5
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:e0000000-e0000fff
        *-usb:1
             description: USB Controller
             product: nForce3 USB 1.1
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a5
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:e0001000-e0001fff
        *-usb:2
             description: USB Controller
             product: nForce3 USB 2.0
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:e0004000-e00040ff
        *-multimedia
             description: Multimedia audio controller
             product: nForce3 Audio
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
             resources: irq:21 ioport:1400(size=256) ioport:1c00(size=128) memory:e0002000-e0002fff
        *-communication UNCLAIMED
             description: Modem
             product: nForce3 Audio
             vendor: nVidia Corporation
             physical id: 6.1
             bus info: pci@0000:00:06.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: latency=0 maxlatency=5 mingnt=2
             resources: ioport:1800(size=256) ioport:1c80(size=128) memory:e0003000-e0003fff
        *-ide
             description: IDE interface
             product: nForce3 IDE
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             logical name: scsi0
             logical name: scsi1
             version: a5
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:2080(size=16)
           *-disk
                description: ATA Disk
                product: FUJITSU MHT2080A
                vendor: Fujitsu
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0022
                serial: NN4FT4613G4R
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000cdb17
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: d168a8af-e8e0-4e9c-82d9-9cf39eaab77b
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-05-28 22:29:54 filesystem=ext4 lastmountpoint=/aï¿œ)-ï¿œï¿œï¿œï¿œHxï¿œï¿œ<^ï¿œï¿œïï¿œï¿œQï¿œHxï¿œÝ&#128;Gï¿œï¿œ6ï¿œï¿œïï¿œï¿œ^ï¿œï¿œ6ï¿œï¿œïï¿œï¿œï¿œï¿œï¿œ\^ï¿œï¿œNeï¿œ@ï¿œ modified=2011-05-28 23:54:13 mounted=2011-05-30 23:35:12 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 509MiB
                   capacity: 509MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 509MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: DVD-ROM GDR8082N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: 0C11
                capabilities: removable audio dvd
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
        *-pci:0
             description: PCI bridge
             product: nForce3 PCI Bridge
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:3000(size=20480) memory:e0100000-e17fffff memory:20000000-27ffffff(prefetchable)
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:19 memory:e0108000-e01087ff memory:e0100000-e0103fff
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 10
                serial: 00:0f:b0:03:b1:ca
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.88 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: irq:18 ioport:7000(size=256) memory:e0108800-e01088ff
           *-network:1
                description: Network controller
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64
                resources: irq:17 memory:e0104000-e0105fff
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1620 PC Card Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:19 memory:e0106000-e0106fff ioport:3000(size=256) ioport:3400(size=256) memory:20000000-23ffffff(prefetchable) memory:e0400000-e07fffff
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1620 PC Card Controller
                vendor: Texas Instruments
                physical id: 4.1
                bus info: pci@0000:02:04.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:18 memory:e0107000-e0107fff ioport:3800(size=256) ioport:3c00(size=256) memory:24000000-27ffffff(prefetchable) memory:e0c00000-e0ffffff
           *-generic UNCLAIMED
                description: System peripheral
                product: PCI1620 Firmware Loading Function
                vendor: Texas Instruments
                physical id: 4.2
                bus info: pci@0000:02:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=7
                resources: ioport:7400(size=64)
        *-pci:1
             description: PCI bridge
             product: nForce3 AGP Bridge
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: memory:e2000000-e2ffffff memory:f0000000-f80fffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: NV17 [GeForce4 440 Go 64M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a3
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master cap_list rom
                configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
                resources: irq:16 memory:e2000000-e2ffffff memory:f0000000-f7ffffff(prefetchable) memory:f8000000-f807ffff(prefetchable) memory:f8080000-f809ffff(prefetchable)
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
          configuration: driver=k8temp
          resources: irq:0
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:5b:67:b2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by freeze10108 on 2011-05-31
We have somewhat similar laptops, though I'm not surprised because they're both HPs.  I didn't really get this from reading through the reports, but it did occur to me when doing so.

If there's a GRUB menu when you boot up, press "e" on the line with Ubuntu on it.  Then add "vesa" to the parameters (I add it after "splash").  Finally, press "Ctrl+X" and see if it boots.  I just did it and I'm using Ubuntu to type this post, but I'm not sure if it's a fluke or not.

If there's no GRUB menu (the computer automatically tries booting into Ubuntu), hold "Shift" as you boot up the computer and the GRUB menu should come up.  Then proceed as in above (from pressing "e").

If it does boot, don't install any additional hardware drivers if Ubuntu prompts you (I did and can't boot again).  Please reboot and see if it works again by adding "vesa" to the parameters again.

BTW, good job on using the CODE tags!  :)

---

### Post by edgardol on 2011-05-31
vesa option didn't help with my machine.
I tried twice, once selecting the regular (1st) boot option on the grub menu, then typing: e, adding: vesa (after: splash), and ctrl-x to reboot. I only get a black screen. This is probably a different problem that I'll have to deal with after getting pass the floppy problem.
The second time, in the grub menu, I scrolled down to the recovery option (2nd), and then hit: e. In this case, the linux line doesn't say: splash, but I still added: vesa, at the end of the linux line. Then I hit ctrl-x. It got stacked again at: floppy0: no floppy controllers found. :(

Thanks,
Edgardo.

---

### Post by psusi on 2011-05-31
Can you post more of the kernel output leading up to that?  Even if it can't find the floppy it should continue to boot after that error.  In the BIOS there should be a screen where you tell it what KIND of floppy you have ( 1.44 MB, 720k, etc ).  It needs to be set to NONE.

---

### Post by edgardol on 2011-06-05
Hi psusi,

In the BIOS there isn't any screen telling what kind of floppy I have. The machine is a laptop and does not have any floppy. There are two screens mentioning "floppy". One is the boot order, where floppy is at the bottom after other three items, and where I tried leaving it alone and also disabling it. The second is the Device security screen, where it lists "Floppy Boot" and "CD-ROM boot", with options Enabled or Disabled. I tried both for floppy.

It does not continue to boot after the floppy line. These are the outputs leading to that floppy line:
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
[   2.784161] firewire_core: created device fw0: GUID 463f0200463f0200, S400
[   4.904048] floppy0: no floppy controllers found

---

### Post by psusi on 2011-06-06
Either you are missing the option or you have a broken bios that does not have the floppy setup option, but goes ahead and tells the OS you have one anyway even though you don't.  That still shouldn't prevent you from booting.

---

