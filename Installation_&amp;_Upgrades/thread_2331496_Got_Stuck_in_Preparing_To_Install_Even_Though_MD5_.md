---
title: "Got Stuck in Preparing To Install Even Though MD5 Checks Out Fine"
date: 2016-07-22
forum: Installation &amp; Upgrades
---

### Post by GraysonPeddie on 2016-07-22
```
[grayson@htpc ~]$ md5sum ubuntu-16.04.1-desktop-amd64.iso 
17643c29e3c4609818f26becf76d29a3  ubuntu-16.04.1-desktop-amd64.iso
```

No matter what I do when it comes to booting into live desktop or by selecting Install Ubuntu from the boot menu and whether if downloading updates/third party software is checked or unchecked, I cannot get past the Preparing to install screen.

```
[grayson@htpc ~]$ sudo fdisk -l
[sudo] password for grayson: 
Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 4B546035-F9E0-48DE-8DE1-BB08568C5229

Device         Start        End    Sectors   Size Type
/dev/sda1       2048     194559     192512    94M EFI System
/dev/sda2     194560  234620927  234426368 111.8G Linux filesystem
/dev/sda3  234620928  297119743   62498816  29.8G Linux swap
/dev/sda4  297119744 1953523711 1656403968 789.9G Linux filesystem


Disk /dev/sdc: 14.7 GiB, 15805186048 bytes, 30869504 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x40a863e7

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdc1  *          0 2955679 2955680  1.4G  0 Empty
/dev/sdc2       2927216 2931951    4736  2.3M ef EFI (FAT-12/16/32)
```

I flashed my USB drive through "dd" while in Arch Linux, as I want to try something different by going with Unity from GNOME 3.20, which I am currently using right now, so yeah, I plan to distro-hop.

Here's my hardware information in case you need it:

```
[grayson@htpc ~]$ sudo lshw -short
H/W path           Device  Class       Description
==================================================
                           system      To be filled by O.E.M. (To be filled by O.E.M.)
/0                         bus         F2A88XM-HD3
/0/0                       memory      64KiB BIOS
/0/23                      memory      16GiB System Memory
/0/23/0                    memory      [empty]
/0/23/1                    memory      8GiB DIMM DDR3 Synchronous Unbuffered (Unregistered) 1866 MHz (0.5 ns)
/0/23/2                    memory      [empty]
/0/23/3                    memory      8GiB DIMM DDR3 Synchronous Unbuffered (Unregistered) 1866 MHz (0.5 ns)
/0/2f                      memory      256KiB L1 cache
/0/30                      memory      4MiB L2 cache
/0/39                      processor   AMD A8-7600 Radeon R7, 10 Compute Cores 4C+6G
/0/100                     bridge      Family 15h (Models 30h-3fh) Processor Root Complex
/0/100/0.2                 generic     Family 15h (Models 30h-3fh) I/O Memory Management Unit
/0/100/1                   display     Kaveri [Radeon R7 Graphics]
/0/100/1.1                 multimedia  Kaveri HDMI/DP Audio Controller
/0/100/2.1                 bridge      Advanced Micro Devices, Inc. [AMD]
/0/100/2.1/0               display     GM206 [GeForce GTX 960]
/0/100/2.1/0.1             multimedia  NVIDIA Corporation
/0/100/3.1                 bridge      Family 15h (Models 30h-3fh) Processor Root Port
/0/100/3.1/0       enp2s0  network     RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/10                  bus         FCH USB XHCI Controller
/0/100/10/0        usb1    bus         xHCI Host Controller
/0/100/10/0/1              multimedia  USB2.0-MIDI
/0/100/10/0/2              bus         USB Hub 2.0
/0/100/10/0/2/2            bus         Keyboard Hub
/0/100/10/0/2/2/2          input       Apple Keyboard
/0/100/10/1        usb2    bus         xHCI Host Controller
/0/100/10/1/1              storage     ADATA USB Flash Drive
/0/100/10.1                bus         FCH USB XHCI Controller
/0/100/10.1/0      usb3    bus         xHCI Host Controller
/0/100/10.1/0/1            generic     Nexus 6P
/0/100/10.1/1      usb4    bus         xHCI Host Controller
/0/100/11                  storage     FCH SATA Controller [AHCI mode]
/0/100/12                  bus         FCH USB OHCI Controller
/0/100/12/1        usb7    bus         OHCI PCI host controller
/0/100/12.2                bus         FCH USB EHCI Controller
/0/100/12.2/1      usb5    bus         EHCI Host Controller
/0/100/13                  bus         FCH USB OHCI Controller
/0/100/13/1        usb8    bus         OHCI PCI host controller
/0/100/13/1/1              input       USB Device
/0/100/13.2                bus         FCH USB EHCI Controller
/0/100/13.2/1      usb6    bus         EHCI Host Controller
/0/100/13.2/1/5            multimedia  FCA1616
/0/100/14                  bus         FCH SMBus Controller
/0/100/14.2                multimedia  FCH Azalia Controller
/0/100/14.3                bridge      FCH LPC Bridge
/0/100/14.4                bridge      FCH PCI Bridge
/0/100/14.5                bus         FCH USB OHCI Controller
/0/100/14.5/1      usb9    bus         OHCI PCI host controller
/0/101                     bridge      Advanced Micro Devices, Inc. [AMD]
/0/102                     bridge      Advanced Micro Devices, Inc. [AMD]
/0/103                     bridge      Advanced Micro Devices, Inc. [AMD]
/0/104                     bridge      Family 15h (Models 30h-3fh) Processor Function 0
/0/105                     bridge      Family 15h (Models 30h-3fh) Processor Function 1
/0/106                     bridge      Family 15h (Models 30h-3fh) Processor Function 2
/0/107                     bridge      Family 15h (Models 30h-3fh) Processor Function 3
/0/108                     bridge      Family 15h (Models 30h-3fh) Processor Function 4
/0/109                     bridge      Family 15h (Models 30h-3fh) Processor Function 5
```

Is there any way to get past the "prepare for installation" screen?

---

### Post by GraysonPeddie on 2016-07-23
I have worked around my problem. I first did an Ubuntu Server install and then install Ubuntu Desktop from the command line.

I did get a warning about /dev/sda2 not being unmounted, but I guess Arch Linux forgot to unmount that partition. Maybe that's what got the Ubiquity installer hanged up on if /dev/sda2 did not get properly unmounted! Although that is a distro's problem that falls beyond the scope of this forum. And yes, I did properly shut down Arch Linux.

So all is well.

---

