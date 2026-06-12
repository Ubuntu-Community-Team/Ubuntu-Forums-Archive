---
title: "failure to install OS on dual boot at &quot;select and install software&quot; stage"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by Eagle Nest on 2014-04-21
OK, I have installed lubuntu 12.04 on an old tower, having got rid of the (expletive) Windows XP OS. Hooray for that step. I made sure to do all the updates (400 of them) while connected to the hard line but the normal location for the PC requires wireless connection. (I can move the tower, if I must, temporarily and connect to the hard line for upgrades, ISO images, etc.) 

And that's where the difficulty lies. I should add that I'm a lubuntu newbie. The main reason I installed the lubuntu as a stand alone OS on the tower was to make sure that I had a dedicated machine for a Linux OS. I just found I wasn't using the Ubuntu OS on my dual boot laptop. 

Anyway, about the wireless connection. 

1. I get a "Authenticate" dialogue box re Network Manager that asks for my password. Upon entering the pasword and clicking on Authenticate, I get another dialogue box indicating that Authentication is required by the wireless network. So then I enter the Wireless network password, click on connect , and ...

2. nothing. It doesn't connect. pointing the cursor down at an icon on the taskbar given me "Configuring wireless network connection (name)" but it simply loops back and again asks for the network password. It never connects. Yes, i checked the password. 

i recently installed the card myself. it is for an Airlink 101 ... 802.11 G Wireless PCI Adaptor. I even sent an e mail to Airlink and then replied as follows:

> Hey Xxxxx, 

Thanks for contacting us.
We no longer officially support this model but you can find the drivers from the Internal Chipset Manufacturer.
Here is the link to the chipset page for the AWLH3028

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=5&Level=6&Conn=5&ProdID=37&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=5&Level=6&Conn=5&ProdID=37&DownTypeID=3&GetDown=false&Downloads=true)

 Yours Sincerely,
Oxxxxx 

OK, so now what?

---

### Post by mörgæs on 2014-04-21
12.04 is out of support. I suggest that you begin with a fresh install of Lubuntu 14.04 using wired internet access. Please post again when all updates have been applied and everything works (with wired).

---

### Post by Eagle Nest on 2014-04-23
Thanks for the reply. I may just have to do that upgrade. However, I would like to be sure that I can do that, given my current hardware. What do I need, hardware wise?

---

### Post by mörgæs on 2014-04-23
If you are able to run 12.04 you can also run 14.04.

---

### Post by Eagle Nest on 2014-04-23
OK, I'm on it. Let's see how things go.

---

### Post by Eagle Nest on 2014-04-24
> **mörgæs said:**
> 12.04 is out of support. I suggest that you begin with a fresh install of Lubuntu 14.04 using wired internet access. Please post again when all updates have been applied and everything works (with wired).

This advice failed. The 14.04 would not install and, in fact, kept crashing over and over again. If I wasn't dedicated to getting a Linux OS on this tower, I would have thrown it in a landfill long ago. 

1. The MD5Sum is OK for 14.04

2. I checked the USB for errors. It was fine. 

3. The Lubuntu 12.04, which "hangs up" and often has to be re-booted, at least runs and works. When it is connected to a network I can use the browser, download files, install updates, (UNetbootin, etc.). The only problem is the issue of wireless connectivity. And for this it is recommended to install another Operating System. 

4. Lubuntu 14.04 will not install. It crashes EVERY time. If I check the USB for errors, it is fine. I have tried different USB drives. No difference. I am not even able to get the "try Lubuntu" to work. Nada. 

5. The install begins, I get that ubuntu/lubuntu row of dots on the screen during an aborted install, it never goes past about 20-24 dots changing colours, then hangs up, done. I tried leaving it overnight. No difference. 

6. Other issues. 

a. Perhaps it is the file system? I have, AFAIK, NTFS on the HDD and the USB is, of course, FAT32.  If this is a problem, can I format the HDD from the Lubuntu on the hard drive that does work, and try something else?

b. I have only ever been able to boot from CD/DVD when I had the WindowsXP install Disc in the drive. At no other time did the machine even look at booting with this drive. OTOH, whatever USB drive I put the USB thumb drive into, the machine recognizes it and seems to try to boot from it if I give the correct instructions. It just never completes the cycle, never installs, never allows me to "try" the Lubuntu, althought the check for errors is always fine.

---

### Post by Eagle Nest on 2014-04-24
> **mörgæs said:**
> 12.04 is out of support. I suggest that you begin with a fresh install of Lubuntu 14.04 using wired internet access. Please post again when all updates have been applied and everything works (with wired).

Perhaps I'm reading you wrong. These remarks can be interpreted a number of ways. One way, which is what I tried to do, was to create a USB install drive for 14.04 and attempt to install. Nada, as I noted above. 

Another way would be to do every single upgrade, one at a time, (perhaps including updates on the way, and not just at the 14.04 OS) until I had 14.04 installed and running. Is this latter what you meant with your remarks?

---

### Post by mörgæs on 2014-04-24
I recommend a fresh install of 14.04 and warn against upGRADE from older versions to 14.04. 

When 14.04 is running a number of upDATES (new software within same release number) should be applied. For doing this you need the two commands 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

and yes, the names of the commands are confusing in light of what I wrote above.


If the standard 14.04 ISO does not work we have to take a closer look at the hardware. Please run (using any Buntu version) ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Eagle Nest on 2014-04-30
> **mörgæs said:**
> I recommend a fresh install of 14.04 and warn against upGRADE from older versions to 14.04. 

When 14.04 is running a number of upDATES (new software within same release number) should be applied. For doing this you need the two commands 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

and yes, the names of the commands are confusing in light of what I wrote above.

I am having a difficult time with the installed OS of Lubuntu 12.04. With 10 attempts to start up, I get about 2 that work. So I am doing the second step you recommend even before I try to get the USB of 14.04 to install. 


> If the standard 14.04 ISO does not work we have to take a closer look at the hardware. Please run (using any Buntu version) ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

ok, here it is...

```
computer
    description: Mini Tower Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0N2828
       vendor: Winbond Electronics
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A07
          date: 11/06/2003
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2666MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: CHANNEL A DIMM 0
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: CHANNEL B DIMM 0
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 2
             slot: CHANNEL A DIMM 1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns) [empty]
             physical id: 3
             slot: CHANNEL B DIMM 1
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-efffffff
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:fd000000-feafffff memory:f0000000-f7ffffff
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:fea00000-fea1ffff
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff80(size=32)
        *-usb:1
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff60(size=32)
        *-usb:2
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff20(size=32)
        *-usb:4
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ffa80800-ffa80bff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:fcf00000-fcffffff
           *-network:0
                description: Wireless interface
                product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 20
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8180 driverversion=3.2.0-60-generic firmware=N/A latency=64 link=no maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
                resources: irq:21 ioport:de00(size=256) memory:fcfeec00-fcfeefff
           *-communication UNCLAIMED
                description: Communication controller
                product: Conexant Systems, Inc.
                vendor: Conexant Systems, Inc.
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
                resources: memory:fcff0000-fcffffff ioport:ddb8(size=8)
           *-network:1
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 memory:fcfef000-fcfeffff ioport:ddc0(size=64)
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
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
             bus info: pci@0000:00:1f.1
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:febffc00-febfffff
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM GDR8162B
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/sr0
                version: 0015
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: CD-RW  CRX216E
                vendor: SONY
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/sr1
                version: PD01
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fea0(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD2500AAKS-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: [REMOVED]
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00066f0f
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 231GiB
                   capacity: 231GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2014-04-19 22:47:43 filesystem=ext4 lastmountpoint=/ modified=2014-04-20 23:21:32 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2014-04-29 14:24:35 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 1534MiB
                   capacity: 1534MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1534MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:eda0(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory:febffa00-febffbff memory:febff900-febff9ff

```

---

### Post by mörgæs on 2014-04-30
The hardware looks fine. 
Have you tried running **memtest** from the boot menu? Best is to let it run for several hours.

If errors are showing please remove one or more of the memory sticks and try again.

---

### Post by Eagle Nest on 2014-04-30
> **mörgæs said:**
> The hardware looks fine. 
Have you tried running **memtest** from the boot menu? Best is to let it run for several hours.

If errors are showing please remove one or more of the memory sticks and try again.

OK, will do. I'm not sure what you mean by all this, but I will look things up and go from there. 

The 12.04 Lubuntu OS starts up, after a few attempts, (although it hangs up like it's a Windows OS, ugh!) , but I have not been able to get the USB for the 14.04 Lubuntu to do anything.

---

### Post by mörgæs on 2014-04-30
I was wondering if one of the memory sticks was failing. 

You could also try booting with only the 1 GB stick or with only the two small ones.

---

### Post by Eagle Nest on 2014-04-30
> **mörgæs said:**
> I was wondering if one of the memory sticks was failing. 

I presume you mean the external USB flash drive that I've been using as a boot device to (unsuccessfully) install Lubuntu 14.04. I'm not sure what you mean by "one of the memory sticks" as the only other USB flash drive I have is one that has somehow become write protected and, for the life of me, I can't figure out how to remove the write protect. 

> You could also try booting with only the 1 GB stick or with only the two small ones.

I dunno what you mean here.

update: I am running a Memtest for the next couple of hours. Does this sort of test apply to the USB drives that are installed externally, eg, the USB drive for the Lubuntu 14.04? Confused.

---

### Post by Eagle Nest on 2014-04-30
> **mörgæs said:**
> The hardware looks fine. 
Have you tried running **memtest** from the boot menu? Best is to let it run for several hours.

If errors are showing please remove one or more of the memory sticks and try again.

OK, "pass complete, no errors ..." was the message I got. That was in relation to the following 

(memtest86+)

but I did not try 

(memtest86+, serial console 115200)

...

---

### Post by mörgæs on 2014-04-30
I was referring to the three RAM sticks (1*1 GB and 2*256 MB) as seen in the output from lshw. Nevermind, if memtest is happy that's not the problem. 

Have you tried the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---

### Post by Eagle Nest on 2014-04-30
> **mörgæs said:**
>  Have you tried the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

I can do that. I haven't tried that yet. 

I'm just wondering if, given the problems with simply starting up the current version of Lubuntu, I should be going back to square one by reformatting the hard drive, etc.

---

### Post by Eagle Nest on 2014-05-02
01234567890

---

### Post by mörgæs on 2014-05-03
> **Eagle Nest said:**
> 
i get an Ubuntu prompt when I boot up, welcoming me to ubutu 14.04 LTS. This is a black/white screen (terminal?) in which i get the prompt ...

username@ubuntu:~$


What happens if you write **startx** here?

> **Eagle Nest said:**
> 
the only times the machine allowed me to boot from the CD/DVD drive was when there was a Windows OS disc in the drive. The rest of the time the machine just ignored any LINUX install discs.


Seems like you have burned the CD the wrong way. Does it work in other computers? 

> **Eagle Nest said:**
> 
...random rants...

If you expect the conversation to carry on I suggest that you post only facts related to the installation. You are free to post your opinions about Buntu in another forum an in another wording.

---

### Post by Eagle Nest on 2014-05-05
xyz

---

### Post by Eagle Nest on 2014-05-06
> **mörgæs said:**
> What happens if you write **startx** here? 

Nothing happens. 

> Seems like you have burned the CD the wrong way. Does it work in other computers? 

Yes. Although I should re-iterate that the install ends with a failure at the "select and install software" step. The "Basic" install is before that, so perhaps that explains why i ma getting a sort of command prompt as follows

"Ubuntu 14.04 LTS ubuntu tty1
login: "

... but that's it.

---

### Post by Eagle Nest on 2014-05-06
I've been trying to install a Linux OS to run properly on an old tower that was used for Windows XP in the past. Endless problems with the install took me to the present situation in which I re-installed the Windows OS, upgraded to XP (sp3), and then tried to install Lubuntu 14.04 using a USB thumb drive. The install failed at the stage of "select and install software" . 

So, I have a dual boot now, with the XP Operating System and the grub that gives me some Ubuntu options (ie Lubuntu). On starting the Lubuntu I get something that looks like a command prompt as follows..

> Ubuntu 14.04 LTS ubuntu tty1
login: 

... and I can login with my account and password. However, typing "startx" does nothing. 

So. Where to now? 

1. Do I uninstall the Lubuntu that failed to completely install so that I can try again with maybe a different USB and/or a different Linux OS? How do I do that?

2. Can I simply "burn" another USB with a Linux ISO and will that do the trick? 

Which is best?

---

### Post by sudodus on 2014-05-07
It will make it easier to help, if you specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

There could be different reasons why your installation failed at "select and install software".

- Maybe you have too low RAM, so that the installer fails. Maybe there was some other problem.
- Have you checked with md5sum that the download was good? Have you checked that the install USB drive is good (one of the menu options)?
- How did you create the USB boot drive (which tool)?

 Use your ability to log in to run some commands to explore your system!

```
sudo parted -l
```
```
df -h
```

***df -h*** should show that Lubuntu's root partition uses slightly more than 2 GB. If less than 2 GB, the installation was stopped before it finished.

---

### Post by mörgæs on 2014-05-07
I'm running low on ideas. What about one of the 12.04-based distros like Bodhi Linux (but not the regular Lubuntu)?

---

### Post by Eagle Nest on 2014-05-07
**[I've started another thread under Installation and Upgrades]("http://ubuntuforums.org/showthread.php?t=2222514")** but I will note the recommendation of Bodhi Linux.

---

### Post by Eagle Nest on 2014-05-07
> **sudodus said:**
> It will make it easier to help, if you specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card 

It should all be here...


```
computer
    description: Mini Tower Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0N2828
       vendor: Winbond Electronics
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A07
          date: 11/06/2003
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2666MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: CHANNEL A DIMM 0
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: CHANNEL B DIMM 0
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 2
             slot: CHANNEL A DIMM 1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns) [empty]
             physical id: 3
             slot: CHANNEL B DIMM 1
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-efffffff
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:fd000000-feafffff memory:f0000000-f7ffffff
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:fea00000-fea1ffff
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff80(size=32)
        *-usb:1
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff60(size=32)
        *-usb:2
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff20(size=32)
        *-usb:4
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ffa80800-ffa80bff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:fcf00000-fcffffff
           *-network:0
                description: Wireless interface
                product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 20
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8180 driverversion=3.2.0-60-generic firmware=N/A latency=64 link=no maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
                resources: irq:21 ioport:de00(size=256) memory:fcfeec00-fcfeefff
           *-communication UNCLAIMED
                description: Communication controller
                product: Conexant Systems, Inc.
                vendor: Conexant Systems, Inc.
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
                resources: memory:fcff0000-fcffffff ioport:ddb8(size=8)
           *-network:1
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 memory:fcfef000-fcfeffff ioport:ddc0(size=64)
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
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
             bus info: pci@0000:00:1f.1
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:febffc00-febfffff
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM GDR8162B
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/sr0
                version: 0015
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: CD-RW  CRX216E
                vendor: SONY
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/sr1
                version: PD01
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fea0(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD2500AAKS-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: [REMOVED]
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00066f0f
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 231GiB
                   capacity: 231GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2014-04-19 22:47:43 filesystem=ext4 lastmountpoint=/ modified=2014-04-20 23:21:32 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2014-04-29 14:24:35 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 1534MiB
                   capacity: 1534MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1534MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:eda0(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory:febffa00-febffbff memory:febff900-febff9ff

```

In regard to the two commands ...

sudo parted -l 

........... gave me "command not found". (There is a list of commands that I can list by typing help)

df -h gave me the following...

Filesystem.............Size........Used...........Avail.......Use%.......Mounted on........

/dev/sda5..............219G.......825M......219G...........1%................./
none.........................4.0K.........0..............4.0K.............0%............../sys/fs/cgroup
udev.........................744M.......4.0K.........744M..........1%............./dev
tmpfs.......................151M........504K........151M.........1%............./run
none..........................5.0M.........0.................5.0M..........0%............/run/lock
none..........................755M........4.0K...........755M........1%............/run/shm
none...........................100M........0.................100M.........0%........../run/user
/home/myusername/.Private........219G.........825M.......207G..........1%.........../home/myusername

---

### Post by oldfred on 2014-05-08
Some very old systems or systems with BIOS having drive set to the old IDE mode have issues booting from any boot file/partition beyond 137GB. If system is new enough AHCI is prefered but XP has to be installed with that driver and is very difficult to add later. Next is LBA or large for large block allocation. Do not use RAID setting if you have it.

If you added a much larger hard drive you can run into that issue, but it is more common with external drives and USB connections.

You are showing a very large / (root) and encrypted /home. Swap also will not show in many tools as it also is encrypted with the encrypted /home.

If you have the BIOS issue, you have to have either a much smaller / partition (20GB) fully inside the 137GB or a separate /boot (300MB) partition fully inside the 137GB. You can shrink XP and have a NTFS data partition and /home or Linux data partitions after the 137GB limit. Reading data is not the issue, just booting.

---

### Post by mörgæs on 2014-05-08
> **Eagle Nest said:**
> **[I've started another thread under Installation and Upgrades]("http://ubuntuforums.org/showthread.php?t=2222514")** but I will note the recommendation of Bodhi Linux.


Threads merged.
Please keep everything in one thread only. People are wasting their time if they don't get to see the history of the problem.

---

### Post by sudodus on 2014-05-08
See the high-lighted [COLOR=#0000ff]blue[/COLOR] and [COLOR=#ff0000]red[/COLOR] text

> **Eagle Nest said:**
> It should all be here...


```
...
     *-cpu
          description: CPU
          product: [COLOR=#0000ff]Intel(R) Pentium(R) 4 CPU 2.66GHz[/COLOR]
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2666MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
...
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: [COLOR=#0000ff]1536MiB[/COLOR]
...
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-efffffff
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:fd000000-feafffff memory:f0000000-f7ffffff
           *-display
                description: VGA compatible controller
                product: [COLOR=#0000ff]NV34 [GeForce FX 5200][/COLOR]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:fea00000-fea1ffff
...
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:fcf00000-fcffffff
           *-network:0
                description: Wireless interface
                product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 20
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8180 driverversion=3.2.0-60-generic firmware=N/A latency=64 link=no maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
                resources: irq:21 ioport:de00(size=256) memory:fcfeec00-fcfeefff
...
           *-network:1
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 memory:fcfef000-fcfeffff ioport:ddc0(size=64)
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
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
             bus info: pci@0000:00:1f.1
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:febffc00-febfffff
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM GDR8162B
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/sr0
                version: 0015
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: CD-RW  CRX216E
                vendor: SONY
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/sr1
                version: PD01
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fea0(size=16)
           *-disk
                description: [COLOR=#0000ff]ATA Disk[/COLOR]
                product: WDC WD2500AAKS-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: [REMOVED]
                size: 232GiB [COLOR=#006400]([/COLOR][COLOR=#0000ff]250GB[/COLOR])
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00066f0f
              *-volume:0
                   description: [COLOR=#006400]EXT4 volume[/COLOR]
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size:[COLOR=#0000ff]231GiB[/COLOR]
                   capacity: 231GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2014-04-19 22:47:43 filesystem=ext4 lastmountpoint=/ modified=2014-04-20 23:21:32 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2014-04-29 14:24:35 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 1534MiB
                   capacity: 1534MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: [COLOR=#0000ff]Linux swap / Solaris partition[/COLOR]
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: [COLOR=#0000ff]1534MiB[/COLOR]
                      capabilities: nofs
...
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory:febffa00-febffbff memory:febff900-febff9ff

```

In regard to the two commands ...

```
sudo parted -l 
```

gave me "command not found". (There is a list of commands that I can list by typing help)

```
df -h
``` gave me the following

```

Filesystem...................Size.......Used...... Avail.......Use%.........Mounted on
[COLOR=#ff0000] /dev/sda5....................219G.......825M......219G. .......1%.........../[/COLOR]
none.........................4.0K.......0......... 4.0K........0%.........../sys/fs/cgroup
udev.........................744M.......4.0K...... 744M........1%.........../dev
tmpfs........................151M.......504K...... 151M........1%.........../run
none.........................5.0M.......0......... 5.0M........0%.........../run/lock
none.........................755M.......4.0K...... 755M........1%.........../run/shm
none.........................100M.......0......... 100M........0%.........../run/user
[COLOR=#ff0000] /home/myusername/.Private....219G.......825M......207G........1%... ......../home/myusername[/COLOR]

```


***Edit***: {It looks like your installation was not complete (the [COLOR=#ff0000]red[/COLOR] text and the  lack of ***parted*** indicates that a lot of packages were not installed).  There are ways to increase the chances to succeed with some boot  options, with the alternate iso, or trying another version, flavour or  re-spin.}

-o-

Considering the link [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640") I think your computer should run with an Ubuntu based flavour,

- ***Lubuntu*** 13.10 or 14.04 LTS
- ***Xubuntu*** 12.04 LTS, 13.10 or 14.04 LTS

- or a re-spin based on Ubuntu 12.04 LTS, ***Bento, Bodhi*** or ***LXLE***.

You have enough CPU and RAM. There might be problems with the nvidia graphics card. If that is the case, try the [boot option]("https://help.ubuntu.com/community/BootOptions") ***nomodeset*** or try with Lubuntu's alternate installer.

[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

In some cases the support for old hardware is dropped in new versions, so it is a good idea to try the oldest version, that is still supported and receives security updates. In this case it is flavours and re-spins based on Ubuntu 12.04 LTS (but Lubuntu 12.04 has passed end of life).

[http://de.releases.ubuntu.com/](http://de.releases.ubuntu.com/)

---

### Post by Eagle Nest on 2014-05-08
> **sudodus said:**
> See the high-lighted [COLOR=#0000ff]blue[/COLOR] and [COLOR=#ff0000]red[/COLOR] text



***Edit***: {It looks like your installation was not complete (the [COLOR=#ff0000]red[/COLOR] text and the  lack of ***parted*** indicates that a lot of packages were not installed).  There are ways to increase the chances to succeed with some boot  options, with the alternate iso, or trying another version, flavour or  re-spin.}

-o-

Considering the link [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640") I think your computer should run with an Ubuntu based flavour,

- ***Lubuntu*** 13.10 or 14.04 LTS
- ***Xubuntu*** 12.04 LTS, 13.10 or 14.04 LTS

- or a re-spin based on Ubuntu 12.04 LTS, ***Bento, Bodhi*** or ***LXLE***.

You have enough CPU and RAM. There might be problems with the nvidia graphics card. If that is the case, try the [boot option]("https://help.ubuntu.com/community/BootOptions") ***nomodeset*** or try with Lubuntu's alternate installer.

[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

In some cases the support for old hardware is dropped in new versions, so it is a good idea to try the oldest version, that is still supported and receives security updates. In this case it is flavours and re-spins based on Ubuntu 12.04 LTS (but Lubuntu 12.04 has passed end of life).

[http://de.releases.ubuntu.com/](http://de.releases.ubuntu.com/)

Your advice was preceded by some comments in which it was suggested that my problems may be connected with the BIOS. Your remarks did not address this issue so I'm not clear what your view is on this matter.

---

### Post by Eagle Nest on 2014-05-08
> **oldfred said:**
> Some very old systems or systems with BIOS having drive set to the old IDE mode have issues booting from any boot file/partition beyond 137GB. If system is new enough AHCI is prefered but XP has to be installed with that driver and is very difficult to add later. Next is LBA or large for large block allocation. Do not use RAID setting if you have it.

If you added a much larger hard drive you can run into that issue, but it is more common with external drives and USB connections.

You are showing a very large / (root) and encrypted /home. Swap also will not show in many tools as it also is encrypted with the encrypted /home.

If you have the BIOS issue, you have to have either a much smaller / partition (20GB) fully inside the 137GB or a separate /boot (300MB) partition fully inside the 137GB. You can shrink XP and have a NTFS data partition and /home or Linux data partitions after the 137GB limit. Reading data is not the issue, just booting.

OK, so what is it that you are recommending that I do? Partition the HDD differently?

---

### Post by oldfred on 2014-05-08
Did you check BIOS settings for hard drive, and what are they?

I normally install Ubuntu in a 20 to 25GB / (root) partition and have all my data in data partitions. For a newer user a separate /home is easier to set up.
If you have one massive / partition, drive has to jump all over drive to load boot files as the Linux file system puts files anywhere in entire partition.

---

### Post by Eagle Nest on 2014-05-08
> **oldfred said:**
> Did you check BIOS settings for hard drive, and what are they?

There is a lot of information in a BIOS. Would you mind narrowing this down, otherwise I have to look up everything in the BIOS since I don't know what specifically you are referring to. Thanks. 

> I normally install Ubuntu in a 20 to 25GB / (root) partition and have all my data in data partitions. For a newer user a separate /home is easier to set up.
If you have one massive / partition, drive has to jump all over drive to load boot files as the Linux file system puts files anywhere in entire partition.

From the sounds of things, I'm going to have to look up a primer on partitioning again. A nice simple one.

---

### Post by sudodus on 2014-05-09
> **Eagle Nest said:**
> Your advice was preceded by some comments in which it was suggested that my problems may be connected with the BIOS. Your remarks did not address this issue so I'm not clear what your view is on this matter.

I don't know about your BIOS. You should look at all menu pages in it and try to identify what might be worth changing. Take notes about all changes, so that you can reset it to the previous settings. Change only one setting each time (at least in the beginning).

Often it is possible to find settings that will allow booting from USB. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

-o-

I suggest 'trial and error'. Try according to the tips you have got already :-)

---

### Post by Eagle Nest on 2014-05-14
> **sudodus said:**
> I don't know about your BIOS. You should look at all menu pages in it and try to identify what might be worth changing. Take notes about all changes, so that you can reset it to the previous settings. Change only one setting each time (at least in the beginning).

Often it is possible to find settings that will allow booting from USB. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

-o-

I suggest 'trial and error'. Try according to the tips you have got already :-)

im not sure what this means. It sounds like you are suggesting that I make one change to the BIOS, try to install the Linux OS, if it doesnt work, then undo the change and try with another change, if it doesnt work, then undo the change and try with another BIOS change, etc , etc, etc. 

??

---

### Post by sudodus on 2014-05-15
Yes. I think you can select what to test in an intelligent way, so that you need not change everything.

-o-

- Did you try according to this link?

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

- Did you check with md5sum, that the download was good. See [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

- Did you test the pendrive in another computer?

- Did you try any other version of Ubuntu?

---

### Post by Eagle Nest on 2014-05-15
OK, the process still failed at the "setup and install software" stage but I have managed a "minimum install" that gives me the Lubuntu 14.04 desktop with a couple of terminal programs (UXTerm and XTerm), FileManager PCManFM, Desktop Preferences and Openbox Configuration Manager. So far, the web browser doesn't start (may not be there).

It's primitive, but perhaps with the terminal and what I have I can get it running properly. I wasn't able to configure the network and simply skipped over that stage in the install procedure. However, it's worth noting (especially given previous problems I have had with this tower) that the Windows XP (sp3) operating system now works WITH the wireless card, and the network printer for that matter (I have a household HP wireless printer), and there is none of the wildly excessive usage patterns in the Windows task manager anymore.  It's still a bit glitchy in Windows but it works. 

My grub loader is a mess of options. I've tried this install a bunch of times, so my hard drive is partitioned a dozen times now. They're all called Ubuntu 14.04, but only one of them works. Good thing I used the same userid and password for all 3 or 4... That is something I would like some help cleaning up but, as long as it doesn't get in my way in the process of getting the Lubuntu 14.04 fully functional, I'm happy to put it on the back burner. 

So:

- a minimal Lubuntu 14.04 is running. Very minimal but more than the command prompt I was getting so far. The browser doesn't come up, the screen won't lock, and I don't know what else isn't functional. 
- the wireless card works for one of the other OS's on the tower (Windows XP), as does the wireless printer after I installed the HP software
- the problem of crazy and excessive CPU usage (as seen in Windows Task .... dialogue box) is gone
- the grub loader reveals a truckload of options [9 actually: 2 for each Ubuntu attempt (1 of which works as noted), 2 for memory checks, and 1 for the Windows OS]

So, I'm ready for the next stage.  What's the best approach? 

1. Connect the tower to a hard line and try to install what I can?

2. Try to get the wireless working and then try to install what I can?

3. Dare I reboot before I do either of 1 or 2 and just see what the grub looks like now?

4. Some other option?

---

### Post by sudodus on 2014-05-16
> **Eagle Nest said:**
> ...

- a minimal Lubuntu 14.04 is running. Very minimal but more than the command prompt I was getting so far. The browser doesn't come up, the screen won't lock, and I don't know what else isn't functional. 
- the wireless card works for one of the other OS's on the tower (Windows XP), as does the wireless printer after I installed the HP software
- the problem of crazy and excessive CPU usage (as seen in Windows Task .... dialogue box) is gone
- the grub loader reveals a truckload of options [9 actually: 2 for each Ubuntu attempt (1 of which works as noted), 2 for memory checks, and 1 for the Windows OS]

So, I'm ready for the next stage.  What's the best approach? 

1. Connect the tower to a hard line and try to install what I can?

2. Try to get the wireless working and then try to install what I can?

3. Dare I reboot before I do either of 1 or 2 and just see what the grub looks like now?

4. Some other option?

I'm glad a minimal Lubuntu 14.04 is running for you :-)

1. Connect the tower to a hard line and try to install what you can.

3. I suggest that you reboot.

---

### Post by Eagle Nest on 2014-05-16
> **sudodus said:**
> I'm glad a minimal Lubuntu 14.04 is running for you :-)

1. Connect the tower to a hard line and try to install what you can.

3. I suggest that you reboot.

The reboot worked OK. (whew)  I will try this evening and get back by tomorrow am.

As I understand it, I should be typing in the terminal as follows ..

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg -- configure -a

and then reboot , possibly with 

sudo shutdown -r now

---

### Post by sudodus on 2014-05-16
Those are good commands. *Oldfred* published this list in a post here at the Ubuntu Forums

```
# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a
```

I use these shorter commands to reboot and poweroff

```
sudo reboot
sudo poweroff
```

---

### Post by Eagle Nest on 2014-05-16
OK, will do.

---

