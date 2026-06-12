---
title: "[SOLVED] Installing PCI cards after installing Ubuntu?"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by Fazz Munkle on 2008-05-26
I noticed a couple of times now that when I add in a new PCI card such as a USB card that Ubuntu apparently doesn't see it. But if I install it before I install Ubuntu it sees it. Is there something I'm not doing in Ubuntu to get a generic USB card to work after I've installed Ubuntu? I thought it would be as easy as installing the hardware and the drivers would automatically see the new card.

---

### Post by tamoneya on 2008-05-26
type ```
lspci
``` Post the results here and we will be able to tell you what is going on.

---

### Post by iaculallad on 2008-05-26
> **Fazz Munkle said:**
> I noticed a couple of times now that when I add in a new PCI card such as a USB card that Ubuntu apparently doesn't see it. But if I install it before I install Ubuntu it sees it. Is there something I'm not doing in Ubuntu to get a generic USB card to work after I've installed Ubuntu? I thought it would be as easy as installing the hardware and the drivers would automatically see the new card.

Does the **lspci** command display the device for you?

---

### Post by Fazz Munkle on 2008-05-26
Oo! I'll do that later tonight when I shut down (I have the PCI card out of the computer now) Thanks!

---

### Post by Fazz Munkle on 2008-05-27
Well, for some reason it decided to work this time. So I guess it's solved. If anybody's curious as to what I installed here's the listing from lspci:

Before:
```
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1) 
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1) 
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1) 
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1) 
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1) 
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1) 
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4) 
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2) 
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) 
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) 
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) 
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1) 
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2) 
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1) 
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) 
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) 
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3) 
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1) 
01:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13) 
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02) 
03:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4400] (rev a2)
```

After:
```
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
01:08.0 USB Controller: NEC Corporation USB (rev 41)
01:08.1 USB Controller: NEC Corporation USB (rev 41)
01:08.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
03:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4400] (rev a2)
```

I added the card temporarily because two of my hubs started behaving badly.

---

