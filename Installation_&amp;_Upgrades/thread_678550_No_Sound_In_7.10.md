---
title: "No Sound In 7.10"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by VoiceOvGod on 2008-01-26
I cannot get my sound card to work

Fresh install of Gutsy

Have only installed the following:

```
sudo apt-get install linux-backports-modules-generic
```

Have NOT updated anything yet.

Here is my sound information

```
~$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2
  *-multimedia UNCLAIMED
       description: Multimedia audio controller
       product: SB Audigy LS
       vendor: Creative Labs
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=20 mingnt=2

```

and alsamixer shows the following:

```
:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

Soundcard is a Soundblaster Audigy SE

---

### Post by rosegarden78 on 2008-01-26
Wowzers!  Maybe the first package messed up something?  If it doesn't work out of the box that's rough.  Good luck!

---

### Post by VoiceOvGod on 2008-01-26
Nope, the card did not work as is.

---

### Post by VoiceOvGod on 2008-01-26
Followed most of the tuitorial found at:

```
https://help.ubuntu.com/community/HowToConfigureSoundBlasterAudigySEinBreezy?highlight=%28soundblaster%29
```

However, when I do the 

```

sudo apt-get install linux-headers-$(uname -r) build-essential gcc-3.4 module-assistant

sudo dpkg -i alsa-source_1.0.10+1.0.11rc2-2_all.deb #or whatever package you downloaded

```

I get the following:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.15-23-386

```

---

### Post by Pumalite on 2008-01-26
Post:
uname -a

---

### Post by VoiceOvGod on 2008-01-26
Hi again!

```
 uname -a
Linux shangrila 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

```

---

### Post by Pumalite on 2008-01-26
What are you doing with a -386 kernel? Stick to 14-generic

---

### Post by VoiceOvGod on 2008-01-26
Ok... how do I switch?

---

### Post by Pumalite on 2008-01-26
Synaptic>Search>linux-image

---

### Post by VoiceOvGod on 2008-01-26
Odd thing

I checked the package manager, it shows 14-generic installed, and not the 386.

I went to reinstall, got the following:

```
E: /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb: failed to delete `//lib/modules/2.6.22-14-generic/kernel/drivers/usb/misc/emi62.ko.dpkg-tmp'

and

E: Failed to write commit log


```

---

### Post by Pumalite on 2008-01-26
What did you reinstall? The kernel only or the whole system?. I would start from scratch, doing md5sum on iso and burning at 4x or less in good CD-R media.

---

### Post by VoiceOvGod on 2008-01-26
Just the kernel

This started as a fresh install. I verified the disk also.

---

### Post by VoiceOvGod on 2008-01-26
Ok, FRESH install. NO updates have been applied yet

In order, what should I do?

Again, thank you so much for your help. I appreciate it so much.

---

### Post by Pumalite on 2008-01-26
Do you have sound? Post:
uname -a
lshw -C sound

---

### Post by axelm on 2008-01-26
I have a similar problem. 

No sound with livecd 7.10. I'm using onboard sound not a sound card. 

```
ubuntu@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ubuntu@ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
ubuntu@ubuntu:~$ sudo lshw -C sound
ubuntu@ubuntu:~$  
```

lshw hangs at this point, although I tried it a few times and it completed but with no output.

Under System>Preferences>Sound the audio test tone fails to play with "Autodetect" (the default) and with Alsa but it works if I select "USB Audio". Selecting "USB Audio" here (under "Music and Movies") also gets sound to work in  totem. But no alsa.

screenshot attached.

---

### Post by VoiceOvGod on 2008-01-27
```
Linux shangrila 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

```

and

```
WARNING: you should run this program as super-user.
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2
  *-multimedia UNCLAIMED
       description: Multimedia audio controller
       product: SB Audigy LS
       vendor: Creative Labs
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=20 mingnt=2

```

I have not updated ANYTHING. Just straight install.

---

### Post by dustman on 2008-01-27
> Linux shangrila 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
How come you have this kernel? I also had trouble getting my sound card to work in 7.10, i had to recompile the alsa sources and got the sound running (by following slyboot's solution: [http://ubuntuforums.org/showthread.php?t=624002&page=3](http://ubuntuforums.org/showthread.php?t=624002&page=3)). But i have a 2.6.22-14 kernel. I think 2.6.15 was the default kernel for Ubuntu 6.06 or older...

---

### Post by VoiceOvGod on 2008-01-27
This was the default kernel that installed.

Again, no updates at all have been applied.

Also, that how-to seems oriented toward Intel soundcard.

What changes would I need to make for a Sound Blaster Audigy SE?

---

### Post by Pumalite on 2008-01-27
When did you download your iso? And are you sure is 7.10? Your kernel should be 22.14-generic

---

### Post by VoiceOvGod on 2008-01-27
It's one of the Official Ubuntu CDs from ShipIt

AFAIK based upon the printing, it is 7.10 :)

---

### Post by Pumalite on 2008-01-27
Something must be wrong with your installation. Download an iso from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Do md5sum, burn as image at 4x or less, check for integrity of CD before install.
Try again.

---

### Post by dustman on 2008-01-27
I'm no expert, but I searched on the official ALSA support site, and found your sound card: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs) . Just search for "Sound Blaster Audigy SE", and click in that table on "Details". You should then see a page where you can find the module for your sound card. As i see it, it's "snd-ca0106". On that page are also details showing how to install the right driver and load the right module into your kernel. Note that you'll have to download the alsa-driver sources : [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download) . If i were you i would wait for a confirmation of what i said here, cause, like i said, i'm not an expert and i might be wrong ;).


P.S. are you sure you have Ubuntu 7.10? :) Cause it's definitely the wrong kernel there...

---

### Post by VoiceOvGod on 2008-01-27
```
Linux shangrila 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

```


This is from a fresh download, md5 matched

---

### Post by Pumalite on 2008-01-27
Post:
lshw

---

### Post by VoiceOvGod on 2008-01-27
```
 *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2
  *-multimedia UNCLAIMED
       description: Multimedia audio controller
       product: SB Audigy LS
       vendor: Creative Labs
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=20 mingnt=2

```

---

### Post by Pumalite on 2008-01-27
I would like to see what hardware you are installing in.
Post:
lshw

---

### Post by VoiceOvGod on 2008-01-27
```
lshw
WARNING: you should run this program as super-user.
shangrila                 
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 1011MB
     *-cpu
          product: AMD Athlon(tm) 64 Processor 3500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 5
          bus info: cpu@0
          version: 15.15.0
          size: 18EHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial UNCLAIMED
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: latency=0 maxlatency=1 mingnt=3
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-multimedia UNCLAIMED
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: latency=0 maxlatency=5 mingnt=2
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3 module=amd74xx
        *-ide
             description: IDE Channel 0
             physical id: 0
             bus info: ide@0
             logical name: ide0
             clock: 66MHz
           *-cdrom:0
                product: JLMS DVD-ROM LTD163D
                physical id: 0
                bus info: ide@0.0
                logical name: /dev/hda
                capabilities: packet
           *-cdrom:1
                product: SONY DVD RW DW-D22A
                physical id: 1
                bus info: ide@0.1
                logical name: /dev/hdb
                capabilities: packet
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: scsi0
          logical name: scsi1
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list scsi-host
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi2
          logical name: scsi3
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list scsi-host
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
        *-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: SB Audigy LS
             vendor: Creative Labs
             physical id: 8
             bus info: pci@0000:01:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=32 maxlatency=20 mingnt=2
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a3
          serial: 00:50:70:56:06:de
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth ip=192.168.1.5 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-display
             description: VGA compatible controller
             product: NV43 [GeForce 6600 GT]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:05:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz

```

---

### Post by Pumalite on 2008-01-27
Try installing 64 bit.
You should have:
pumalite@pumalite-desktop:~$ uname -a
Linux pumalite-desktop 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64 GNU/Linux
pumalite@pumalite-desktop:~$

---

### Post by VoiceOvGod on 2008-01-27
I am rather opposed to installing 64 bit. Too many apps just dont work.

---

### Post by VoiceOvGod on 2008-01-28
HUZZAH!!!!

```
~$ uname -a
Linux shangrila 2.6.22-14-386 #1 Tue Dec 18 07:34:24 UTC 2007 i686 GNU/Linux

```

I had to load up GRUB and manually select which kernel.

Now I get to research how to get rid of the old kernel from GRUB.

And yes, my sound card is showing up!

And so is the onboard from the mobo!

Thank you again for all your help!

What I did was go into synaptic and install all the 2.6.22 packages for Generic and 386. After a reboot, it worked!

---

### Post by Pumalite on 2008-01-28
Good for you. Good luck.

---

### Post by dustman on 2008-01-28
glad to hear that ;)

Cheers!

---

