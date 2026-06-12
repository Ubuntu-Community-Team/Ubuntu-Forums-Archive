---
title: "flickering screen in ubuntu 10.4"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by yummygirl on 2010-05-03
Hi everyone

First of all, I'm new in this, I love ubuntu , but I'm kind of new in the ubuntu world.

I have just updated my Ubuntu from 9.10 to 10.4.
But after restarting it showed flickering screen.

I can see videos, navigate in the web , everything, but my screen is so annoying with this flickering.

I try several times restarting, but nothing happens...so I go to sleep, today in the morning I woke up my laptop and the flickering is less annoying but still there.

What things do I need to do ?

I don't know what graphic card I have, but I follow the instructions and show up this!

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 718b
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
04:06.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
04:06.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
04:06.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
04:06.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
04:06.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
04:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)


Sorry , I'm new , but I really like ubuntu :P someone can help me? 

thanks!

---

### Post by quixote on 2010-05-04
You have ATI graphics (line 01.00 in your list).  They make excellent graphics cards, but don't usually work much with the open source community, so an ATI setup often requires a bit of tweaking to get it to work right.  The issue you're having sounds like the system is using a less-than-ideal driver.

To find out which ATI, exactly, open a terminal (Applications > Accessories > Terminal) and type ```
lspci | grep 'VGA'          *(Case sensitive!)* 
``` That'll give you the model.  Then you can search for that specific model and lucid. e.g. "ATI Radeon 7500 Lucid" (without quotes).  You may find people with similar problems and, even better, solutions. :D

Just some non-specific suggestions: open Synaptic (System > Administration > Synaptic), and in the search box at the top type ATI.  Not all the stuff that comes up needs to be installed.  As far as I know, the 'fglrx' driver tends to be used when there's an ATI card, but check around for advice from someone who knows. :-k

---

### Post by texaswriter on 2010-05-05
I have a dell n series laptop with an intel gma graphics card with the default Linux driver and it still does the flickering thing occasionally. 

Don't think it has anything to do with ATI [just a coincident].

---

### Post by JS36 on 2010-05-05
Try this.
> If you have an Intel Corporation Mobile 915GM/GMS/910GML card, your screen may flicker every 5-10 seconds. To prevent this:

* System -> Administration -> Advanced -> Service Manager
* Uncheck "Detect RANDR (monitor) changes" 
From [http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

---

### Post by janneman37 on 2010-05-07
same problem with ati x1400...

---

### Post by giri on 2010-05-07
I have the same problem with Lenovo T400 with Intel Corporation Mobile Integrated Graphics Controller. It worked great with Ubuntu 9.10.

How to access the service manager in gnome ?

---

### Post by janneman37 on 2010-05-08
This problem is solved here when i boot with option "nomodeset"

---

### Post by xcesarfrancox on 2010-05-08
Well I have the same problem with the open source driver:

```
lspci | grep 'VGA'
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]

```

A fresh install shows blue horizontal dashes going from left to right of my screen during boot, and less during normal use, since the beta versions, but installing the restricted driver stop the flickering, however, the restricted driver makes my laptop go hot and the Plymouth splash ugly, is there a workaround for this flickering under the open source driver?

---

### Post by djf_pingu on 2010-05-12
> **janneman37 said:**
> This problem is solved here when i boot with option "nomodeset"

Awesome.  This also works for me.

For anyone who is in the same boat, I have the amd64 distro with an Intel GM45 graphics setup.

---

### Post by iofanster on 2010-05-12
I have Intel Mobile PM965/GM965/GL960 Controller. And I fixed temporary by adding 
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection
Section "Module"
        Disable "dri"
EndSection
to xorg.conf
But! now only gnome works. Xfce that I used still blincking so that I have to reboot by a power key. The same if I try Alt-Ctrl-Fx to switch to command line.

---

### Post by texaswriter on 2010-05-12
How do you set "nomodset" as a boot option. 

Thanks

---

### Post by Catharsis on 2010-05-12
> **texaswriter said:**
> How do you set "nomodset" as a boot option. 

Thanks

Try it out first:
1) Hold down Shift while booting to enter grub.
2) Hit 'e' to edit. Add "nomodeset" after "quiet splash".
3) Ctrl+x to boot.

If that does indeed fix it, make it permanent by:
```
gksudo gedit /etc/default/grub
```
Add "nomodeset" to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
so it reads
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
Save and exit, and then run:
```
sudo update-grub
```

---

### Post by linuxalwaysbreakssuspend on 2010-05-23
Same problem with a laptop using ati x1200 internal card (unsupported crap from ATI).

nomodset _does not_ fix the problem, upgrading to 2.6.34 kernel reduces the frequency of flickers but problem persists and is very irritating.  Discovered the problem the moment the ubuntu logo came up with the new 10.04 LTS liveCD with almost constant flickering and I knew it was going to be another long ubuntu release cycle :mad:

Don't people test anymore, or is the new mentality, upload it and hope nobody notices?

---

### Post by texaswriter on 2010-05-23
Intel GMA: I think the nomodset worked, I haven't noticed the flickering screen in a week or so now. 

Thanks!!!!:guitar:

---

