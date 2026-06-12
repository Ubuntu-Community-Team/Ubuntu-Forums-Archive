---
title: "Dapper install disk impressions"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by Tiede on 2006-06-30
I did not know where to put this, so since this relates to the liveCD, I thought that this section is as good as it gets.
---

Although I was quite impressed with the new dapper Install Disc, I have however found some things that should be fixed in the edgy release:
When you select a language via F2 on bootup, it automatically selects a keyboard language, which in my case is a pain seeing as I prefer reading a French OS but only have a US keyboard layout (my laptop is US). A fix would be to prompt for the correct keyboard layout upon startup (as it is currently done in Mandriva Live), where the default could be us_english, but the other layouts would still be available.
My Synaptics touchpad is not working well by default. Side-scroll is disabled, so is tap-n'-hold drag, and therefore double-tap click... Futhermore, if I use the directional scrolls on my touchpad, they do not behave correctly: downward scroll became right-click, and the other three directions (up, left, and right) are all obsolete. I remember running in that problem before in dapper beta and know there is a fix for it, but apparently it wasn't included in the final release version of dapper. So, I had to go and manually edit my xorg.conf to include the Synaptics Touchpad Section as so:
> 
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

I hope it is not gonna be overlooked in edgy. BTW, I have an Acer Aspire 3003WLCi laptop.

Of course, my Broadcom 4318 wireless card is [b]*STILL*[b] not working... I have tried a quick ```
sudo modprobe -r bcm43xx
sudo modprobe bcm43xx --first-time
sudo modprobe bcm43xx --first-time[code] to make sure it is loaded, but it won't budge. It shows up in System->Administration->Networking, but it is listed as not active, and pressing the Activate button just gives me the  never-ending Activating eth1 pop-up window... I have checked my dmesg for anything on bcm, and here's the output:
[code]
[4294745.476000] bcm43xx driver
[4294746.628000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4294746.640000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4294940.935000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4294946.196000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4295263.017000] bcm43xx driver
[4295263.162000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4295263.178000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4295321.846000] bcm43xx driver
[4295321.987000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4295322.003000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4295341.428000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4295341.444000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

```
Apparently, it is something wrong with microcode5.fw which looks odd to me, since i do not have bcm43xx-fwcutter installed (this is the install disk)... I do remember running in the same problem in dapper beta two months ago when I did have bcm43xx-fwcutter installed and using either the bcmwl5(a).sys/inf present on my laptop, the one from the official Acer US website, and the one available here on the forums... With ALL of'em I always saw that microcode5.fw error popping up.

Another issue is the resolution, which is only 1024*768 while my PC's default is 1280*800, although I am sure once installed, I can edit my xorg.conf to include 1280*800(Editing the live version's xorg.conf and killing X doesn't seem to be enough)... I just think that it may not register well with someone whose never used linux before to see his resolution stuck at a number lower than the one he's used to.

I wanna say though that I was quite impressed with dapper (finally) harvesting the right DSDT table for my laptop, with my battery status now properly detected. Also impressing was the fact that the OS detected a new Ubuntu cd when I inserted it in my CD drive and asked me if I wished to open Synaptic and include that cd in my repos list...


--
PS:For the sake of being informational, here's my lspci:
```

 ubuntu@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter
ubuntu@ubuntu:~$

```


--
Note: in order to get my card working, I have tried using the updated (wl_apsta.o) driver given in the Broadcom Howto on my dapper beta, and it failed like so:
```

marc@tuxed:~$ bcm43xx-fwcutter /home/marc/wl_apsta.o
Sorry, the input file is either wrong or not supported by fwcutter.
I can't find the MD5sum 88ee65d8d68505620b58c9fd2785ddf3 :(
marc@tuxed:~$

```
I know my card is a Air Force One 4318, and it is said that this is the card with the most failed install attempts, but I do not think it should have failed so soon... Am I missing something?

Thanks every one for listening in. Any comment appreciated.

---

### Post by timmir on 2006-07-09
I'm having the same problems.  I just bought a Gateway MX6441.  It's basically the same as yours, but with ATI instead of SIS.  Here's my hardware listing
```

0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 Fast Ethernet Controller (rev 10)
0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:05:09.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
0000:06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

```
I've installed Dapper twice and I seem to remember that the wireless worked on the first sctivate both installs.  I just installed the fwcutter program and it ran, but on later dates =, when trying to activate the wireless it had the neverending loop loke yours.  I've tried using both the bcm43xx and ndiswrapper (b;acklisting the one I'm not using) and nothing works.  I'm currently on an realtek8180l pcmcia card.  I would rather use the internal card if possible.  My realtek(Netgear) card is only 802.11b.

p.s. as a site note, my mouse won't click and drag using the button.  I have to double-tap and drag instead.

---

### Post by serkanp on 2007-08-15
hi guys, 
i have hp pavillon dv5176 notebook and same configuration as yours. 
i also get bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed message. 
but strangely, i installed fedora core 7, ubuntu 7 , kubuntu etc.. 
all have the same problem.. 
but .. i used a different linux distribution named Pardus 2007.2 , it automatically detected my wireless card and installed it. also i installed beryl on it.. 
but my wireless not works on ubuntu and fedora... :)

---

