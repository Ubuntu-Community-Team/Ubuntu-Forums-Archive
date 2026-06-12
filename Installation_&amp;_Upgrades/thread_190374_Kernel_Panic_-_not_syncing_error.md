---
title: "Kernel Panic - not syncing error"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by Mikamura on 2006-06-06
While I'm fresh installing Ubuntu 6.06 into my PC. There're errors and the PC stall.

Error Message
-------------------------------------------
[4294805.586000] Call Trace:
[4294805.586000] apic_timer_interrupt (some hexadecimal)
[4294805.586000] do_page_fault (some hexadecimal)
[4294805.586000] die (some hexadecimal)

<various trace>

Kernel panic - not syncing: Fatal exception in interrupt. [4294805.586000]
--------------------------------------------

I experimented this problem by install the Ubuntu 5.10, and it finished in the first step. But it stall in second (graphic) step with the "Start hotplug ... (something I don't remember properly)".

I think Ubuntu has a problem with my PC's USB port or else. So if there're any method to cope with this problem, thanks in advance.:-D

My PC

Monitor: CRT 17"
Ram Amount: 1 GB (DDRRAM 512 MB x2)
HD: IDE 120 GB
Discreet Graphics Card: ATI ASUS A9250 128 MB
CPU: Intel Pentium 4 Prescott 2.66 GHz
MainBoard: ASRock 775i65GV INTEL (USB 2.0 Support)
Network Adaptor: Realtek RTL8139

---

### Post by Phasmagon on 2006-06-06
In my case (in breezy) it had something to do with ATI drivers. I had to blacklist something but I really can't remember what. I also had to change ati to vesa module in /etc/X11/xorg.conf, before i could continue with the setup. I had to use a recovery CD for that.

If you are not into searching and testing i would recommend downloading Ubuntu Live-CD and install from there, using safe graphics mode

This though might just be trivial in your case.

---

### Post by Mikamura on 2006-06-06
I've tried the Ubuntu 6.06 Live CD installation, but this error occur again. But thanks for help.

---

### Post by Mikamura on 2006-06-06
After experimenting with Ubuntu 6.06 & 5.10. There're errors when "Probing" the hardware (stall in safe mode, crash in normal mode). Are Ubuntu have any hardware compatibility issue? Thanks for more help in advance.

---

