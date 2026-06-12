---
title: "How to install CUDA"
date: 2015-01-18
forum: Installation &amp; Upgrades
---

### Post by jrdobelmann on 2015-01-18
Recently I attempted to install the drivers for my Geforce 840M.  I constantly uninstalled and reinstalled the drivers because Blender would never recognize the graphics card.  I realized since then that I have to install CUDA support separately.  So assuming my drivers have been installed correctly, how do I install CUDA support?

I'm running Ubuntu Studio 14.04 64bit edition, lspci outputs
> 00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.1 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 2 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)
08:00.0 Network controller: Intel Corporation Wireless 7260 (rev 9b)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
0a:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)


and I have the 3.13.0-44 kernel, both generic and lowlatency.

---

### Post by tokyobadger on 2015-01-19
[have a look at that]("http://www.r-tutor.com/gpu-computing/cuda-installation/cuda6.5-ubuntu")
*caveat: don't use CUDA myself and haven't tried the guide at the link

**EDIT** I'm assuming you sorted out your [nvidia driver issue?](http://ubuntuforums.org/showthread.php?t=2261032) - please mark that thread as resolved if so

---

