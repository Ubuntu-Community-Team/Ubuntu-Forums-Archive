---
title: "NOT SOLVED: Waiting for sound system to respond"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by lelandnielsen on 2011-02-12
I've spend the morning poking through forums and attempting every fix suggested and still no luck on this one:

At first i didn't have any sound.  But now I do (and I'm not sure which solution fixed the problem).  But I still don't have a Sound icon in my menu bar and when I attempt to access my Sound Preferences I receive the message: "Waiting for sound system to respond" which display indefinitely.  

I tried:
- removing and reinstalling alsa packages
- deleting the .pulse folder
- adding a Pulseadio daemon

I'm running 10.04 LTS 64bit.  

Help?

---

### Post by gordintoronto on 2011-02-12
For the sound icon: right-click on the top panel, select "add to panel." Select the "indicator applet."

What sound hardware is on your computer? The command lspci should display it.

What do you see when you run System/Preferences/Sound?

---

### Post by lelandnielsen on 2011-02-12
When I run System/Preferences/Sound I receive an alert window that reads:
"Waiting for sound system to respond."
Which waits indefinitely.

Indicator applet adds a Mail icon.  

Here's my lspci output:
```

00:00.0 Host bridge: ATI Technologies Inc RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D)
00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation G96 [Quadro FX 580] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
05:05.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)


```

---

### Post by gordintoronto on 2011-02-12
You have two audio devices:
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
05:05.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

I assume one is on the motherboard, and the other is an add-on card? Can you go into the BIOS settings and disable the on-board audio, or physically remove the add-on card? It sounds like they are conflicting.

---

### Post by lelandnielsen on 2011-02-12
I disabled the onboard soundcard through BIOS and routed audio to the ICE1712, but I still cannot access Sound Preferences.

Thoughts?

And thanks!

---

### Post by gordintoronto on 2011-02-13
I assume there is some benefit to the Envy24 beyond a regular sound card? If it were me, I would just remove it and use the on-board sound. 

Quite a few years ago I bought a custom-built PC, and specified a high-end sound card. These days, I'm quite happy with on-board audio.

---

### Post by moongya on 2011-03-13
sir,
I too have everything but fail to get sound after i moved my home folder. help

---

