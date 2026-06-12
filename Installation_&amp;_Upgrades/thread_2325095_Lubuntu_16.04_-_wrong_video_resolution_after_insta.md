---
title: "Lubuntu 16.04 - wrong video resolution after installation, but OK with live CD"
date: 2016-05-19
forum: Installation &amp; Upgrades
---

### Post by lubuntalb on 2016-05-19
Hi,

Lubuntu 16.04 LTS i386 on Acer Aspire 3005WLMi with SIS M760GX video chip (2 GB RAM, 160 GB HD)

When I run live CD I get a 1024 x 768 resolution, that is good for me (max resol should be 1280 x 800... maybe)

After installing this distribution from the same live CD, max resolution become 640 x 480.

I don't see differences between lspci - k with Live CD and after installation.

How can I solve this problem?

Thank you

Alby


```
lspci - k (installed Lubuntu)

760/M760 Host (rev 03)
            Kernel driver in use: agpgart-amd64
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
            Kernel modules: shpchp
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] LPC Controller (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller
            Kernel driver in use: sis96x_smbus
            Kernel modules: i2c_sis96x
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller
            Subsystem: Acer Incorporated [ALI] 5513 IDE Controller
            Kernel driver in use: pata_sis
            Kernel modules: pata_acpi
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
            Subsystem: Acer Incorporated [ALI] AC'97 Modem Controller
            Kernel modules: snd_intel8x0m
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
            Subsystem: Acer Incorporated [ALI] SiS7012 AC'97 Sound Controller
            Kernel driver in use: snd_intel8x0
            Kernel modules: snd_intel8x0
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
            Subsystem: Acer Incorporated [ALI] USB 1.1 Controller
            Kernel driver in use: ohci-pci
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
            Subsystem: Acer Incorporated [ALI] USB 1.1 Controller
            Kernel driver in use: ohci-pci
00:03.2 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
            Subsystem: Acer Incorporated [ALI] USB 2.0 Controller
            Kernel driver in use: ehci-pci
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
            Subsystem: Acer Incorporated [ALI] SiS900 PCI Fast Ethernet
            Kernel driver in use: sis900
            Kernel modules: sis900
00:06.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
            Subsystem: Acer Incorporated [ALI] PCI1510 PC card Cardbus Controller
            Kernel driver in use: yenta_cardbus
            Kernel modules: yenta_socket
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
            Subsystem: AMBIT Microsystem Corp. TravelMate 2410
            Kernel driver in use: b43-pci-bridge
            Kernel modules: ssb
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
            Kernel modules: amd64_edac_mod
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
            Kernel driver in use: k8temp
            Kernel modules: k8temp
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
            Subsystem: Acer Incorporated [ALI] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
            Kernel modules: sisfb
```

------------

```
lspci - k (live CD)

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
            Kernel driver in use: agpgart-amd64
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
            Kernel modules: shpchp
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] LPC Controller (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller
            Kernel driver in use: sis96x_smbus
            Kernel modules: i2c_sis96x
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller
            Subsystem: Acer Incorporated [ALI] 5513 IDE Controller
            Kernel driver in use: pata_sis
            Kernel modules: pata_acpi
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
            Subsystem: Acer Incorporated [ALI] AC'97 Modem Controller
            Kernel modules: snd_intel8x0m
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
            Subsystem: Acer Incorporated [ALI] SiS7012 AC'97 Sound Controller
            Kernel driver in use: snd_intel8x0
            Kernel modules: snd_intel8x0
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
            Subsystem: Acer Incorporated [ALI] USB 1.1 Controller
            Kernel driver in use: ohci-pci
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
            Subsystem: Acer Incorporated [ALI] USB 1.1 Controller
            Kernel driver in use: ohci-pci
00:03.2 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
            Subsystem: Acer Incorporated [ALI] USB 2.0 Controller
            Kernel driver in use: ehci-pci
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
            Subsystem: Acer Incorporated [ALI] SiS900 PCI Fast Ethernet
            Kernel driver in use: sis900
            Kernel modules: sis900
00:06.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
            Subsystem: Acer Incorporated [ALI] PCI1510 PC card Cardbus Controller
            Kernel driver in use: yenta_cardbus
            Kernel modules: yenta_socket
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
            Subsystem: AMBIT Microsystem Corp. TravelMate 2410
            Kernel driver in use: b43-pci-bridge
            Kernel modules: ssb
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
            Kernel modules: amd64_edac_mod
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
            Kernel driver in use: k8temp
            Kernel modules: k8temp
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
            Subsystem: Acer Incorporated [ALI] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
            Kernel modules: sisfb
```

---

### Post by mörgæs on 2016-05-21
For the 760 it might be a good idea to try 14.04 as described here: [http://ubuntuforums.org/showthread.php?t=2252413](http://ubuntuforums.org/showthread.php?t=2252413)

This is one of the few examples where I suggest going back to old software.

---

### Post by lubuntalb on 2016-05-23
> **mörgæs said:**
> For the 760 it might be a good idea to try 14.04 as described here: [http://ubuntuforums.org/showthread.php?t=2252413](http://ubuntuforums.org/showthread.php?t=2252413)

This is one of the few examples where I suggest going back to old software.

Thank you for your answer and your connected posts (with a lot of interesting commands).
I will try to find a solution with the 16.04 version for a couple of weaks, and if I don't succed I'll come back to 14.04!!

---

### Post by mörgæs on 2016-05-23
Good, please post the results if you find a solution for 16.04 so we can add that to the thread.

---

### Post by lubuntalb on 2016-07-25
I finally decided to install the 14.04 version but max resolution is always [COLOR=#000000]640 x 480[/COLOR] :(.

---

### Post by Neill_R on 2016-07-25
I would like to report that on several computers that are capable of run Live CD try before you Install for version 14.04(.4) that on 16.04 and now 16.04(.1) the graphics renders the feature totally unworkable.

Also I have waited to see the release of 16.04.1 expecting that here on my 14.04 machine i would be informed of the new LTS upgrade. However although my software IS UP TO DATE. only by setting Notiffy Me of new Ubuntu version to For any new version rather that to LTS do i get offered a new version of 15.10.

```

neill@ubuntu-server:~$ do-release-upgrade -c
Checking for a new Ubuntu release
New release '15.10' available.
Run 'do-release-upgrade' to upgrade to it.
neill@ubuntu-server:~$ 

```

have they overlooked the 16.04 for LTS or is something else going on

---

### Post by lubuntalb on 2016-07-25
I finally decided to install the 14.04 version but max resolution is always [COLOR=#000000]640 x 480[/COLOR] :(.
But... :-)

On the following forum I tried again the suggested commands that didn't work with the 16.04, and now resolution is OK!!!
[https://forum.ubuntu-fr.org/viewtopic.php?pid=21522944#p21522944](https://forum.ubuntu-fr.org/viewtopic.php?pid=21522944#p21522944)

Firstable, please verify that you are in the same situation:

```


lspci -nnk | awk '/\[03[0-9]+\]/,/Kernel driver/'
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330]
    Subsystem: Acer Incorporated [ALI] Device [1025:0083]

```

Then try the following commands:

```

sudo apt-cache search sis | grep xorg


sudo apt-get install xserver-xorg-video-sis

```


If **sudo apt-get install xserver-xorg-video-sis**
returns

xserver-xorg-video-sis : Dépend: xorg-video-abi-15
                                 Dépend: xserver-xorg-core (>= 2:1.14.99.902)

install the dependences:

```

sudo apt-get install xorg-video-abi-15
sudo apt-get install xserver-xorg-core
```

then repeat the command.

N.-B.:
I forgot to use the command: sudo apt-cache search sis | grep xorgMy Lubuntu don't want to shut down (I have to press ON/OFF button for 5 sec.)... But it's another problem for another day ;-) (I am a newbie!!!)

I hope that the problem will be solved with 16.04 version. Please post any good news :)

Neill_R... I just read your post now!!!

---

