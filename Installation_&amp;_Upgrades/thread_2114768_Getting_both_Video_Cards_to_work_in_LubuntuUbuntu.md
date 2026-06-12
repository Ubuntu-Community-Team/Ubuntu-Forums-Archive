---
title: "Getting both Video Cards to work in Lubuntu/Ubuntu"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by matthew1429 on 2013-02-11
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
[COLOR="Red"]**00:01.0 PCI bridge: Intel Corporation 82865G/PE/P AGP Bridge (rev 02)**[/COLOR]
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
[COLOR="red"]**01:00.0 VGA compatible controller: NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1)**[/COLOR]

I'm speaking to you on a fresh install of an older computer that has built in Intel graphics (enabled at bios) and the additional nvideo video card.  

the "additional drivers" screen doesn't list anything proprietary.  I've been told that Intel drivers are built in, can you tell me how to get both cards working at the same time?  My nvidia works but I don't have an output from my intle.

Thanks

---

### Post by QIII on 2013-02-11
Is that a desktop?

---

### Post by matthew1429 on 2013-02-11
it is, a dell optiplex gx270 and as I stated I've thrown the extra nvidia in

---

### Post by QIII on 2013-02-11
It is unlikely that you can use both GPUs simultaneously.  Does the BIOS allow you to switch between the two?

---

### Post by matthew1429 on 2013-02-11
not good news, would i be able to do this if I slapped another card in?

---

### Post by QIII on 2013-02-11
You will have to see if the BIOS allows both onboard and dedicated to be used at the same time.

Dell is a bit of an odd bird sometimes.   

Even other motherboard OEMs have some models that will allow it and some that won't.

---

### Post by matthew1429 on 2013-02-11
i did slap this in:  
02:07.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Rage 128 PP/PRO TMDS [Xpert 128]

so now I'm using the 2nd card and don't have a display showing for the rage 128, would I still hav ea bios issue?

---

### Post by QIII on 2013-02-11
So you now have the NVIDIA dedicated card and the ATI card both?

---

### Post by matthew1429 on 2013-02-11
i do - and the "monitor" option doesn't see the 2nd monitor

---

### Post by matthew1429 on 2013-02-11
as an fyi, i do have r128 installed, i did : sudo apt-get install xserver-xorg-video-r128 and this was the output "Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-r128 is already the newest version.
xserver-xorg-video-r128 set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic linux-headers-3.5.0-18 linux-headers-3.5.0-18-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 53 not upgraded.

---

### Post by QIII on 2013-02-11
Mixing NVIDIA and AMD/ATi cards spells bigger trouble still.

It might be worth seeing if just the ATi card will work, but that is a very old card.

Again, this is probably something you will have to check in your BIOS.

---

### Post by Mark Phelps on 2013-02-11
> **matthew1429 said:**
> i did slap this in:  
02:07.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Rage 128 PP/PRO TMDS [Xpert 128]

so now I'm using the 2nd card and don't have a display showing for the rage 128, would I still hav ea bios issue?

That ATI card is so old that ATI stopped producing drivers for it before Ubuntu 9x.  I doubt current drivers would work at all.

---

