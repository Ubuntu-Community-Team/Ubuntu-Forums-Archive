---
title: "Fresh install laggs"
date: 2019-07-07
forum: Installation &amp; Upgrades
---

### Post by lielz on 2019-07-07
Hey everybody,

I have terrible lags in a Fresh 19.04 Ubuntu.

I've more problems like sound adjust itself or maybe the Input source disappear for second and back I am not really sure.
I've also notice that if I go to nVidia setting and make it run on performance mode its works better but still there is laggs here and there.

also not related performance problem that I have:
1. How I chance the next lang hot keys with "SHIFT" everything works just "SHIFT" didint work :/
2. I am a web developer, and i've seen that its css files to everything, I can edit them? its safe if I know waht Iam doing?, and there is a list that tell you what classes is what ?

I am new in this world, someone can help me fix that ?


--------------
The OS install on my SSD drive, while windows install on my M.2 Drive.
My CPU is already on performance mod in the governor.
Screenshot of the system: [https://ibb.co/S055GG3](https://ibb.co/S055GG3)

```
lspci -k

```[HTML]00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 05)    Subsystem: Gigabyte Technology Co., Ltd Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers    Kernel driver in use: skl_uncore00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 05)    Kernel driver in use: pcieport00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model    Subsystem: Gigabyte Technology Co., Ltd Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model00:14.0 USB controller: Intel Corporation 200 Series/Z370 Chipset Family USB 3.0 xHCI Controller    Subsystem: Gigabyte Technology Co., Ltd 200 Series/Z370 Chipset Family USB 3.0 xHCI Controller    Kernel driver in use: xhci_hcd00:16.0 Communication controller: Intel Corporation 200 Series PCH CSME HECI #1    Subsystem: Gigabyte Technology Co., Ltd 200 Series PCH CSME HECI    Kernel driver in use: mei_me    Kernel modules: mei_me00:17.0 SATA controller: Intel Corporation 200 Series PCH SATA controller [AHCI mode]    Subsystem: Gigabyte Technology Co., Ltd 200 Series PCH SATA controller [AHCI mode]    Kernel driver in use: ahci    Kernel modules: ahci00:1b.0 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #19 (rev f0)    Kernel driver in use: pcieport00:1b.3 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #20 (rev f0)    Kernel driver in use: pcieport00:1b.4 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #21 (rev f0)    Kernel driver in use: pcieport00:1c.0 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #3 (rev f0)    Kernel driver in use: pcieport00:1c.4 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #5 (rev f0)    Kernel driver in use: pcieport00:1d.0 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #9 (rev f0)    Kernel driver in use: pcieport00:1f.0 ISA bridge: Intel Corporation 200 Series PCH LPC Controller (H270)    Subsystem: Gigabyte Technology Co., Ltd 200 Series PCH LPC Controller (H270)00:1f.2 Memory controller: Intel Corporation 200 Series/Z370 Chipset Family Power Management Controller    Subsystem: Gigabyte Technology Co., Ltd 200 Series/Z370 Chipset Family Power Management Controller00:1f.3 Audio device: Intel Corporation 200 Series PCH HD Audio    Subsystem: Gigabyte Technology Co., Ltd 200 Series PCH HD Audio    Kernel driver in use: snd_hda_intel    Kernel modules: snd_hda_intel00:1f.4 SMBus: Intel Corporation 200 Series/Z370 Chipset Family SMBus Controller    Subsystem: Gigabyte Technology Co., Ltd 200 Series/Z370 Chipset Family SMBus Controller    Kernel driver in use: i801_smbus    Kernel modules: i2c_i80100:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-V    Subsystem: Gigabyte Technology Co., Ltd Ethernet Connection (2) I219-V    Kernel driver in use: e1000e    Kernel modules: e1000e01:00.0 VGA compatible controller: NVIDIA Corporation GP106 [GeForce GTX 1060 3GB] (rev a1)    Subsystem: Gigabyte Technology Co., Ltd GP106 [GeForce GTX 1060 3GB]    Kernel driver in use: nvidia    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia01:00.1 Audio device: NVIDIA Corporation GP106 High Definition Audio Controller (rev a1)    Subsystem: Gigabyte Technology Co., Ltd GP106 High Definition Audio Controller    Kernel driver in use: snd_hda_intel    Kernel modules: snd_hda_intel05:00.0 PCI bridge: Integrated Technology Express, Inc. IT8892E PCIe to PCI Bridge (rev 71)
[/HTML]


Thank you! :)

---

