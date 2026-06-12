---
title: "Installing Ubuntu in MSI GE62 6QD"
date: 2016-11-21
forum: Installation &amp; Upgrades
---

### Post by aoodi6 on 2016-11-21
Hello, after a long time trying to install any Linux distro in my laptop I finally managed to install Ubuntu. This laptop has lots of non-free drivers and incompatibilities. So here is what I did to Install Ubuntu 16.04. Works fine with Ubuntu 16.10.

This is my ```
lspci
```

```
Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 07)
PCI bridge: Intel Corporation Sky Lake PCIe Controller (x16) (rev 07)
VGA compatible controller: Intel Corporation Skylake Integrated Graphics (rev 06)
USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
SATA controller: Intel Corporation Sunrise Point-H SATA Controller [AHCI mode] (rev 31)
PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #1 (rev f1)
PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #4 (rev f1)
PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #5 (rev f1)
ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
3D controller: NVIDIA Corporation GM107M [GeForce GTX 960M] (rev a2)
Network controller: Intel Corporation Wireless 3165 (rev 81)
Ethernet controller: Qualcomm Atheros Killer E2400 Gigabit Ethernet Controller (rev 10)
USB controller: ASMedia Technology Inc. ASM1142 USB 3.1 Host Controller
```


Okay, so for installation when it first appears the EMPTY purple screen press ENTER, SELECT YOUR LANGUAGE, and then press F6 and choose NOMODESET. Continue with installation, and when it first boots, download latest nvidia drivers by:

```
sudo apt-get install nvidia-367
```

For 21/11/2016 nvidia-367 is la latest.

Go to grub and take off the nomodeset line, right under "quiet splash" line:

[HTML]sudo gedit /etc/default/grub
sudo upgrade-grub
reboot[/HTML]

If Intel card is being used got to command line (CNTRL-ALT-F1) and do:
```
sudo prime select-nvidia
```

That's all!

Ps.: Integrated Intel 530 graphics crashes, so I'm using Nvidia's card all the time. Any solutions feel free to comment!

---

