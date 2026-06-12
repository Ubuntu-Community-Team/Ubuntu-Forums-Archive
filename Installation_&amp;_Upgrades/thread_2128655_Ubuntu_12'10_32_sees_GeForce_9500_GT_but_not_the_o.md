---
title: "Ubuntu 12'10 32 sees GeForce 9500 GT but not the other GT520 I have both installed"
date: 2013-03-23
forum: Installation &amp; Upgrades
---

### Post by TunesForMe on 2013-03-23
I run a quad core Asus desktop with 2 video cards installed Windows can handle this easily. I use 3 monitors and have capacity for a 4th. Each video card has 2 HD outputs. Ubuntu sees the main first video card and I have duel monitors working on the one 9500 GT Nvida card with no problem. I want to enable the second video card GT 520 Nvidia  as well for the 3rd monitor. Is this possible?

I have been looking and can not find an answer.

---

### Post by TunesForMe on 2013-03-23
INFO:

chuck@Linux-Pc:~$  lspci -nnk | grep -iA2 vga
03:00.0 VGA compatible controller [0300]: NVIDIA Corporation G96 [GeForce 9500 GT] [10de:0640] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:c959]
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current_updates, nouveau, nvidiafb
05:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119 [GeForce GT 520] [10de:1040] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:1526]
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current_updates, nouveau, nvidiafb
--
    Subsystem: eVga.com. Corp. Device [3842:1526]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
chuck@Linux-Pc:~$ sudo lshw -C display
[sudo] password for chuck: 
  *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9500 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f6000000-f6ffffff memory:c0000000-cfffffff memory:f4000000-f5ffffff ioport:ec00(size=128) memory:f7f80000-f7ffffff
  *-display
       description: VGA compatible controller
       product: GF119 [GeForce GT 520]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f9000000-f9ffffff memory:d8000000-dfffffff memory:e6000000-e7ffffff ioport:cc00(size=128) memory:e0000000-e007ffff

---

### Post by TunesForMe on 2013-03-23
NO video is coming out of the second card the GT 520. Any help is appreciated.

---

### Post by oldfred on 2013-03-24
I have this link, now older as you are not using gdm (lightdm if Ubuntu?). But shows it can be done.

Do you have this?
 ARandR Screen Layout Editor 0.1.4 - Dual screens
[http://christian.amsuess.com/tools/arandr/](http://christian.amsuess.com/tools/arandr/)

12 monitors Natty Warhal
This is a success story for installing 3 ATI Firepro 2260's and 1 Radeon HD 5870 in the same computer. 
[http://ubuntuforums.org/showthread.php?t=1850517](http://ubuntuforums.org/showthread.php?t=1850517)

---

