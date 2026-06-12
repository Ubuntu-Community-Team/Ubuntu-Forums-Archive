---
title: "Please Help with Lucid and Eclipse/Terminal"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by rfrey74 on 2010-07-17
First, I must apologize if this has already been posted, but I could not find anywhere that had my exact problem.  All similar problems and "fixes" have failed for me, so here is my problem. 

So, I use the tigris.org Galileo Eclipse to do Java work.  I am on a x86 64 machine using sun-java-6.  When I was using Hardy, everything was fine.  After upgrading to Lucid, my Eclipse Java text editor started to freeze after content assist.  I could click on the Navigation panel in Eclipse and then click back on the editor and continue with my coding.  However, this fix gets old really quickly.  Later, I started noticing the same problem if I had two terminals open at the same time.  I could be typing in one and then do some thing else which would take focus off the terminal, then I would go back to the original terminal and it would not register keyboard input.  I put focus on the second terminal by clicking on it, then click on the original terminal again and hey presto, I could type again in the original terminal.

Has anyone else experienced these problems and come up with a solution?  Just to stress, this does not happen in Hardy, only in Lucid.  I have another x86 64 desktop that is still running Hardy without these problems.  I would like to update it, but not if these problems are going to manifest on it too.

Here are the technical stats for my desk top.

lspci
> 00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
01:05.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400] (rev b1)
03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller

> **Ubuntu**
Release 10.04 (lucid)
Kernel Linux 2.6.32-23-generic
Gnome 2.30.2

**Hardware**
Memory: 3.4 GiB [Actually I have 4 GB of RAM, but for some reason Ubuntu doesn't register all 4 GBs, even though Memtest sees all 4 GBs]
Processor 0: Intel(R) Core(TM)2 Duo CPU  E7400 2.80 GHz
Processor 1: Intel(R) Core(TM)2 Duo CPU  E7400 2.80 GHz

**System Status**
Available disk space: 744.3 GiB

If you need any more info about my desktop, please let me know and provide a command for retrieving the info.

---

### Post by rfrey74 on 2010-07-20
Just an update.  The above symptoms are happening in gedit as well.

Does anyone have any answers on this one?

---

### Post by rfrey74 on 2010-08-03
Anyone?

---

### Post by Rendrago on 2010-08-05
I'm no expert but it sounds like a video driver problem. Have you tried different nVidia drivers? I've had random lock-up and weird looking screen issues with almost every version of Ubuntu while using nVidia cards. Usually getting the driver right did the trick.

Again, I'm no expert but strange lock-ups + video garbage + nVidia = driver issues.

---

