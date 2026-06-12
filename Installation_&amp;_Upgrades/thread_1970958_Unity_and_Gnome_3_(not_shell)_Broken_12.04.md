---
title: "Unity and Gnome 3 (not shell) Broken 12.04"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by Tourniquette on 2012-05-01
Hey all. I upgraded to 12.04 a couple days ago, and it went pretty smoothly. Nothing out of the ordinary. I have 3 GUI's installed: Unity (obviously), Gnome 3, and XFCE. New login screen working, everything seems fine. But as soon as I login to either the newest Unity or Gnome, I get an error saying either that Compiz has crashed or that there was an internal error. Unity 2D works fine, and so does XFCE (aside from some minor audio problems). Am I right in assuming that this is a driver problem?I've tried both available drivers with no luck. I have an oldish Nvidia card (GeForce 6150 LE/integrated/SSE2), but before the upgrade everything was working perfectly. Processor is an AMD Athlon 64 Processor 3500+  Hopefully someone can throw me some answers. Here's my lspci output:

00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: NVIDIA Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: NVIDIA Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:0a.0 Communication controller: LSI Corporation Lucent V.92 Data/Fax Modem

---

### Post by The Rnegade on 2012-05-02
> **Tourniquette said:**
> Hey all. I upgraded to 12.04 a couple days ago, and it went pretty smoothly. Nothing out of the ordinary. I have 3 GUI's installed: Unity (obviously), Gnome 3, and XFCE. New login screen working, everything seems fine. But as soon as I login to either the newest Unity or Gnome, I get an error saying either that Compiz has crashed or that there was an internal error. Unity 2D works fine, and so does XFCE (aside from some minor audio problems). Am I right in assuming that this is a driver problem?I've tried both available drivers with no luck. I have an oldish Nvidia card (GeForce 6150 LE/integrated/SSE2), but before the upgrade everything was working perfectly. Processor is an AMD Athlon 64 Processor 3500+  Hopefully someone can throw me some answers. Here's my lspci output:

00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: NVIDIA Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: NVIDIA Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:0a.0 Communication controller: LSI Corporation Lucent V.92 Data/Fax Modem

gnome 3 and normal unity both need 3d acceleration to run. gnome 3 just added systemd as a dependency, which makes it harder for older computers to run it

---

### Post by oboedad55 on 2012-05-02
Gnome shell uses mutter, Unity uses compiz. I'm running both Unity 3D and Gnome shell with an Nvidia 6200 LE which is a pretty low-power video card, with the current driver. There is no "Gnome 3", just old Gnome 2 and Gnome shell. If Unity 3D was working in 11.10 it should still work in 12.04. Sounds like something else is wonky. I'm not suggesting this necessarily, but I always just do a clean install rather than upgrade. Seems to take less time and there's no risk of weird things happening. My understanding is that with the 12.04 CD, even without a /home partition you should be able to install and keep your /home folder. As always, BACK UP any data you want to keep.

---

### Post by Tourniquette on 2012-05-03
Well, the only thing is that every desktop worked fine before that, and they were all up to date. And I'm out of discs to burn to, so I was really hoping it was just a driver issue:)

---

### Post by leojimenezcr on 2012-05-09
I have the same problem with a Nvidia GeForce 6150 LE in a Dell Optiplex 740 computer. I tried with the free and the privative driver provided by Ubuntu.

I installed the drivers provided by Nvidia in the web site and it work very good.

My solution:
1. Install 'linux-headers-x.x.x-xx' package
2. Go to [http://www.geforce.com/Drivers](http://www.geforce.com/Drivers) and download the drivers (in my case Linux 64bits)
3. Go to a terminal (Ctrl+Alt+F1). It not work in graphic mode :-/
4. Stop the graphic server: sudo service lightdm stop
5. Make the driver script executable: chmod +x /path/to/script/NVIDIA-Linux-x86_xx-xx.xx.run
6. Run the script: sudo /path/to/script/NVIDIA-Linux-x86_xx-xx.xx.run
7. Ok, ok, ok, ok, ...
8. Reboot the computer with command: sudo reboot

It script buld a specific module to connect Nvidia drivers with the Linux kernel installed. If you upgrade your kernel, after reboot repeat the process to build a new module to connect to the new kernel. So, keep the installer.

Any better solution please tell us :-)

---

