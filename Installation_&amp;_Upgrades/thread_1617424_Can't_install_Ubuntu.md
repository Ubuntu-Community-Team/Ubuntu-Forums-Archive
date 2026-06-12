---
title: "Can't install Ubuntu"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by garyedwardjohnston on 2010-11-09
Ive been using Ubuntu for about 5 years steady and been very happy until recently.

I purchased a new computer and have been having numerous problems...please help.

Firstly, trying to install gave me the error "Unable to find a medium containing a live file system".  I gave up trying to fix this and simply disabled my Blu-Ray / DVD writer in the BIOS.  This at least allowed me to install Ubuntu 10.10.

I can live without the optical drive for a while but not without wireless Internet.

I have tried everything...the problem seems weird because the driver appears to be installed fine and one lucky attempt out of 100 I could actually see networks but couldn't connect to them.

If I can get wireless to work that would be great.  If I could get the Blu-Ray to work too that would be awesome:)

My PC is [here]("http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=4224630").

Thanks for your help.

PS  Because Ubuntu wouldn't install I decided to give Windows 7 a try (it came pre-installed) AND HATED IT.  After only 1 month I am desperate to come back to Ubuntu.  Thanks

---

### Post by Chazz44able on 2010-11-09
If I were you, I would revert to Ubuntu 10.04, at the moment Maverick is still so new that it may well come up with some teething issues

---

### Post by ajgreeny on 2010-11-09
There is no indication in the spec you linked to of the wireless chip in the machine.

If you can get the ubuntu install running, even as a live CD/USB please let's see the output from ```
lspci
``` or if you install lshw to the install or the live OS, the output from ```
sudo lshw -C network
```which will give some clue about driver requirements.

---

### Post by garyedwardjohnston on 2010-11-09
lspci

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 04)

```

sudo lshw -C network

```
  *-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 70:f1:a1:de:e6:5c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-22-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fe7f0000-fe7fffff

```

btw thx :)

---

### Post by searchfgold6789 on 2010-11-09
Check out the [_**wireless troubleshooting guide**_]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide").
I recommend sticking with the LTS for another few months :\
If you overwrote your other install It can easily be recovered with testdisk.

---

### Post by nbala.iyer on 2010-11-09
hi , you may need to enable the WiFi using the Wake command .. type this in konsole terminal ..

>
[I]qdbus --system org.freedesktop.NetworkManager \
/org/freedesktop/NetworkManager org.freedesktop.NetworkManager.wake
[/I]<

---

### Post by garyedwardjohnston on 2010-11-09
Interestingly enough I took it downstairs and plugged it in and a wired connection didn't work either.

Giving up on Ubuntu, I tried to install Windows 7 and it said that I needed a drivers disc, which of course HP didn't provide.

So now I have $1,000 computer that is a paper weight.

I'm now gonna try other Linux distributions to see if they work.

---

### Post by ajgreeny on 2010-11-09
Rather than go through all this myself and try to help you that way, I will just offer you this link to a googlubuntu search on RT3090 which found plenty of posts.

I hope this may give you something which helps, but if you choose to look at other distros, good luck.
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=RT3090&as_qdr=all&sa=Google+Search&lang=en#783](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=RT3090&as_qdr=all&sa=Google+Search&lang=en#783)

---

### Post by nbala.iyer on 2010-11-11
hi , the autoeth may not be enabled , hence the network settings in etc folder is quite relevant.... try nosing around a bit and you will be able to make it fully functional :) ..

---

