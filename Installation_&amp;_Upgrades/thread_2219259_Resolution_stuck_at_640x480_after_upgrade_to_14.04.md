---
title: "Resolution stuck at 640x480 after upgrade to 14.04"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by greg49 on 2014-04-23
Hello everyone. I am having an issue with my laptop screen resolution being stuck at 640x480 after upgrading to 14.04 this morning. I searched the forums, but the majority of threads regarding this issue seem to revolve around VMs on various hardware. My installation is on an external usb drive connected to my HP 8570p.

I collected some of the info that appears to be useful in troubleshooting these types of issues below. Any assistance would be greatly appreciated!

greg@greg-HP-EliteBook-8570p:~$ uname -a
Linux greg-HP-EliteBook-8570p 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux


greg@greg-HP-EliteBook-8570p:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


greg@greg-HP-EliteBook-8570p:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: Thames [Radeon HD 7550M/7570M/7650M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:c0000000-cfffffff memory:d4300000-d431ffff ioport:4000(size=256) memory:d4340000-d435ffff


greg@greg-HP-EliteBook-8570p:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 7 Series/C210 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7550M/7570M/7650M]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Turks/Whistler HDMI Audio [Radeon HD 6000 Series]
24:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 30)
24:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
24:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
25:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)

If there is any other useful information I should collect and provide, please let me know and I will do my best to get it posted up.

Thanks!

---

### Post by greg49 on 2014-04-23
Well, looks like it might not matter now. I tried installing the AMD specific drivers manually, and can't start X or do anything else useful (that I know to do) from the cmd line. So, I guess I'm going to try a fresh install. Barring that, I suppose I'm down to just purchasing a personal Windows laptop.

---

