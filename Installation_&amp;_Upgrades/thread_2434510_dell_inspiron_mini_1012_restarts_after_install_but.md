---
title: "dell inspiron mini 1012 restarts after install but any further boots hang"
date: 2020-01-07
forum: Installation &amp; Upgrades
---

### Post by iminfargo on 2020-01-07
I have an obviously ancient Dell Mini 1012,  I know it's a single core Atom processor and there is 2gb of memory.  I downloaded the lubuntu 19 (?) iso and burned it to a dvd on my normal laptop.  I connected an external dvd drive to the Dell Mini and was able to boot and install lubuntu.

At the end of the install I selected restart.  It restarted fine and went to the desktop.  I hooked up a hard wire connection to my router so I could install the wireless drivers.

I shutdown that session and then later went to reboot.  I spins the little swirl on the lubuntu screen a few times and just hangs.  

I did the best I could at research on the net and it was mentioned in might be the vga= boot option that would help.  I tried vga=771 and still had the same problem.  I then tried vga=788 and still had the same problem.

I don't know much about any of this so I'm just looking for some help.

I know the mini is VERY old but I'm trying to get it running to install a BINGO calling program I wrote and then giving it to the bingo playing group here in our seniors apartments

Thank you.

---

### Post by mörgæs on 2020-01-07
Hi, welcome to the fora.

Let's see more of the hardware. Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it onto the command line, run it and post lshw.txt in CODE tags. Can be done from a live boot.

---

### Post by iminfargo on 2020-01-08
The output follows below.  I did notice a couple of things:  after install if I turn off the PC instead of restart it doesn't boot.  It's only on a restart request when the installation finishes.  All things considered, are the things that only happen on first boot but not subsequent boots?  

after watching linux boot on my Chromebook it appears to be right about the time it is setting up the video or starting  x, but that's only a very naive shot in the wind.

```
me@ubuntu:~$ sudo lshw -sanitize > lshw.txt
[sudo] password for me: 
me@ubuntu:~$ cat lshw.txt   
computer
    description: Portable Computer
    product: Inspiron 1012
    vendor: Dell Inc.
    version: A12
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=portable cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 1
          version: A12
          date: 03/22/2011
          size: 103KiB
          capacity: 1984KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer int10video acpi usb smartbattery biosbootspecification netboot
     *-board UNCLAIMED
          description: Motherboard
          vendor: Dell Inc.
          physical id: 3
          version: A12
          serial: [REMOVED]
          slot: Not Applicable
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N450   @ 1.66GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 6.12.10
          serial: [REMOVED]
          slot: CPU 1
          size: 1562MHz
          capacity: 1667MHz
          width: 64 bits
          clock: 667MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts cpuid aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dtherm cpufreq
          configuration: cores=1 enabledcores=1 id=0 threads=2
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-back
             configuration: level=2
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 2GiB
        *-bank
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: HYMP125S64CP8-Y5
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 0
             serial: [REMOVED]
             slot: J6G1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0200000-f027ffff ioport:18d0(size=8) memory:d0000000-dfffffff memory:f0000000-f00fffff memory:c0000-dffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0280000-f02fffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:26 memory:f0500000-f0503fff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:80000000-804fffff ioport:f0f00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: enp5s0
                version: 02
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:24 ioport:2000(size=256) memory:f0f20000-f0f20fff memory:f0f10000-f0f1ffff memory:80000000-8001ffff
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:3000(size=4096) memory:f0100000-f01fffff ioport:80500000(size=2097152)
           *-network
                description: Network controller
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Limited
                physical id: 0
                bus info: pci@0000:07:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:17 memory:f0100000-f0103fff
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-20-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Mouse
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@2:1
                   version: 22.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-20-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-20-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-20-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f0504000-f05043ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.15.0-20-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb:0
                   description: Mass storage device
                   product: Portable Super Multi Drive
                   vendor: Hitachi-LG Data Storage Inc
                   physical id: 3
                   bus info: usb@1:3
                   logical name: scsi4
                   version: 0.00
                   serial: [REMOVED]
                   capabilities: usb-2.00 atapi emulated scsi-host
                   configuration: driver=usb-storage maxpower=500mA speed=480Mbit/s
                 *-cdrom
                      description: DVD-RAM writer
                      product: DVDRAM GP55EX70
                      vendor: HL-DT-ST
                      physical id: 0.0.0
                      bus info: scsi@4:0.0.0
                      logical name: /dev/cdrom
                      logical name: /dev/cdrw
                      logical name: /dev/dvd
                      logical name: /dev/dvdrw
                      logical name: /dev/sr0
                      version: PF00
                      capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                      configuration: status=open
              *-usb:1
                   description: Video
                   product: Laptop_Integrated_Webcam_1.3M
                   vendor: SuYin
                   physical id: 4
                   bus info: usb@1:4
                   version: 9a.14
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: NM10 Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: NM10/ICH7 Family SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:25 ioport:18e8(size=8) ioport:18dc(size=4) ioport:18e0(size=8) ioport:18d8(size=4) ioport:18c0(size=16) memory:f0504400-f05047ff
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18a0(size=32)
     *-scsi
          physical id: 0
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG HM160HI
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0-15
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=7845965b
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 149GiB
                capacity: 149GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2020-01-08 03:11:30 filesystem=ext4 lastmountpoint=/target modified=2020-01-08 04:08:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2020-01-08 03:11:49 state=mounted
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound
me@ubuntu:~$ 
```

---

### Post by iminfargo on 2020-01-08
Also please note that the lubuntu dvd i downloaded doesn't have a live session option - I have to install lubuntu all over again each time I need to get information or try something.

I also noticed that in lspci it shows the driver in use as i915.  I seem to remember reading somewhere about i915.modeset=0 so I tried to reboot and enter that in as a boot option.  However it only goes so far before it stops the boot with messages about my BCM wireless.  So I assume I'm going to have to go through the entire installation process again so that I can actually boot on that first restart and figure out how to install the wireless drivers,  I should be able to find that information somewhere.  The thing is, with this slow single core processor it takes FOREVER to do the install, so I'd prefer to not keeping doing so without thinking I might actually be accomplishing something.

So, I'll go through it again, install the wireless drivers and try a boot with i915.modeset and see what happens but that will all have to wait - I have got to get to bed.

Thank you.

---

### Post by ajgreeny on 2020-01-08
I am a bit surprised that the Lubuntu iso file you downloaded did not have a live option when you booted so tell us exactly what that iso is named.

Did you download an **Alternate ISO** from [https://lubuntu.me/downloads/](https://lubuntu.me/downloads/) or was it from some other source?

Incidentally, I have an even lower powered Atom 270N powered netbook with only 1G ram on which I installed Debian-10, using the Debian-10-netinstall.iso, and added LXDE during installation; it is not fast but it does run well enough to be useful for browsing and emails and word processing or spreadsheets with abiword and gnumeric.

---

### Post by iminfargo on 2020-01-08
I just checked my download:  lubuntu -18.04-alternate-i386 so it must be an alternate dvd.    I remember what was supposed to be the lubuntu web site.  I think the processor is 64-bit so I'm going to go back and try to find the newest 64-bit version that allows the live run, download it and start again.

I'll let you know what happens from there.

Thanks.

---

### Post by mörgæs on 2020-01-09
Though your hardware supports a 64 bit OS I'm not sure it's the best choice. 

If you find that it's slow you could also try [Debian 32 bit]("https://ubuntuforums.org/showthread.php?t=2130640&page=22&p=13902890&viewfull=1#post13902890").

---

### Post by iminfargo on 2020-01-09
So I downloaded the 64-bit desktop iso which seemed to be working ok.  I installed to my hard drive and it rebooted once ok at which point I searched online for someway to enable a bcm4312 wireless.  Found a post in the ubuntu forums about using something called STA so I followed those instructions and it worked then.  Powered down.  On restart it hung pretty close to right away.  I rebooted and kept pressing shift until the boot menu came up.  I tried adding l915.modeset=1 and doing F10 for it to boot.  It went through a little way in text, got to a message about sta and then gave me 3 messages about a read error on the disk and stopped.  So I swapped out the hard disk with a spare 128GB SSD I had, reinstalled, and now it won't do the reboot.  Nothing shows up - just the backlight is on the screen.  I guess I'll try downloaded the livedvd for 32-bit and try that to see if it helps.  64-bit is really not going to do much better on this system.  I know - wider bus, prefetch, etc., but the end result is that it is a old slow machine.  I don't like how the wireless turned out so if I can ever get this installed so it actually boots I can try messing with that.

Anyone have any advice for this poor novice?

Thanks.

---

### Post by iminfargo on 2020-01-09
Morgaes - I missed your reply.  I agree on the 64-bit - it won't help on something this old.

---

### Post by guiverc on 2020-01-09
FYI:  the Alternate (18.04 LTS) ISO is for low RAM machines. The live system runs best with most of 700MB of RAM, the `ubiquity` installer also most of 700MB of ram to fully function; so the Alternate installer is built for machines with only 700MB that cannot run 'live' & 'installer' at the same time, ie. low RAM boxes.  It also hasn't been re-spin since the original 18.04 release (ie. no 18.04.1/.2/.3..) as few people use it, but isn't needed if you machine has >700MB of RAM.

Also be aware of where you downloaded the ISO from.  Search engines point to a number (*3 that I'm aware of*) sites that offer Lubuntu for download (only 1 is under the control of the Lubuntu team & Canonical); and the unofficial sites tend to offer the alternate more than the official site ([http://lubuntu.me/](http://lubuntu.me/)) does.   I'd suggest sticking to official Ubuntu or Ubuntu flavor (Lubuntu) sites (ie. go through [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) to find out which is the official sites for any flavor, and don't ask search engines).

---

### Post by iminfargo on 2020-01-09
The downloads have been from the lubuntu site - I just clicked the wrong download the first time and that's how I got the alternate.  I have since tried both the 32-bit and 64-bit versions of the livedvd and when it boots up clicking to install lubuntu.  I tried both with and without selecting the install of extra software/drivers/etc., still to no avail.  What i have always happen is that it restarts after installation just fine, but any subsequent boot still hangs.  The latest has been that the screen with the 5 dots shows for about 3 seconds, then it goes to a blank screen, the hard disk blinks a few times and then it hangs.  So, I have to ask, what does Ubuntu and it's derivatives do on the very first boot that it doesn't do any other time?  Surely it has to know "first boot"?  What ever happens during that seems to negate being able to boot again.

---

### Post by iminfargo on 2020-01-09
Just tried the same thing with xubuntu 18.04(?) - same problem.  So, this little thing has a resolution of 1024x600 which I know really isn't a standard resolution.  Is it possible that this is causing the problem?  Perhaps this is when X is starting up?

---

### Post by iminfargo on 2020-01-12
I think it is hanging when it is starting X.  On the initial boot after installation the screen goes blank at about the same time and then goes to the arrow in the screen while X comes up.  On second boot it hangs at this point with a dash or underbar in the top left of the screen.  If I reboot a live session and look on the drive i installed to there doesn't seem to be any errors in the log files I have found on that disk's /var directory.

---

### Post by mörgæs on 2020-01-12
How does Debian behave?

---

### Post by iminfargo on 2020-01-15
So sorry - I didn't realize 2 things in your previous reply:
(1) it was actually a link to Debian
(2) Debian was an actual version of linux

I'll be trying that later tonight and post back the results.

Thanks!

---

### Post by iminfargo on 2020-01-16
Same result.  Windows 10 installs and runs - albeit slowly.  It's not worth the hassle to me, so I'm just going to trash it.

---

### Post by mörgæs on 2020-01-16
I thin it's too early to give up.

What exactly is the error / problem when using Debian? Same as in post 13?

---

