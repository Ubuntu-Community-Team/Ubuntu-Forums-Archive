---
title: "Installing Sound"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by llloyd on 2008-07-06
Hi! I hate to keep coming back here again and again but I am not finding much I can understand, as a Windows user, while trying to get the sound to work on Xubuntu 8.04 ... 

The sound card is a SB 16 Pro (CT 2290) , afaik Alsa is what is installed but after some confusion on the alsa-project website where most of the commands didn't work, like alsamixer returned a command not found error in the Terminal window. But "alsa' does return something but only options are load, unload, etc nothing about configuring it. O.o 

But I could be wrong, maybe remnants of Alsa is installed and I need the commands for the system that is indeed installed that handles sound on a default Xubuntu install. Any help be appreciated.

L. Lloyd

---

### Post by Pumalite on 2008-07-06
Let's find out if your card is recognized first. Post:
lshw -C sound

---

### Post by llloyd on 2008-07-07
Returns nothing, but noticed it isn't scanning the ISA bus, just PCI (sysfs), IDE, Scsi, and framebuffer devices... The sound card is an ISA card. O.o 

L. Lloyd

> **Pumalite said:**
> Let's find out if your card is recognized first. Post:
lshw -C sound

---

### Post by llloyd on 2008-07-08
And yes, I do have the settings for the card... <peers> 

I/O 220-22F
I/O 330-331
I/O 388-38B
IRQ 10
DMA 3
DMA 7

From the Win98 System properties...

L. Lloyd

> **Pumalite said:**
> Let's find out if your card is recognized first. Post:
lshw -C sound

---

### Post by Pumalite on 2008-07-08
Did you get that from the Terminal or your friends?.

---

### Post by llloyd on 2008-07-08
*hrrs?* From Windows 98, this is a dual boot setup. Now with that how do I go about getting this ISA sound card to work? Thanks!

L. Lloyd

> **Pumalite said:**
> Did you get that from the Terminal or your friends?.

---

### Post by Pumalite on 2008-07-08
What we are trying to determine here is if the Ubuntu kernel recognizes the card and loads the module. Looking at it from Windows is no good.

---

### Post by llloyd on 2008-07-08
And I said earlier, the command you gave me doesn't scan the ISA bus, so, no, it didn't see the ISA soundcard... That command you gave me turned up nothing...

L. Lloyd

> **Pumalite said:**
> What we are trying to determine here is if the Ubuntu kernel recognizes the card and loads the module. Looking at it from Windows is no good.

---

### Post by Pumalite on 2008-07-08
show me the nothingness...

---

### Post by llloyd on 2008-07-08
Show the nothingness... Ok... Pardon if I sound frustrated, not your fault... Let me see...

llloyd@Kenya:~$ sudo lshw -C sound
llloyd@Kenya:~$

There, nothing.

L. Lloyd

> **Pumalite said:**
> show me the nothingness...

---

### Post by Pumalite on 2008-07-08
Try:
sudo lshw

---

### Post by llloyd on 2008-07-08
llloyd@Kenya:~$ sudo lshw
kenya                     
    description: Computer
    product: System Name
    vendor: System Manufacturer
    version: System Version
    serial: SYS-1234567890
    width: 32 bits
    capabilities: dmi-2.0
  *-core
       description: Motherboard
       product: P5A-B
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.XX
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: ASUS P5A-B ACPI BIOS Revision 1011 Beta 005 (05/02/02)
          size: 64KiB
          capacity: 64KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video
     *-cpu
          description: CPU
          product: AMD-K6(tm) 3D processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 5.8.12
          slot: SOCKET 7
          size: 400MHz
          capacity: 500MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr cx8 pge mmx syscall 3dnow k6_mtrr up
        *-cache
             description: L1 cache
             physical id: 0
             size: 64KiB
     *-memory
          description: System memory
          product: FPM EDO PARITY DIMM SDRAM Memory Controller
          physical id: 5
          size: 320MiB
          capacity: 1536MiB
        *-bank:0
             description: EDO DIMM [empty]
             physical id: 0
             slot: DIMM1-2
             clock: 14MHz (70.0ns)
        *-bank:1
             description: DIMM
             physical id: 1
             slot: DIMM2-1
             size: 64MiB
             capacity: 64MiB
             clock: 14MHz (70.0ns)
        *-bank:2
             description: EDO DIMM [empty]
             physical id: 2
             slot: DIMM2-2
             clock: 14MHz (70.0ns)
        *-bank:3
             description: DIMM
             physical id: 3
             slot: DIMM3-1
             size: 128MiB
             capacity: 128MiB
             clock: 14MHz (70.0ns)
        *-bank:4
             description: DIMM
             physical id: 4
             slot: DIMM3-2
             size: 128MiB
             capacity: 128MiB
             clock: 14MHz (70.0ns)
     *-cache:0
          description: L1 cache
          physical id: c
          slot: L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: internal write-back
     *-cache:1
          description: L2 cache
          physical id: d
          slot: L2 Cache
          size: 512KiB
          capacity: 1MiB
          capabilities: pipeline-burst external write-back
     *-pci
          description: Host bridge
          product: M1541
          vendor: ALi Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-ali latency=64 module=ali_agp
        *-pci
             description: PCI bridge
             product: M1541 PCI to AGP Controller
             vendor: ALi Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Voodoo 3
                vendor: 3Dfx Interactive, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-1.0 pm vga_controller cap_list
                configuration: driver=voodoo3_smbus latency=0 module=i2c_voodoo3
        *-usb
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-bridge
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=ali15x3_smbus latency=0 module=i2c_ali15x3
        *-isa
             description: ISA bridge
             product: M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: c3
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: RTL-8029(AS)
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: eth0
             version: 00
             serial: 00:40:05:5e:b0:b0
             width: 32 bits
             clock: 33MHz
             capabilities: ethernet physical
             configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=192.168.0.2 latency=0 module=ne2k_pci multicast=yes
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             version: c1
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ALI15x3_IDE latency=32 maxlatency=4 mingnt=2 module=alim15x3
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD400AB-32BVA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 21.01H21
                   serial: WD-WMA7E1805000
                   size: 37GiB (40GB)
                   capacity: 37GiB (40GB)
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: signature=493c1b77 smart=on
                 *-volume:0
                      description: Windows FAT volume
                      vendor: MSWIN4.1
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      version: FAT32
                      serial: 0f5e-1900
                      size: 10001MiB
                      capacity: 10001MiB
                      capabilities: primary bootable fat initialized
                      configuration: FATs=2 filesystem=fat
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 27GiB
                      capacity: 27GiB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume:0
                         description: W95 FAT32 partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 17GiB
                    *-logicalvolume:1
                         description: Linux filesystem partition
                         physical id: 6
                         logical name: /dev/hda6
                         logical name: /
                         logical name: /dev/.static/dev
                         capacity: 9060MiB
                         configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                    *-logicalvolume:2
                         description: Linux swap / Solaris partition
                         physical id: 7
                         logical name: /dev/hda7
                         capacity: 941MiB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: TSSTcorp CDDVDW SH-S202G
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: SB00
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: status=nodisc
llloyd@Kenya:~$ 


> **Pumalite said:**
> Try:
sudo lshw

---

### Post by Pumalite on 2008-07-08
I don't see any sound card. Check your BIOS.

---

### Post by llloyd on 2008-07-08
Check it for what? The sound card works beautifully in Win98SE, just not seen by Xubuntu. So it has to be OS not hardware I would think?

L. Lloyd

> **Pumalite said:**
> I don't see any sound card. Check your BIOS.

---

### Post by Pumalite on 2008-07-08
open up all your ports except src and do a:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by llloyd on 2008-07-08
I apologize if I sound *stupid*, I am only a Windows user... Open up all my ports but src ? O.o 

L. Lloyd

> **Pumalite said:**
> open up all your ports except src and do a:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by Pumalite on 2008-07-08
System>Administration>Software Sources

---

### Post by llloyd on 2008-07-08
Thank you! Now, let me see...

Under the Software Sources ...

Ubuntu Software Tab ...

Canonical Sources (main) is checked
Community-maintained (Universe) is checked
Proprietary Drivers (restricted) is checked
Software Restricted by copywrite (multi verse) is checked
Source Code has a "-" though the box.

Third Party Software Tab ...

Two cdrom: is unchecked
Two http:// is checked

And the two sudo apt-get commands return...

llloyd@Kenya:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US        
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release              
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
llloyd@Kenya:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libdns35
The following packages will be upgraded:
  bind9-host dnsutils libbind9-30 libisc32 libisccc30 libisccfg30 liblwres30
7 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 903kB of archives.
After this operation, 1311kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libisc32 1:9.4.2-10ubuntu0.1 [126kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libdns35 1:9.4.2-10ubuntu0.1 [493kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libisccc30 1:9.4.2-10ubuntu0.1 [22.9kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libisccfg30 1:9.4.2-10ubuntu0.1 [38.3kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libbind9-30 1:9.4.2-10ubuntu0.1 [27.3kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main liblwres30 1:9.4.2-10ubuntu0.1 [40.1kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main bind9-host 1:9.4.2-10ubuntu0.1 [44.7kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main dnsutils 1:9.4.2-10ubuntu0.1 [110kB]
Fetched 903kB in 5s (159kB/s)    
(Reading database ... 90988 files and directories currently installed.)
Preparing to replace libisc32 1:9.4.2-10 (using .../libisc32_1%3a9.4.2-10ubuntu0.1_i386.deb) ...
Unpacking replacement libisc32 ...
Selecting previously deselected package libdns35.
Unpacking libdns35 (from .../libdns35_1%3a9.4.2-10ubuntu0.1_i386.deb) ...
Preparing to replace libisccc30 1:9.4.2-10 (using .../libisccc30_1%3a9.4.2-10ubuntu0.1_i386.deb) ...
Unpacking replacement libisccc30 ...
Preparing to replace libisccfg30 1:9.4.2-10 (using .../libisccfg30_1%3a9.4.2-10ubuntu0.1_i386.deb) ...
Unpacking replacement libisccfg30 ...
Preparing to replace libbind9-30 1:9.4.2-10 (using .../libbind9-30_1%3a9.4.2-10ubuntu0.1_i386.deb) ...
Unpacking replacement libbind9-30 ...
Preparing to replace liblwres30 1:9.4.2-10 (using .../liblwres30_1%3a9.4.2-10ubuntu0.1_i386.deb) ...
Unpacking replacement liblwres30 ...
Preparing to replace bind9-host 1:9.4.2-10 (using .../bind9-host_1%3a9.4.2-10ubuntu0.1_i386.deb) ...
Unpacking replacement bind9-host ...
Preparing to replace dnsutils 1:9.4.2-10 (using .../dnsutils_1%3a9.4.2-10ubuntu0.1_i386.deb) ...
Unpacking replacement dnsutils ...
Setting up libisc32 (1:9.4.2-10ubuntu0.1) ...

Setting up libdns35 (1:9.4.2-10ubuntu0.1) ...

Setting up libisccc30 (1:9.4.2-10ubuntu0.1) ...

Setting up libisccfg30 (1:9.4.2-10ubuntu0.1) ...

Setting up libbind9-30 (1:9.4.2-10ubuntu0.1) ...

Setting up liblwres30 (1:9.4.2-10ubuntu0.1) ...

Setting up bind9-host (1:9.4.2-10ubuntu0.1) ...
Setting up dnsutils (1:9.4.2-10ubuntu0.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
llloyd@Kenya:~$ 

Ok? Shall I redo the sudo lshw -C sound ? Thanks!

L. Lloyd


> **Pumalite said:**
> System>Administration>Software Sources

---

### Post by Pumalite on 2008-07-08
Do it again. You need backports.

---

### Post by llloyd on 2008-07-09
Backports? 

L. Lloyd

> **Pumalite said:**
> Do it again. You need backports.

---

### Post by Pumalite on 2008-07-09
Check your Software Sources again.

---

### Post by Sealbhach on 2008-07-09
I'd just like to suggest this thread here - it's helped a lot of people.

It does a step-by-step diagnostic.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


.

---

