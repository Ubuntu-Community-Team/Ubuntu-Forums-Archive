---
title: "Halting ubuntu on Acer aspire 3680"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by emuzesto on 2007-12-02
I currently run Ubuntu Gutsy on an Acer Aspire 3680, running the 2.6.22-14-generic kernel. I have a problem which I can't find described anywhere else. The computer is frequently halting or freezing, which is irritating and impractical when viewing video, writing, listening to music, or generally sitting at the computer. I can remember having this problem since edgy, but can't remember which kernel. 

I suspect it of being a grafics related problem, but I'm not really sure as I don't use pure CLI much. I've tried to change resolution, turn off proprietary video drivers etc. but so far without success.

---

### Post by Pumalite on 2007-12-02
??

 Dynamic Video Memory Technology 3.0
Graphics Processor / Vendor:
	
Intel GMA 950 

You might be running out of memory at times. What size is your /swap?

---

### Post by emuzesto on 2007-12-02
My swap is 502 mb and seems to be quite steady on around 33 mb used, but the cpu load seems to shoot suddenly at 100% usage during these halts. I'm not really sure what graphic card I got, but I think it is an Intel of some sort. The CPU is an Intel Celeron 1,6 GHz.

---

### Post by Pumalite on 2007-12-02
Your video card is what I posted in post#2 and it uses quite a bit of your ram, so for intensive tasks (like decompressing a movie) you might run short.

---

### Post by emuzesto on 2007-12-02
I understand. This is however not a problem just when doing that kind of higher-intencity tasks, but also when doing ordinary things like writing and browsing the web.

---

### Post by Pumalite on 2007-12-02
I'd reinstall then.

---

### Post by emuzesto on 2008-05-05
I still have these problems with Hardy. In addition I get total system freezes from time to time.

---

### Post by skylinedna on 2008-07-20
I get these same problems as well on acer 3680 same specs as above. i notice its like the hardrive pauses before anything will work. startup is real slow as well. Any ideas?

---

### Post by zipperback on 2008-07-20
> **emuzesto said:**
> I still have these problems with Hardy. In addition I get total system freezes from time to time.



Please open a terminal window and provide the output from the following command.

```

lspci

```

Lets see if we can get you up and running properly.

I have an Acer Aspire 5050-3371 Laptop and it seems to be extremely stable with Ubuntu Hardy.

- zipperback
:popcorn:

---

### Post by emuzesto on 2008-07-20
Here's the lspci output:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

---

