---
title: "tuxonice install problems with gutsy"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by bitmonkey on 2008-01-15
I am having major problems getting hibernation to work. I am trying to install tuxonice. The kernel rebuild goes fine, using a base .config from the /boot directory and only changing the  necessary items, plus another couple of minor optimisations not related to the issues detailed later. Install of the kernel and headers is ok. Building the restricted modules kept failing due to name wierdness - the kernel make system (using make-kpkg) was producing kernel builds with package names that wouldn't match up with the name of the restricted drivers .deb, so the restricted drivers install would fail on a dependency issue.

I kludged that together by editing the restricted drivers /debian/rules file and the kernel Makefile to get the package names to come out the same. Then I built the restricted drivers against the new headers, installed and all should have been well.

However, now although I can boot to X with most basics seeming to work, a lot is broken: sound, wireless network (which was using ndiswrapper) and graphics optimisations (can't enable desktop effects, but desktop is accessible at a normal resolution and otherwise OK) at the least, possibly more is broken - I haven't looked. 

Doing some poking about I noticed hardly any modules loaded. I rebooted into my stock kernel, did a lsmod, noted the modules then rebooted into the new kernel and modprobed them all - still no sound, network or desktop effects. When I tried to modprobe in everything that had been listed under lsmod in the working kernel most of it probed in ok, but the following errors occured - I think since ndiswapper was being used for my network card and possibly (I don't know) snd_hda_intel for my sound this may be a clue as to what is going on - however it doesn't tell me enough to fix it (not the most experienced linux user). 

WARNING: Module cpufreq_userspace not found.
WARNING: Module ndiswrapper not found.
WARNING: Module snd_hda_intel not found.
WARNING: Module snd_hda_intel,snd_pcm_oss not found.
WARNING: Module lirc_mceusb2 not found.
WARNING: Module lirc_dev not found.
WARNING: Module uvcvideo not found.
WARNING: Module ohci_mod not found.
WARNING: Module ehci_mod not found.
WARNING: Module apparmor not found.

Opening the "restricted drivers manager" says that none of my hardware needs proprietary drivers - not so, the graphics card uses this normally.

I'm going to paste my lspci below.

If they will be any use I can post my /var/log/messages and dmesg output. Please request if they will help.

Here's my lspci output incase it's of help:

00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

