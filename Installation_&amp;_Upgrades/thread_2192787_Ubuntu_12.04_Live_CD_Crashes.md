---
title: "Ubuntu 12.04 Live CD Crashes"
date: 2013-12-09
forum: Installation &amp; Upgrades
---

### Post by hookzilla on 2013-12-09
Unusual Problem.  I cannot get ther Ubuntu 12.04 live cd to run on my Acern Aspire 3003 WLCi laptop.  Mint 13 also fails.  The live CD starts to load, but crashes with kernel panic.  These same cds work fine on a Dell 600M laptop and several desktops.  Puppy and other Linux based utilities load fine.  Any suggestions will be appreciated.
Thanks,

My system:
Acer Aspire 3003WLCi
CPU - AMD Mobile Sempron 3000+
MOBO - Acer Lucano M
BIOS - Phoenix NoteBIOS 4.o
Video - SiS M760GX 128 mb  1280x800
LAN - SiS 900 PCI Fast Ethernet
WIFI - Broadcom BCM43XX
Audio - Realtek '97
Pad - Synaptics PS/2 Toufhpad
USB - SiS 7001 PCI to USB Host
Optical - DVD / CDRW
DDR RAM - 2GB


On further investigation, the crash seems to be related to the wifi chip - BCM4306.  I've found ways to blacklist the included B43driver, but only if I get something installed.  Still stumped.

---

### Post by ian-weisser on 2013-12-09
Dell 600M generally uses a Pentium-family CPU. Aspire uses an AMD Sempron.
Those seem like different architectures to me.
You need the version of Ubuntu appropriate for each architecture.

---

### Post by Bucky Ball on 2013-12-09
Could be a problem with the SiS graphics. Try this:

When you get to the window after boot that says 'Try Ubuntu' 'Install Ubuntu' etc. hit F6 and choose 'nomodset'. Proceed. Any luck?

---

### Post by fantab on 2013-12-10
How much RAM is there on the machine? If I remember correctly this model came with less than 1gig memory...
You should probably try [LUBUNTU, or consider lubuntu alternative install or minimal...]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu")

---

### Post by mörgæs on 2013-12-10
> **ian-weisser said:**
> Dell 600M generally uses a Pentium-family CPU. Aspire uses an AMD Sempron.
Those seem like different architectures to me.
You need the version of Ubuntu appropriate for each architecture.

No, whether the processor is AMD or Intel does not matter. The only thing to consider is 32/64 bit, and if that were the problem you would have seen an explicit message about this.

As posted above the SIS graphics is likely the cause.

---

### Post by hookzilla on 2013-12-10
"nomodset"  had no effect

---

### Post by hookzilla on 2013-12-10
machine has 2 gb ram

---

### Post by hookzilla on 2013-12-10
OK, I found a suggestion ([http://ubuntuforums.org/showthread.php?t=1966655](http://ubuntuforums.org/showthread.php?t=1966655))  and finally was able to add " b43.blacklist=yes " to the boot instructions.  This allowed me to load the live cd.  I haven't tried an actual install as yet.

Thanks to all for the suggestions.

---

### Post by Topsiho on 2013-12-11
Glad problem is solved.

Just this:

hit F6 and choose 'nomodset'. 
nomodset had no effect

This was a typo, it should have been: nomodeset

I add this for the readers of this topic, to be sure, and sorry to Bucky Ball :)

Topsiho

---

### Post by Bucky Ball on 2013-12-11
> **Topsiho said:**
> 

This was a typo, it should have been: nomodeset



Nope, you had it right. It is 'nomodset'. ;)

---

