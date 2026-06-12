---
title: "remove / undo trial installation of 12.04"
date: 2014-03-24
forum: Installation &amp; Upgrades
---

### Post by jan-bol on 2014-03-24
Hello guys!

I tried to install 12.04 but I run into problems with Nvidia driver and a dual screen set up. 

I had the same problem a year ago. That time I was not able to fix it and I hoped that the problem was solved by now. 

Now I might be able to resolve this issue, there is a lot of new info available, but the first attempts of installing new drivers were not succesful

Point is: I want to undo the trial installation of 12.04 and sort out as I currently don't have the time to fiddle around with drivers (may be it takes only an hour, but it also might take two days or more and I can't afford spending so much time on it right now)

Okay, I admit, may be I shouldn't have attempted this installation right now :p but here I am: trying to get my old 10.04 back.

So my question:

How do I remove the trial installation ? (I opted for the L/H option in below screen)

I tried already with the cd removed from the tray but then I get a prompt (before any ubuntu screen comes on) asking for user name and password. Now I dont remember my username (Silly may be, but i remember only my password). So i logged in as root. But then i only get a prompt that says i'm logged in as root, but still no Ubuntu screen.

I checked google and the search option in this forum but i couldn't find a thread.

Any help would be highly appreciated!!!!
[IMG]http://www.google.nl/url?sa=i&rct=j&q=&esrc=s&source=images&cd=&cad=rja&uact=8&docid=StOqLqdYb6spDM&tbnid=_txLVzp3dgj49M:&ved=0CAYQjRw&url=http%3A%2F%2Fwww.ubuntu.com%2Fdownload%2Fdesktop%2Ftry-ubuntu-before-you-install&ei=WZwwU7LsOKWK0AWOmIC4Cw&bvm=bv.62922401,d.d2k&psig=AFQjCNHWLVtqwTAKk55mHO5U5kj70B3aFg&ust=1395781077549660[/IMG]

---

### Post by jan-bol on 2014-03-24
I noticed that the image of the screen did not come along with the post. Anyway, it is the Try Ubuntu option I'm talking about

---

### Post by mörgæs on 2014-03-25
Please begin with a complete hardware description. Run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---

### Post by jan-bol on 2014-03-25
Okay Mörgæs, bellow I added the lshw.txt.

IMHO I thought I could undo the installation when I boot without the cd. As I mentioned that doesn' t work as I get asked for username/password. While installing 12.04 I got a messages asking if i wanted to replace old system files in which case i would loose changes that I made to those files. I made educated guesses as to which files to replace or  not. Could this cause the system not to boot without the CD?

```
computer
    description: Desktop Computer
    product: MS-7318 ()
    vendor: MEDIONPC
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=desktop uuid=[REMOVED]
  *-core
       description: Motherboard
       product: MS-7318
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG
          date: 02/02/2007
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2
          slot: Socket 775
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 266MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow cpufreq
        *-cache
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
     *-cache
          description: L1 cache
          physical id: 9
          slot: Internal Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: [REMOVED]
             slot: A0
             size: 2GiB
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: [REMOVED]
             slot: A1
             size: 1GiB
     *-pci:0
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:d0000000-d7ffffff
        *-generic UNCLAIMED
             description: PIC
             product: P4M890 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: io_x_-apic bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: ioport:b000(size=4096) memory:dfd00000-dfdfffff memory:dfc00000-dfcfffff
        *-pci:1
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:64 ioport:a000(size=4096) memory:dc000000-deffffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G73 [GeForce 7650 GS]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:24 memory:dc000000-dcffffff memory:c0000000-cfffffff memory:dd000000-ddffffff ioport:ac00(size=128) memory:de000000-de01ffff
        *-pci:2
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:65 ioport:c000(size=4096) memory:dfb00000-dfbfffff ioport:dfe00000(size=1048576)
        *-ide:0
             description: IDE interface
             product: VT8251 Serial ATA Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_via latency=32
             resources: irq:21 ioport:fc00(size=8) ioport:f800(size=4) ioport:f400(size=8) ioport:f000(size=4) ioport:ec00(size=16) memory:dffff000-dffff3ff
           *-disk
                description: ATA Disk
                product: ST3320820AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sdd
                version: 3.AA
                serial: [REMOVED]
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000c0350
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sdd1
                   version: 1.0
                   serial: [REMOVED]
                   size: 289GiB
                   capacity: 289GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2012-08-01 10:06:32 filesystem=ext4 lastmountpoint=/ modified=2014-03-24 20:10:20 mounted=2014-03-25 12:18:31 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sdd2
                   size: 8840MiB
                   capacity: 8840MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdd5
                      capacity: 8840MiB
                      capabilities: nofs
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi2
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e800(size=16)
           *-cdrom:0
                description: DVD-RAM writer
                product: DVDRAM GSA-H42L
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                logical name: /cdrom
                version: SL00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   capabilities: partitioned partitioned:dos
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=67c8e78a state=mounted
                 *-volume UNCLAIMED
                      description: Hidden HPFS/NTFS partition
                      physical id: 1
                      capacity: 698MiB
                      capabilities: primary bootable hidden
           *-cdrom:1
                description: DVD reader
                product: DVD-ROM GDR8164B
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@2:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/sr1
                version: 0U08
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 91
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:20 ioport:e400(size=32)
        *-usb:1
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 91
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:22 ioport:e000(size=32)
        *-usb:2
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 91
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:dc00(size=32)
        *-usb:3
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 91
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:23 ioport:d800(size=32)
        *-usb:4
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:22 memory:dfffe000-dfffe0ff
        *-isa
             description: ISA bridge
             product: VT8251 PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: [REMOVED]
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
             resources: irq:23 ioport:d400(size=256) memory:dfffd000-dfffd0ff
        *-pci:3
             description: PCI bridge
             product: VT8251 Host Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht normal_decode bus_master
             resources: ioport:8000(size=8192) memory:df800000-dfafffff ioport:df600000(size=2097152)
           *-pci:0
                description: PCI bridge
                product: VT8251 PCIE Root Port
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: iomemory:90900-908ff irq:66 ioport:9000(size=4096) memory:df800000-df8fffff memory:df700000-df7fffff
           *-pci:1
                description: PCI bridge
                product: VT8251 PCIE Root Port
                vendor: VIA Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:04:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: iomemory:80800-807ff irq:67 ioport:8000(size=4096) memory:df900000-df9fffff memory:df600000-df6fffff
           *-multimedia
                description: Audio device
                product: VT8237A/VT8251 HDA Controller
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:04:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:68 memory:dfafc000-dfafffff
        *-pci:4
             description: PCI bridge
             product: VT8251 PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht subtractive_decode bus_master
             resources: ioport:7000(size=4096) memory:df500000-df5fffff ioport:df400000(size=1048576)
           *-multimedia
                description: Multimedia controller
                product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
                vendor: Philips Semiconductors
                physical id: 9
                bus info: pci@0000:07:09.0
                version: d1
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=saa7134 latency=32 maxlatency=32 mingnt=84
                resources: irq:16 memory:df5ff000-df5ff7ff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: c
                bus info: pci@0000:07:0c.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=32
                resources: irq:19 memory:df5fe000-df5fe7ff ioport:7c00(size=128)
     *-pci:1
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: P4M890 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8237/8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-scsi
          physical id: 1
          bus info: usb@1:1.1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: Flash HS-CF
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: 4.44
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sda
        *-disk:1
             description: SCSI Disk
             product: Flash HS-MS/SD
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdb
             version: 4.44
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
        *-disk:2
             description: SCSI Disk
             product: Flash HS-SM
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdc
             version: 4.44
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1.2
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.2.0-23-generic firmware=1.7 ip=[REMOVED] link=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by mörgæs on 2014-03-25
The hardware is strong and can run any of the 13.10 releases. 10.04 is out of support and should be forgotten.

You simply boot a live system or the system on the hard disk. Insert an empty USB stick and copy all the stuff you want to save.

When all your important files are safe you create a bootable USB with L/X/K/Ubuntu 13.10 of your choice. Choose install and replace, and the hard disk will be wiped in the process. You don't have to remove the old system manually.

---

### Post by jan-bol on 2014-03-25
I already transferred the important data and as a quick fix i am now working on a laptop.

So yes, I could go along with your suggestion and do fresh installation of 13.10 / 12.04 LTS 

BUT.... I am not sure if i can get my set up working which is:

Dual monitor (Eizo Flexscan L887 & Proline E 1900 S)
Nvidia Geforce 7650 GS

As mentioned I tried this about 1 1/2 yr ago but I could not find a driver that allowed dual monitor and specified graphic card set up to run on 12.04. I spent an awful lot of time back then.

I know i can get the set up working with 10.04, but as you state correctly -> no longer supported. (But its better to have a system that is not supported than to have a system that is not running.)

So may be I am able to solve this driver issue this time, may be not (yet). So in the worst case I might be forced to go back to 10.04 till I find a solution. In that case I would like to go back to my old 10.04 installation because that saves tonnes of time of configuring everything again.

So that's why I ask: can I still go back to my old 10.04 installation?    

At this moment i have choosen the "try ubuntu" ubuntu option. To me "try" means that you can go back to the old situation if you want. I only don't know how.

---

### Post by grahammechanical on 2014-03-25
What you want to do is called "Re-installing." And no, you are wrong about the meaning of "Try Ubuntu." Since before Ubuntu 10.04 was even dreamed of "Try Ubuntu" meant run a Ubuntu session from the CD drive and do not start the installation of Ubuntu on to the hard disk until the user gives a specific instruction to install to the hard disk.

I understood that this was the meaning when I first put a Ubuntu CD into my optical drive back in April 2007. It is still the meaning. With the "Try Ubuntu" session we get back to the old situation by exiting the session by shutting down Ubuntu  from a menu. Our machine would then be in exactly the same state as when we put the ubuntu CD/DVD into the optical drive. No changes made to the hard disk or hardware.

---

### Post by jan-bol on 2014-03-25
Okay Graham, thanks for your info

I assume you mean: "And no, you are not wrong". At least that would be in line with the rest of your answer.

So if I understand you correctly, if I shut down the trial installation from a menu, I should go back to the old installation? I tried shutting down from the panel (R/H top) but that doesn't work. So do you mean a different menu?

---

### Post by mörgæs on 2014-03-26
> **jan-bol said:**
> 

As mentioned I tried this about 1 1/2 yr ago but I could not find a driver that allowed dual monitor and specified graphic card set up to run on 12.04. I spent an awful lot of time back then.


If you check the 'restricted drivers' (or something like that) box during installation all available closed-source drivers will be installed automatically.

---

### Post by jan-bol on 2014-05-19
Hi Guys

First thanks for all the support on this issue.

I left the issue for a while but as my laptop has a hd problems i was forced to get my desktop up and running again.

To summarise my findings:

- I installed 14.04 lts
- It resulted in a black/white square checker kind of thing screen
- I could only start normally through the ubuntu recovery mode after repair packages (sorry forgot the exact menu title)
- After that I got one time a warning saying that something was wrong with X... Couldn't exactly trace it
- Rebooting resulted in endless booting. The screen showed repetitive messages. The words i remembered from the error messages where Nouveau and Xorg. Googling on that led me to installing the correct driver for my (GeForce 7650 GS) video card. (it appeared you were right [**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075"))
- after having selected everything turned out fine
- dual screen is also working without a hitch

So all turned out ok in the end

---

### Post by mörgæs on 2014-05-19
Good, please mark the thread 'solved'.

---

### Post by jan-bol on 2014-05-19
I would like to but I don's see how to do that

---

### Post by pfeiffep on 2014-05-19
Instructions posted [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

