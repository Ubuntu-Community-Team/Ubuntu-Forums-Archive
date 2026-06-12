---
title: "USB Support didn't install, need post install fix."
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by WolfmanK on 2007-01-11
I just installed 6.10 i386 verion off the alternat install CD.  For some reason it didn't pick up the USB chipset, as I can't get anything to work using either the USB or the Firewire ports.  
[B]
How do I fix/enable this post install?[/B]

System Info:
AMD 64 3200+
1.5GB RAM
160GB Hard Drive
nVidia 7300GS Graphics Card

History:
This machine was running 6.06 i386 version, no problems (usb/firewire worked)
I upgraded it to 6.10 AMD 64 version, no problems (usb/firewire worked)
I briefly tried OpenSuse on this machinee (usb/firewire worked) but didn't like it.
Now I reinstalled ubuntu but used i386 for better driver support, used the alt install cd because ther regular install cd doesn't detect proper monitor resolution and network settings on this system.

Thanks in advance for the help.

---

### Post by computergroove on 2007-01-11
well I see a few options.

1. (pretty much guaranteed to work) reinstall just like you did before. Install 6.06 and upgrade to 6.10. Lets try to avoid this one. 

2. You could get the 6.10 and modify the display settings (kind of a pain in the butt) and reinstall with the new settings.

3. Boot with the live cd and see if the usb works in the live environment and (this is the part I dont know about) find the configured file that is making the usb work and copy it to the new installation location. 

Wish I could be of more help. What kind of chipset does your motherboard have?

---

### Post by WolfmanK on 2007-01-11
Well I'm attempting to do this without a reinstall.  Eveything else in the system works fine so I'd rather just keep this one.

As far as finding the file that makes the USB work, if I knew what that was I would just start playing with it in this install, but yes USB does work with the live CD.

Its possable its a kernal issue, issue and I need to get into that, but I am not sure.  I am hoping to catch the attention of one of the real ubuntu geeks to let me know where to start poking around.

The Chipset is whatever comes with the ATI x200 on board graphics card.

---

### Post by computergroove on 2007-01-11
What is the model of your motherboard. ATI does not make a motherboard chipset for controlling the usb functions. Im looking for an answer like Nforce 3 chipset or SIS or VIA or ALI Chipset. If you geve the model of the motherboard I can look it up. You may just need to install the chipset drivers and it will work.

---

### Post by WolfmanK on 2007-01-12
Its an eMachines T6212 Machine.   Here are the specs.

AMD Athlon&#8482; 64 3200+ Processor (with AMD 64 technology)
(2GHz, , 512KB L2 cache)

Chipset:   ATI Radeon® Xpress 200
Memory: 	512MB DDR (2 × 256MB), 400MHz Dual Channel  (upgraded to 1.5gb)
Hard Drive: 	160GB HDD &#8211; 7200rpm, 2MB cache
Optical Drive: 	16x DVD±RW multi-format double layer; 48x CD-ROM
Media Reader: 	8-in-1 Media Reader
Secure Digital&#8482; (SD), Smart Media, Compact Flash, Micro Drive, Memory Stick®, Memory Stick PRO, Multimedia Card, USB 2.0
Video: 	ATI Radeon® Xpress 200 (PCI-Express® )128MB shared video memory  (using PCI-E nVidia 7300 GS)
Sound: 	6-channel Audio
Network: 	10/100Mbps built-in Ethernet
Ports/Other:  	7 USB 2.0 ports (2 in front; 4 in back; 1 in Media Reader), 1 IEEE 1394 port (1 in back), 1 Parallel, 2 PS/2, Audio-In & Out


So, yeah According to this it is an ATI chipset.

---

### Post by WolfmanK on 2007-01-15
Sorry for the bump, but this is still unresolved....

---

