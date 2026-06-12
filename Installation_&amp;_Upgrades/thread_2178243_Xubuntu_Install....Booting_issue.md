---
title: "Xubuntu Install....Booting issue"
date: 2013-10-02
forum: Installation &amp; Upgrades
---

### Post by SolomonMan on 2013-10-02
All,
I have been trying to setup a machine in my one garage to use as a basic desktop mostly for web browsing, PDF viewing etc. I am using a old machine I had laying around and hoped to put it back to work.

I installed Xubuntu 13.04. 

The system is a AMD XP Athlon 1700 and the Motherboard is a ECS K7SEM with 1 Gig of RAM. It does have a wireless card (TPLink TL-WN951N R), a IDE drive 60 Gigs Maxtor.

Upon First Boot it comes past the Xubuntu splash screen and then just Flashes the screen over and over likes its "Syncing" the graphics/Monitor.

I tried to troubleshoot this some and I was able to ALT-Ctrl-F1 and open terminal window. For what its worth the latest knoppix Live CD boots fine into X-Windows.

I am looking to correct this issue, troubleshoot it, or at least find out what's occurring.

Please help,
Chris

---

### Post by grahammechanical on 2013-10-02
When you installed did you tick to install thrid party software? If you did then a proprietary video driver was also installed and that video driver may be causing this problem. Do you get a Grub boot menu? If not hold down shift when booting to bring up the Grub boot menu and select Recovery mode. You will find it under the Advanced Options sub menu. At the Recovery menu select Resume. That should get you to a working desktop without loading the proprietary video driver. Then look for the Xubuntu utility that allows you to change video drivers and try the open source driver called Nouveau.

Regards.

---

### Post by mörgæs on 2013-10-02
Please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

We might have a problem with a SIS chipset.

---

### Post by sheldon-corey on 2013-10-02
not sure if pc is hanging or just taking forever to install..

Running a Dell D600 with XP Pro 32b and used wubi to dl and install xbuntu on a 20GB partition and all seems well using "Normal Mode" boot and after installing system and a few other devices it goes from the xfce to what looks just like cmd and last line appears to be hanging on CPU 0 and very top line appears to indicate a kernel debugger failure with cpu, I will admit it has been a long time since I use Linux in any form and have gotten back into android development and wish to relearn Linux for that purpose and figured easiest way was to boot into it when reading Linux for idiots style books and tutorials so I could get hard knowledge, thanks in advance...


Corey

---

### Post by tpurcell on 2013-10-02
Chris

I ran into the same issue today(on a Dell Optiplex 7010 with a Radeon HD 7470). In searching for an answer I came across this: [http://askubuntu.com/questions/339312/ubuntu-12-04-boot-problem](http://askubuntu.com/questions/339312/ubuntu-12-04-boot-problem).

I downloaded the drivers form AMD and installed them. The first time I booted the machine came right up without me having to go into Grub but the colors were really off. I tried rebooting and when it came back up everything was fine and the colors were correct.

I've rebooted several times and everything is working well.

Good luck
Tom

---

### Post by SolomonMan on 2013-10-03
All,
Give me a few days to let me walk through the above suggestions etc.... as I do not get to be in the garage except for weekends and/or occasional evenings after work.

I will follow through and post results.

Thanks!
Chris

---

### Post by SolomonMan on 2013-10-03
> **mörgæs said:**
> Please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

We might have a problem with a SIS chipset.

All,
ended up running the lshw command below is its output;
```

[SIZE=2]computerdescription: Desktop Computer
product: 1234567890
vendor: Uknown Chassis Manufacture
version: 1234567890
serial: [REMOVED]
width: 32 bits
capabilities: smbios-2.3 dmi-2.3
configuration: chassis=desktop
*-core
description: Motherboard
physical id: 0
*-firmware
description: BIOS
vendor: American Megatrends Inc.
physical id: 0
version: 062710
date: 07/15/97
size: 64KiB
capacity: 192KiB
capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
*-cpu
description: CPU
product: AMD Duron(tm) Processor
vendor: Advanced Micro Devices [AMD]
physical id: 4
bus info: cpu@0
version: 6.3.1
slot: Sockey-A
size: 950MHz
capacity: 1200MHz
width: 32 bits
clock: 66MHz
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow
*-cache:0
description: L1 cache
physical id: 5
slot: Internal Cache
size: 128KiB
capacity: 1MiB
capabilities: synchronous internal write-back unified
*-cache:1
description: L2 cache
physical id: 6
slot: Internal Cache
size: 64KiB
capacity: 1MiB
capabilities: synchronous internal write-back unified
*-memory
description: System memory
physical id: 1
size: 1019MiB
*-pci
description: Host bridge
product: 730 Host
vendor: Silicon Integrated Systems [SiS]
physical id: 100
bus info: pci@0000:00:00.0
version: 02
width: 32 bits
clock: 33MHz
configuration: driver=agpgart-sis latency=32
resources: irq:0 memory:d0000000-d3ffffff
*-ide
description: IDE interface
product: 5513 IDE Controller
vendor: Silicon Integrated Systems [SiS]
physical id: 0.1
bus info: pci@0000:00:00.1
version: d0
width: 32 bits
clock: 33MHz
capabilities: ide bus_master
configuration: driver=pata_sis latency=128
resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
*-isa
description: ISA bridge
product: SiS85C503/5513 (LPC Bridge)
vendor: Silicon Integrated Systems [SiS]
physical id: 1
bus info: pci@0000:00:01.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: isa bus_master
configuration: driver=sis630_smbus latency=0
resources: irq:0
*-network:0
description: Ethernet interface
product: SiS900 PCI Fast Ethernet
vendor: Silicon Integrated Systems [SiS]
physical id: 1.1
bus info: pci@0000:00:01.1
logical name: eth0
version: 82
serial: [REMOVED]
size: 10Mbit/s
capacity: 100Mbit/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=64 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10Mbit/s
resources: irq:3 ioport:d400(size=256) memory:cfff7000-cfff7fff memory:cffc0000-cffdffff
*-usb:0
description: USB controller
product: USB 1.1 Controller
vendor: Silicon Integrated Systems [SiS]
physical id: 1.2
bus info: pci@0000:00:01.2
version: 07
width: 32 bits
clock: 33MHz
capabilities: ohci bus_master
configuration: driver=ohci_hcd latency=64 maxlatency=80
resources: irq:5 memory:cfffc000-cfffcfff
*-usb:1
description: USB controller
product: USB 1.1 Controller
vendor: Silicon Integrated Systems [SiS]
physical id: 1.3
bus info: pci@0000:00:01.3
version: 07
width: 32 bits
clock: 33MHz
capabilities: ohci bus_master
configuration: driver=ohci_hcd latency=64 maxlatency=80
resources: irq:5 memory:cfffd000-cfffdfff
*-multimedia
description: Multimedia audio controller
product: SiS PCI Audio Accelerator
vendor: Silicon Integrated Systems [SiS]
physical id: 1.4
bus info: pci@0000:00:01.4
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=snd_trident latency=64 maxlatency=24 mingnt=2
resources: irq:11 ioport:d800(size=256) memory:cfffe000-cfffefff
*-pci
description: PCI bridge
product: AGP Port (virtual PCI-to-PCI bridge)
vendor: Silicon Integrated Systems [SiS]
physical id: 2
bus info: pci@0000:00:02.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pci normal_decode bus_master vga_palette
resources: ioport:b000(size=4096) memory:cfe00000-cfefffff memory:bfc00000-cfcfffff
*-display UNCLAIMED
description: VGA compatible controller
product: 630/730 PCI/AGP VGA Display Adapter
vendor: Silicon Integrated Systems [SiS]
physical id: 0
bus info: pci@0000:01:00.0
version: 31
width: 32 bits
clock: 66MHz
capabilities: pm agp agp-2.0 vga_controller cap_list
configuration: latency=0
resources: memory:c0000000-c7ffffff memory:cfee0000-cfefffff ioport:bc00(size=128)
*-network:1
description: Wireless interface
product: AR922X Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: b
bus info: pci@0000:00:0b.0
logical name: wlan0
version: 01
serial: [REMOVED]
width: 32 bits
clock: 66MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath9k driverversion=3.8.0-30-generic firmware=N/A latency=168 link=no multicast=yes wireless=IEEE 802.11bgn
resources: irq:3 memory:cffe0000-cffeffff
*-scsi:0
physical id: 2
logical name: scsi0
capabilities: emulated
*-disk
description: ATA Disk
product: Maxtor 6Y060L0
vendor: Maxtor
physical id: 0.0.0
bus info: scsi@0:0.0.0
logical name: /dev/sda
version: YAR4
serial: [REMOVED]
size: 57GiB (61GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 sectorsize=512 signature=000a509b
*-volume:0
description: EXT4 volume
vendor: Linux
physical id: 1
bus info: scsi@0:0.0.0,1
logical name: /dev/sda1
logical name: /
version: 1.0
serial: [REMOVED]
size: 56GiB
capacity: 56GiB
capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
configuration: created=2013-09-20 22:29:13 filesystem=ext4 lastmountpoint=/ modified=2013-10-03 17:50:01 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-10-03 17:50:01 state=mounted
*-volume:1
description: Extended partition
physical id: 2
bus info: scsi@0:0.0.0,2
logical name: /dev/sda2
size: 1007MiB
capacity: 1007MiB
capabilities: primary extended partitioned partitioned:extended
*-logicalvolume
description: Linux swap / Solaris partition
physical id: 5
logical name: /dev/sda5
capacity: 1007MiB
capabilities: nofs
*-scsi:1
physical id: 3
logical name: scsi1
capabilities: emulated
*-cdrom:0
description: CD-R/CD-RW writer
physical id: 0.0.0
bus info: scsi@1:0.0.0
logical name: /dev/cdrom1
logical name: /dev/cdrw1
logical name: /dev/sr0
capabilities: audio cd-r cd-rw
configuration: status=nodisc
*-cdrom:1
description: SCSI CD-ROM
physical id: 0.1.0
bus info: scsi@1:0.1.0
logical name: /dev/cdrom
logical name: /dev/sr1
capabilities: audio
configuration: status=nodisc
[/SIZE]

```

I was surprised to see it was a Duron Processor and slower then what Expected....I am considering replacing the motherboard as I have a Athlon XP 2200+ processor laying around and this latest issue. 

Not sure if the above will help much but anyone have any ideas?

Thanks,
Chris

---

### Post by SolomonMan on 2013-10-03
All,
Tried the Shift key and into the Grub-Recovery and received same issue but instead of blinking/syncing screen getting a blinking cursor....I let it sit for 5 minutes and same blinking cursor.

Thanks!
Chris

---

### Post by SolomonMan on 2013-10-03
All,
For the record/knowledge....To my knowledge I did not select anything other than Xubuntu Desktop....

Thanks,
Chris

---

### Post by mastablasta on 2013-10-04
> **SolomonMan said:**
> All,
For the record/knowledge....To my knowledge I did not select anything other than Xubuntu Desktop....

Thanks,
Chris

it seems SiS is indeed causing the problem:
```
[SIZE=2]*-display UNCLAIMED
description: VGA compatible controller
product: 630/730 PCI/AGP VGA Display Adapter
vendor: Silicon Integrated Systems [SiS]
physical id: 0
bus info: pci@0000:01:00.0
version: 31
width: 32 bits
clock: 66MHz
capabilities: pm agp agp-2.0 vga_controller cap_list
configuration: latency=0
resources: memory:c0000000-c7ffffff memory:cfee0000-cfefffff ioport:bc00(size=128)
[/SIZE]
```

if you have another graphics card laying arroung such as AMD or Nvidia use those instead.

---

### Post by Bucky Ball on 2013-10-04
Boot from the install CD, when it gets to 'Try' 'Install' etc, hit F6. Choose 'nomodset'. Continue to 'Try'. Did that work? If so, we can make that change permanent on the hard drive install.

---

### Post by SolomonMan on 2013-10-04
mastablasta/all,
For my future troubleshooting knowledge, how did you know that the Video card was the issue from the lshw result?

Also how does Knoppix boot up...Is the requirements for the distros different?..Can I somehow change some settings in X-windows/system to make it work......I am asking these questions for knowledge reasons only.

Most of my video cards I have laying around, unfortunately, are much older than I would like to use....If I have to upgrade the video card it may be better for me to buy a new motherboard.....but while I am on the subject.....

If I was to pick up another motherboard (most likely used) which one would you all suggest.... The only requirements I would have is I would like to use the Athlon 2200+ CPU (AXDA2200DKV3C) and I would like to use the memory (PC133 133Mhz 64Mx64 168 Pins Unbuffered, Non-ECC, Non-Registered 3.3V CL 3)  that I have laying around.  Also It would be nice if a Ethernet and a video card that works with Linux/Ubuntu was part of the package but the network card could be optional.....Suggestions?

Thanks everyone for the help so far,
Chris

---

### Post by mörgæs on 2013-10-04
Before investing money please try a fresh install of Xubuntu 12.04.

The SIS cards are a well-known problem for the latest Buntus. There are workarounds, but let's first see how 12.04 behaves.

Nouveau drivers mentioned in an above post are irrelevant, as they are only for Nvidia cards.

---

### Post by Bucky Ball on 2013-10-04
> **mörgæs said:**
> Before investing money please try a fresh install of Xubuntu 12.04.

The SIS cards are a well-known problem for the latest Buntus. There are workarounds, but let's first see how 12.04 behaves.

Nouveau drivers mentioned in an above post are irrelevant, as they are only for Nvidia cards.

+1 to all of this. You say you have other vid cards sitting around. Maybe try one that ISN'T the SIS. That might solve your problem. What ya got?

PS: My 'nomodset' suggestion is probably superfluous. I didn't notice the SIS. ;)

Generally when everything seems to be working okay on install until the screen starts doing odd things ... it's graphics. And usually if it doesn't give any indication it's not via an error message to the contrary. Choosing 'nomodset', in a lot of cases, at least gets you to a desktop so you can make some permanent changes and do some troubleshooting. 

In this case, it is probably the SIS, as mörgæs says.

---

### Post by SolomonMan on 2013-10-04
All,
So its known the video is onboard currently.

I believe the PCI cards I have are like Trident S3 cards....but that is just a guess as I am not in front of them (old) currently....

I do have a 3dfx AGP card from years ago and a Matrox AGP card that had all the bells and whistles at the time but I am afraid they were not compatible with the motherboard.  ( I believe the one card had power requirement issues but that's from memory)

I will take a look over the weekend and try a couple things out....Let you know what I find.

Thanks
Chris

---

### Post by SolomonMan on 2013-10-14
All,
Did a fresh install of 12.04 and it came up without a problem!

I played around with it for about 20 or so minutes last night and I shut it down but just before it asked me if I would like to do the 90+ updates (I did not do the updates)....With these updates in mind will these updates, going forward, cause me any kind of issue?  ( I know this may be a open ended question...previous experiences? :) )

 What I mean is will the machine no longer work (as it did with the 13.04 install)....as things will sooner or later, I assume, be upgraded to 13.04 point?

I also recently picked up another motherboard (PC Chips) with a trade for some old hardware that will support the memory and Athlon I have laying around so now I have to make the decision upgrade this Duron machine (replace motherboard) or build another box....probably going to build another box and give this machine to my 4 year old daughter.

Anyways thanks for all the help,
Chris

---

### Post by mörgæs on 2013-10-14
> **SolomonMan said:**
> What I mean is will the machine no longer work (as it did with the 13.04 install)....as things will sooner or later, I assume, be upgraded to 13.04 point?



No. Select parts of 13.04 (and 13.10) will be backported to 12.04, but far from the entire system. 

It's likely that your install will keep working after the update (and you don't really have a choice, if you want to stay secure). Try it and let us know the result.

---

### Post by SolomonMan on 2013-10-15
All,
I will go forward with the updates sometime later this week. (crazy week)

I will let everyone know the initial results and then pop in on this thread occasionally and let you know what I find.


Thanks everyone for the help,
Chris

---

### Post by Bucky Ball on 2013-10-15
Doubt you'll find anything. Updates are a normal part of Ubuntu life and, at least with an LTS release, shouldn't break anything. Rare.

---

### Post by mastablasta on 2013-10-16
12.04 will be supported for quite some time and it is posisbel that this problem found in 13.04 will be solved in the future. it would help if you reported a but for it so someone is assigned to it or they will connect you with previously existing bugs and you can then subscribe to them and see if they get solved.

---

