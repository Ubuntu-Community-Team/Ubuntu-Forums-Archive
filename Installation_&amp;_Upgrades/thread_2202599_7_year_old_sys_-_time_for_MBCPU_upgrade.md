---
title: "7 year old sys - time for MB/CPU upgrade"
date: 2014-01-30
forum: Installation &amp; Upgrades
---

### Post by xigen on 2014-01-30
My trusty Ubuntu system is now 7 years old.   
$glances shows that my cpu runs at 90% plus during simple browsing.    
It feels like it is time to upgrade. 

With a $400.00 budget what can I get (Ubuntu compatible) while retaining as many of my existing parts as possible to save money?

What are some of your suggested approaches to the research?

...

Motherboard: M2N-E SLI  [www.asus.com/Motherboards/M2NE_SLI/](www.asus.com/Motherboards/M2NE_SLI/)
AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
4GB of DIMM 800 MHz (1.2 ns)
* a nice quiet cpu fan
** a good powersupply 500W
ATX formfactor Case. 
....

GeForce GTX 650/PCIe/SSE2/3DNOW!
Delta 66 Pci Sound Card
PIONEER DVD-RW DVR-112D(it's old)

...

250 GB HD for operating system and a little storage
2TB HD attached via usb2 for Storage.

:p

---

### Post by tgalati4 on 2014-01-30
10 RaspberryPI's at $40 each and wire them in a cluster.

It's hard to integrate really old parts with a new motherboard.  Old RAM sticks are much slower than newer sticks.  Old drives are slower.  You really waste the performance of a new motherboard with old parts.  Even the power supply is probably worn out if it is 7 years old.  Injecting too much power noise (due to an old power supply) can cause a new board to fail or act strange.

Save yourself some money and buy a gamer's machine that is a couple years old--gamers are constantly buying new systems--it is an addiction.  Use that to your advantage and put Ubuntu on someone's "so last year" computer.  Check craigslist or your local linux club.

---

### Post by Bucky Ball on 2014-01-30
** a good powersupply 500W

But if your hardware specs are it and that's all you've got in the box on that machine, you don't need 500W. Go for a PSU that is 80+ or 85+ energy efficient (they are labelled) and is from a reputable name. DON'T go for a generic silver box. They can kill everything inside your box with one unexpected pop, some smoke and flames and a few seconds. Plus, they are more efficient as heaters than PSUs as they generally run at <70% efficiency.

It is worth spending the money on a decent PSU. A good one will outlast the machine easily, keep you safe with the inbuilt safety switches, and use less energy.

You don't describe the machine you are running now, but my guess is that an SSD and more RAM may solve some of your issues. Please provide the hardware you are using on your current machine.

---

### Post by xigen on 2014-01-30
It actually might be 350.  My query $sudo dmidecode --type 39   did not give me a direct answer.   

I know what you mean about lame power supplies. 

Cheers,

---

### Post by Bucky Ball on 2014-01-30
I'm not sure what that command you mention is but if you looking for your machine specs, 'sudo lspci' should tell you everything.

---

### Post by xigen on 2014-01-30
Hmmm... I am not sure sudo lspci  gives power supply info on my system. 

 $sudo dmidecode --type 39 ... is .. tell me about the powersupply. 
[http://www.howtoforge.com/dmidecode-finding-out-hardware-details-without-opening-the-computer-case](http://www.howtoforge.com/dmidecode-finding-out-hardware-details-without-opening-the-computer-case)

meow@meow:~$ sudo lspci
[sudo] password for meow: 
00:00.0 Memory controller: NVIDIA Corporation CK804 Memory Controller (rev a4)
00:01.0 ISA bridge: NVIDIA Corporation CK804 ISA Bridge (rev f1)
00:01.1 SMBus: NVIDIA Corporation CK804 SMBus (rev a2)
00:02.0 USB controller: NVIDIA Corporation CK804 USB Controller (rev a2)
00:02.1 USB controller: NVIDIA Corporation CK804 USB Controller (rev a4)
00:06.0 IDE interface: NVIDIA Corporation CK804 IDE (rev f3)
00:07.0 IDE interface: NVIDIA Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: NVIDIA Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: NVIDIA Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: NVIDIA Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
01:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
01:07.0 Network controller: Ralink corp. RT3062 Wireless 802.11n 2T/2R
05:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GTX 650] (rev a1)
05:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)

---

### Post by Bucky Ball on 2014-01-30
No, not. My mistake. ;)

Odd, because from 'sudo dmidecode --type 39' I get:

```
# dmidecode 2.11
SMBIOS 2.6 present.

Handle 0x0012, DMI type 39, 22 bytes
System Power Supply
	Location: OEM_Define0
	Name: OEM_Define1
	Manufacturer: OEM_Define2
	Serial Number: OEM_Define3
	Asset Tag: OEM_Define4
	Model Part Number: OEM_Define5
	Revision: OEM_Define6
	Max Power Capacity: 75 W
	Status: Present, OK
	Type: Regulator
	Input Voltage Range Switching: Auto-switch
	Plugged: No
	Hot Replaceable: No
	Cooling Device Handle: 0x0010
```

By not a direct answer do you mean it didn't give you the make and model, as above?

(Neat command, never seen that one. Have been having a good look around. Thanks.)

---

### Post by mastablasta on 2014-01-30
why would that maschine run slow? with 4GB, dual core CPU and descent GPU?

i have Single core 3200+, 4 GB ram and radeon HD 3650 and haven't notice any slowness while browsing. only newer graphics intesnive games don't really run that well. more power is always better though... :-) so the only reaosn i am thinking 8but onyl thinking since i dont' have the money) of getting something newer is to play some newer games. but then agian ther eis plenty of those form 2005-2009 i haven't played. and those generaly work quite nice. maybe not at maxed out settings but still..

---

### Post by Bucky Ball on 2014-01-30
Yes, it is odd that there is 90% usage. You might save some money and try and solve that problem, because there's nothing wrong with '4GB, dual core CPU and descent GPU'. You have no need to upgrade unless you are intending to do something more resource intensive than what you're already doing. Better to try and work out the Firefox browsing problem on a new thread.

---

### Post by xigen on 2014-01-30
I think it is due to my browsing habits.   I do a lot of research on sites with Graphics/Ads/Flash and have 10+ tabs open at a time.

---

### Post by Bucky Ball on 2014-01-30
10? That's nothing! You could try installing adblock plus. 

I have an i3 dual-core CPU with 4Gb of RAM and regularly have 20+ tabs open AND three or four other apps going at the same time (and I mean perhaps five terminals open, three Libreoffice documents and VLC) and not really breaking a sweat ...

The partition is not almost full by any chance? Have a look in Gparted and check. Firefox plugins can also cause issues. I suggest removing them all, seeing if it makes a difference, then add back one at a time and test each.

---

