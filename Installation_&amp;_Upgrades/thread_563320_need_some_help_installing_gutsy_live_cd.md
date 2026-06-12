---
title: "need some help installing gutsy live cd"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by pulsifier on 2007-09-29
ok, so let me start with what i've tried.  a direct upgrade through the update manager which 

resulted in a 4hr d/l and 40min install only to have the system hang while loading.  a d/l of the 

iso to burn a cd image only to have that hang while loading as well.  Feisty did the same until i

used the boot option: pnpacpi=off noacpi nolacpi.  i tried that with the gutsy live cd as well as 

other boot options but to no avail.  i'm sure this is all a result of using SiS hardware, pure 

garbage.  anyway, if there is anything anyone can suggest i will appreciate it immensely, i'll try 

anything.  thnx

---

### Post by pulsifier on 2007-09-30
anyone?

---

### Post by Pumalite on 2007-09-30
Post your specs.

---

### Post by pulsifier on 2007-09-30
sure thing...

here's th lspci output:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] Unknown device 0671
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:09.0 FLASH memory: ENE Technology Inc Unknown device 0730
00:09.1 Generic system peripheral [0805]: ENE Technology Inc Unknown device 0750
00:09.3 FLASH memory: ENE Technology Inc Unknown device 0751
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

generic specs:  core 2, 2g RAM, SiS m671 graphics card.

thanks for the reply, if you can make any sense of it that would be spectacular.  if there's any futher info...

---

### Post by Pumalite on 2007-09-30
If you want Gutsy (it's in testing; stable out October 18th I think), save your data and do a fresh install with Alternate CD.

---

### Post by pulsifier on 2007-09-30
alright, i'll do that.  is the alternate CD not too complicated to install (for a moron like myself anyway)?

---

### Post by Pumalite on 2007-09-30
It's text based, but easier to install. It gives you more control over what happens and avoids graphics issues.

---

### Post by pulsifier on 2007-10-02
th alternate cd does not work either, looks like i'm SOOL until SiS gets their **** together and releases some linux drivers

---

