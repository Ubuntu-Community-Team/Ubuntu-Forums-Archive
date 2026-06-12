---
title: "X crashes frequently, randomly, not on Live USB"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by Dr.Dixie on 2009-12-25
Ok, I've got a rather annoying problem (probably putting it a bit lightly).

Basically, within about five minutes of me logging on to a recently installed and updated installation of Ubuntu 9.10 (on my SATA drive), something happens that has roughly the effect that Ctrl+Alt+Backspace used to. This has happened multiple times, within no less than two installations of Ubuntu. I've always thought that reinstalling an operating system, supposing restarting it didn't fix the problem, would. However, in this case, it seems, reinstalling did no good at all. One possibility, I think, would be that I've installed something, or some things, that conflict either with my hardware (which is already annoyingly conflicted...I'll explain a bit later), or with another package.

The most recent instance, I think, was when I had opened a few tabs in Google Chrome (most recent dev build, as of sometime this morning), and had started loading all but one of the four. When I switched over to it, and pressed enter, within a couple seconds, at most, the screen went black and it returned me to the login screen. I'm fairly sure this has happened more than once on this most recent installation, and probably at least five times in the previous.

You can probably imagine I'm getting tired of this.

I had had a fantastic experience with 9.10 prior to this, but now I worry that the horror stories about 9.10 that have been going around might not be unjustified. This simply can't go on.

If you need any logs, the list of packages, or anything else, don't hesitate to ask. I'm more than happy, in this instance, to attempt to find a way to remedy this life-mutilating problem.

Oh, yes. My hardware. I've got a Dell Optiplex GX280, as you might have seen in my signature...and, yes. I've run a memory test on both of my two gigabytes for hours and hours a while ago, and for thirty minutes or so today (never found any errors at all).

The sticky part? I've got a Pentium 4 670. It's clocked at 3.8 GHz, and Dell, for some reason, has created a BIOS that only allows it to use 2.8 GHz of that. I don't entirely blame them for it...they're a company more for the consumer than the DIYer...

Anyway...when I ran the memory test, it said my memory was clocked at 266 MHz, less than half of what it should be (667 MHz).

Also, when I ran CPU-Z in windows, it came up with the memory clocked at 333 MHz. When I ran some super-exhaustive system info command (can't remember it) in Ubuntu, it showed the memory as DDR2 5300, what it is. It'd be nice to know that I'm only using less than half my memory bandwidth, meaning, with a new motherboard, that my system would be much, much faster, but, still...why all the different stats?

Oh! I forgot to say...the guy I bought this computer from upgraded the motherboard. I've looked all over the internet for info on this board, but, seriously, I can't find anything but prices.

Yikes, tangents.

I hope more than half of this helpful...

Merry Christmas,


!Dr.Dixie!

---

### Post by gsmanners on 2009-12-25
Could you post the output of the "lspci" terminal command?

---

### Post by Dr.Dixie on 2009-12-25
Here.

```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
```


!Dr.Dixie!

---

### Post by gsmanners on 2009-12-26
I can't think of anything except maybe the SATA is going bad or something like that. I don't know how likely Intel boards are to that kind of breakage, but I've personally seen that with an nForce board here. Sorry I can't help out more.

---

### Post by lamadog on 2010-01-18
I have the same exact problem, and I think I might have found the culprit to be Google Chrome. It started after switching to Chrome, and I have yet to experience it while Chrome is not running. I might be wrong, but that's my guess as of now.

Here is my output, if it's any good:

```
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)
02:00.0 SATA controller: JMicron Technology Corp. JMB360 AHCI Controller (rev 02)
03:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
03:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

```

---

