---
title: "help with fglrx stuff"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jfelts on 2008-10-24
Sorry i'm kinda newb, but trying my best.

I had 8.04 running with fglrx and a mobile ATI radeon 9600. Did the update to 8.10, and now it cannot detect my graphics card.

I completely removed fglrx, updated , and reinstalled through restricted drivers. I get the same error. (EE) no devices detected.

I hear of everyone having success with the new driver, why isnt it working for me? I'm attaching my xorg.log file.

---

### Post by whsutton on 2008-10-25
Sorry my friend but as far I know that driver "8.10" only works up to Xorg 7.3. Intrepid has Xorg 7.4. Soooo you are pretty much in limbo like most of us until ATi or Nvidia Release driver's for Legacy video cards.

But altogether I could be wrong?

---

### Post by jfelts on 2008-10-25
Thing is, fglrx in intrpid is supposed to have an updated driver with support for 7.4 that isnt even available from ATI yet. Its working for alot of people, just not for me. I wonder if they dropped support for 9xxx cards?

---

### Post by sdowney717 on 2008-10-25
interesting!
I have a system with a 9600 se 64 mb ati card and it gives me the same error.
FWIW, this system with an older nvidia mx4000 works fine.

What is your intel chipset, mine is 82875.

In another system, different intel chipset, I have an x1300 and fglrx works

why not submit a bug report

---

### Post by natros on 2008-10-25
same problem here with 9700, i don't know what to do, i'm running in low graphics mode :(

i hope it gets fixed soon otherwise i'm going back to 8.04

---

### Post by sdowney717 on 2008-10-25
a lot of people will want this fixed since a lot of older systems can run ubuntu. They cant run or upgrade to vista.

---

### Post by grotto on 2008-10-25
I couldn't get my 9700 working with fglrx, either. There wasn't much in my error log. Just an error saying that the hardware could not be detected.

---

### Post by jfelts on 2008-10-25
be nice to know if anyone has a 9xxx card working in 7.4 with fglrx. surprised the dev's didnt run into this considering its the most common ATI chip, specially in laptops.

---

### Post by jfelts on 2008-10-29
i was surprised to not see a bug report submitted since so many have been posting here with problems on it, so I put one in.

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/290692](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/290692)

---

### Post by gsaggior on 2008-10-29
Also on my Dell, with a Radeon Mobility 7500, just installed with Intrepid RC the video card does not work but with the standard VGA drivers. Gnome on XOrg runs at 640x480 pixels only.... 

Linux xxx 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

sudo lspci -v
...
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
	Subsystem: Dell Device 012a
	Flags: bus master, VGA palette snoop, stepping, 66MHz, medium   devsel, latency 32, IRQ 11
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at c000 [size=256]
	Memory at fcff0000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at fc000000 [disabled] [size=128K]
	Capabilities: [58] AGP version 2.0
	Capabilities: [50] Power Management version 2
	Kernel modules: radeonfb


:guitar::confused::confused::confused::confused::confused:

---

### Post by Bo Rosén on 2008-10-29
As mentioned in another thread (by me) I have the same problem with a 9500 pro. The opensource driver is nice, but tv-out (which I want) seems to be disabled on it.

Added a "me too" to the bug report.

---

