---
title: "Random xserver restarts and freezes"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by ShishKabab on 2007-05-14
Hello,

I've recently bought a new second-hand computer.

During the installation of Kubuntu 7.04 Feisty Fawn I had problems with the computer that froze at random points. I could still move the mouse but the LEDs on the keyboard wouldn't respond and I could do anything. By now I solved the problem by disabling my Nvidia network card(I now only have my 3COM card enabled)

Now I'm experiencing random XServer restarts. The last one was when I tried to check my Yahoo! Mail with Firefox without any other application open.

There are also some random system freezes. My mouse disappears and the LEDs do not respond.

Could anyone help me out?

This is the output from lspci:
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1
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
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Contr
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Se
02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Etherne
03:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev)

Thnx in advance,
Vincent

---

### Post by ShishKabab on 2007-05-15
Just so you know. It was my graphical card that was probably damaged. I popped in a GeForce 2 and everything works just fine now.

---

