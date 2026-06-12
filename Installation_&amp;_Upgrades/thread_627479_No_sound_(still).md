---
title: "No sound (still)"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by Zebadim on 2007-11-30
Hi,

I have been trying to solve a "no sound" problem but I have been quite unsuccessful. The sound card belongs to the HDA Intel ICH8 Family (rev 03)(Realtek 268 ).  Suggestions, please?

Thanks in advance.

---

### Post by buzzmandt on 2007-11-30
post results from lspci

---

### Post by Pumalite on 2007-11-30
Found in another thread:

My suggestion is this:

1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide below:

If it doesn't work go to [http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage), download the
alsa-driver, lib and utils and follow the Howto at the same address and look for your driver at the Sound card matrix. Then, if needed, apply the patch and add something at the end of /etc/modprobe.d/alsa-base (sudo gedit) at described in the previous link. I do not own the same laptop but I also have got a Intel Sound Card and worked a bit to have a functioning audio.
I hope it will help you

After fiddling with the sound settings trying various suggestions in the Comprehensive Sound Problem Solutions Guide thread, I totally buggered up my sound. Oh well, a fresh install of Feisty never hurt anyone and I had my /home directory on a separate partition.

After the new install, I still had the 6 symptoms described above.

Thinking that it might be some sort of .config file remnant, I created a new user and everythng worked properly. A-HA! Comparing the user home directories, I noticed the presence of a .asoundrc file and another similarly named file. After doing some research here about what the file is for (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

---

### Post by buzzmandt on 2007-11-30
is this a laptop? if so what is it

---

### Post by Pumalite on 2007-11-30
This is one more option you have:
sudo apt-get install linux-backports-modules-generic
[http://ubuntuforums.org/showthread.php?t=610854](http://ubuntuforums.org/showthread.php?t=610854)

---

### Post by Zebadim on 2007-11-30
Hi again,

Thank you so much for all your prompt replies.

The laptop is a portuguese brand called Tsunami (model Runner 9575S) . I tried to look for solutions in portuguese forums but no luck yet.

I tried the solution - sudo apt-get install-linux-backports-modules-generic - but it did not solve the problem. However, alsamixer changed, different channels appeared...

The lspci -v command:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c4000000-c6ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at f8504800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at f8500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Prefetchable memory behind bridge: 00000000cc000000-00000000cdffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: f0000000-f3ffffff
        Prefetchable memory behind bridge: 00000000fa000000-00000000fbffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: f4000000-f7ffffff
        Prefetchable memory behind bridge: 00000000fc000000-00000000fdffffff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Prefetchable memory behind bridge: 00000000c8000000-00000000c9ffffff
        Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: f8100000-f81fffff
        Prefetchable memory behind bridge: 00000000c7000000-00000000c70fffff
        Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
        Memory behind bridge: f8000000-f80fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at f8504c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0e, subordinate=0e, sec-latency=32
        Memory behind bridge: f8200000-f82fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18a0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 18d8 [size=8]
        I/O ports at 18cc [size=4]
        I/O ports at 18d0 [size=8]
        I/O ports at 18c8 [size=4]
        I/O ports at 18e0 [size=32]
        Memory at f8504000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: medium devsel, IRQ 10
        Memory at c7100000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1) (prog-if 00 [VGA])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at c6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c4000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f0000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

0a:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
        Subsystem: Intel Corporation Turbo Memory Controller
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at f8100000 (32-bit, non-prefetchable) [size=1K]
        I/O ports at 7000 [size=128]
        [virtual] Expansion ROM at c7000000 [disabled] [size=64K]
        Capabilities: <access denied>

0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
        Subsystem: Intel Corporation Unknown device 1101
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f8000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

0e:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at f8200000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

0e:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at f8200800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

0e:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: medium devsel, IRQ 10
        Memory at f8200c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

0e:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: medium devsel, IRQ 10
        Memory at f8201000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by Pumalite on 2007-11-30
From the link provided in post #5:

got it working!  wow, only took me four months! yeah enough of my whining, I know. Here's how *I* did it:

(NOTE: I know this works with my Lenovo 3000 N100 0768 E7U, I'm not guaranteeing that it works with any other model/variant)

Code:

sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
mkdir ~/alsa-src && cd ~/alsa-src
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)
sudo tar xjf alsa-driver-1.0.15.tar.bz2
sudo tar xjf alsa-lib-1.0.15.tar.bz2
sudo tar xjf alsa-utils-1.0.15.tar.bz2
cd alsa-driver-1.0.15
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
cd ../alsa-lib-1.0.15
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.15
sudo ./configure
sudo make
sudo make install

Reboot
Code:

sudo gedit /etc/modprobe.d/alsa-base

Add this line at the end of the file:
Code:

options snd-hda-intel model=3stack

Save the file, close it, reboot, and CROSS YOUR FINGERS!

As usual, if there's no sound initially, open the volume control and make sure nothing is muted. Also, open the volume control(doubleclick the speaker), click File->change device, select the OSS mixer, and make sure none of those output channels are muted either. If none of these work for you, then you can try PM'ing me, but I'm pretty new to this still.

Much of this comes from the howto at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Note: Initially, because I had fiddled with it so much, I had nothing detected - a red X next to the volume control, would tell me I had no sound card when I tried to adjust volume. To get rid of that, I ran "sudo apt-get install linux-backports-modules-generic" as suggested by Pumalite, and it restored it to (what appears to be) the default - sound card looks like it's working, but you can't hear sound out of anything.

Once again: THANK YOU to everyone who helped me here!

---

### Post by Zebadim on 2007-11-30
Thank you very much for all your help. I am going to try out the solution now.

---

### Post by Pumalite on 2007-11-30
Good luck!

---

### Post by Zebadim on 2007-11-30
No luck :-(

Oh well... time will provide an answer ;-) For the moment the answer is a silent laptop :-)

---

### Post by Pumalite on 2007-11-30
Post:
uname -r

---

### Post by Zebadim on 2007-11-30
Hi,

uname -r 

2.6.22-14-generic

thank you very much for your help
All the best

---

### Post by Pumalite on 2007-11-30
You are using the right kernel. For a moment I thought you might be using -386. Sorry. Best of luck.

---

### Post by Zebadim on 2007-11-30
According to this site ([http://kmuto.jp/debian/hcl/](http://kmuto.jp/debian/hcl/)), after inserting the relevant info (from lspci -n), it seems that my soundcard is supported snd-hda-intel. How can I be sure that this is the driver I am currently running? Sorry for the newbie question but... I am a newbie (Ubuntu - 7days approximately)

---

### Post by Pumalite on 2007-11-30
Post:
 sudo lshw -C sound

---

### Post by Zebadim on 2007-11-30
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status

---

### Post by Pumalite on 2007-11-30
Post:
lshw

---

### Post by Zebadim on 2007-11-30
nuno-laptop               
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3034MB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.10
          serial: 0000-06FA-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8600M GT
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Contoller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetLink BCM5787M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 02
                serial: 00:1b:38:2b:e9:ea
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.77 latency=0 module=tg3 multicast=yes
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:5
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-memory UNCLAIMED
                description: Memory controller
                product: Turbo Memory Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0a:00.0
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: bus_master cap_list
                configuration: latency=0
        *-pci:6
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wmaster0
                version: 61
                serial: 00:13:e8:d9:25:5b
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl4965 ip=192.168.1.128 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:7
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:0e:06.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:0e:06.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-system:1 UNCLAIMED
                description: System peripheral
                product: R5C843 MMC Host Controller
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:0e:06.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=64
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:0e:06.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=64
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0 module=ahci
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

---

### Post by Pumalite on 2007-11-30
Here is the answer to your question:
configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by Zebadim on 2007-11-30
Yep, indeed.

Thanks for your help!

---

### Post by Pumalite on 2007-11-30
You are welcome. There are a few more things you might be interested in reading:
 Re: [SOLVED] No sound after installation of Gutsy
What are you saying for analog digital jack its true..This must be unchecked..Im guessing alsa doesnt support it.
As for the other problem i solved it by:
Getting the list of sound cards
Quote:
sudo asoundconf list
Setting as default the one i want
Quote:
asoundconf set-default-card soundcard
Replacing soundcard with mine
And i used this command to test my surround 5.1:
Quote:
speaker-test -D surround51 -c 6
which after some digging on volume control and enabling from preferences new menus i manage to get it to work
__________________
Reply With Quote
 Re: [SOLVED] No sound after installation of Gutsy
What are you saying for analog digital jack its true..This must be unchecked..Im guessing alsa doesnt support it.
As for the other problem i solved it by:
Getting the list of sound cards
Quote:
sudo asoundconf list
Setting as default the one i want
Quote:
asoundconf set-default-card soundcard
Replacing soundcard with mine
And i used this command to test my surround 5.1:
Quote:
speaker-test -D surround51 -c 6
which after some digging on volume control and enabling from preferences new menus i manage to get it to work
__________________
Reply With Quote
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
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

---

