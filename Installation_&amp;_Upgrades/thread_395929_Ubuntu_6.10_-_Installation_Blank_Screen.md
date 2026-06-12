---
title: "Ubuntu 6.10 - Installation Blank Screen"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by fsm39 on 2007-03-28
Hello everyone, I'm new to Ubuntu, and Linux, and right off the start I'm having a bit of difficulty.

I'm attempting to install 6.10 on SATA HD, running on a sil3112 controller, with and without any partitions. The CD was burned at 4x, the md5 checked out, and the built in CD check after it has booted checks out OK. When I select Install I get the logo and loading bar, and after it's progressed to 100% the screen goes blank, and for a moment I see a cursor, and then nothing but black. The CD-ROM is still spinning, along with mild hard drive access noise, but nothing has happened in over 30 minutes. Pressing the system power button results a system beep, followed by the CD ejecting - which seems a little weird to me!

With Win 2000/XP I had to preload the sil3112 driver, or include it on a slipstreamed CD, but I was under the impression that Ubuntu 6.10 already contained it, or a generic SATA driver. I'm also assuming that the SATA controller has anything to do with it... Did I miss something right off the start, or is something messed up?

Thanks in advance for any feedback:)

---

### Post by fsm39 on 2007-03-29
Alright, I've done some looking around and it appears I'm not the only person to run into this problem, 6.10 or the 7.04 beta. Recommendations are usually
```

vga=771
noapic nolapic

```

Neither has made any difference.

NF7-S 2.0 - AXP 3200+ - 1GB
R9800 Pro
SB Audigy 2 ZS
WD Raptor

Being a newcomer I'm pretty stumped, any input would be appreciated!

---

### Post by ToeCutter2112 on 2007-03-29
Hmm, my issue sounds similiar.

I get right up the "final" progress bar and screen goes blank with a flashing cursor, then a meesage saying "Cannot Display This Mode" appears on my LCD.

I'm running a pretty vanilla config:

Intel Celeron
768MB RAM
Intel 845 Chipset (Intel Thrasher Mainboard)
Embedded IDE/NIC/Graphics

It seems like the display goes out of sync, despite trying every different resolution available on the splash screen (and the VGA=711 etc switch)

Any thoughts out there?

---

