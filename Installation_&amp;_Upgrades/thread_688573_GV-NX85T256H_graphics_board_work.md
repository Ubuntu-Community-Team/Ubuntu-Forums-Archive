---
title: "GV-NX85T256H graphics board work??"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by lightkeeper on 2008-02-05
Has anyone been successful installinig 7.10 with the Gigabyte GV-NX85T256H GeForce 8500 Graphics Accelerator?

I am ubuntu newbie - have built new pc and try to boot up with install CD.  Starts out ok - Got the splash screen (I guess they call it) with the bar moving back and forth - that lasted maby 4 min and the the bar started to fill up left to right -- after that it went to the blue screen - no graphics.

Computers here are on a KVM box. When I switch monitor, keyboad and mouse to windows box and then back to ubuntu box for just a second or so after the switch the monitor does show that I am at a ubuntu desktop with an istall icon, menus at the top of screen etc. and then the screen goes blue. (Yes same thing if I go direct eliminating the KVM switch.)

Seems like something is amis with the graphics driver or something.  I have upated the mobo to latest bios 1302 downloaded from ASUS.

I am stuck and could use suggestions on how to solve this problem and move forward.

Thanks in Advance.

Lightkeeper

Hardware:
Motherboard Asus M2N-SLI Deluxe Green nVIDIA Socket Am2 ATX 

Processor AMD Athlon 64 X2 Dual-Core 6000+ 3.0 GHz 

Memory 8096MB Dual Channel 4096MB PC6400 DDR2 800MHz Memory

Video Card - GIGABYTE GV-NX85T256H GeForce 8500GT 256MB 128-bit GDDR2 PCI Express x16 

Hard Drive - HITACHI Deskstar 7K1000 HDS721010KLA330 (0A34915) 1TB 7200 RPM 32MB Cache SATA 3.0Gb/s 

DVD - SAMSUNG SH203N SATA

---

### Post by lightkeeper on 2008-02-05
Finally got the screen problem solved.  By switching back and forth between the windows box and the ubuntu box and working in the 1 sec window I was able to move to system>admin>screens&graphics and change the ubuntu resolution from an unsupported 1280x768 which it had defaulted to to a 1024x768 which works!

I had tried setting screen to 1024x768 on the initial screen which come up after you boot with the install CD but it does not work.

---

