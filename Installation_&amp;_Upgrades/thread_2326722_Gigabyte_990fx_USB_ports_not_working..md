---
title: "Gigabyte 990fx USB ports not working."
date: 2016-06-03
forum: Installation &amp; Upgrades
---

### Post by br116 on 2016-06-03
On a Gigabyte 990FX Gaming rev. 1 USB ports "DAC UP" and 3.1 are not working on Ubuntu 14.04. Keyboard and mouse attached there do work in BIOS (and Win7).
They do work on USB 3.0 port (see below).
Note, all other USB ports (if listed below) have hardware connected to them (HDD, SDD, Camera, MP3, etc) with no luck.

Below results of
 lspci -nnk | egrep -iA2 'net|usb'
lsusb

00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ohci-pci
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ehci-pci
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ohci-pci
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ehci-pci
--
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ohci-pci
--
00:16.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ohci-pci
00:16.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Kernel driver in use: ehci-pci
--
02:00.0 USB controller [0c03]: ASMedia Technology Inc. Device [1b21:1343]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5007]
    Kernel driver in use: xhci_hcd
--
05:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller [1969:e091] (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
    Kernel driver in use: alx
06:00.0 USB controller [0c03]: VIA Technologies, Inc. VL805 USB 3.0 Host Controller [1106:3483] (rev 01)
    Subsystem: VIA Technologies, Inc. VL805 USB 3.0 Host Controller [1106:3483]
    Kernel driver in use: xhci_hcd
br116@br116-GA-MA770T-UD3P:~$ lsusb
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 003: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 003 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Can someone please help?

---

### Post by oldfred on 2016-06-03
Probably IOMMU, both in UEFI and a boot option setting.
Use e for edit on grub menu and add to or replace quiet splash with:
iommu=soft

 turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[URL="http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1"]http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1
[/URL]
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - 
Permanent setting in /etc/default/grub: IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[URL="http://ubuntuforums.org/showthread.php?t=2111223&page=5"]http://ubuntuforums.org/showthread.php?t=2111223&page=5

[/URL]Boot Options
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) 

[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by QIII on 2016-06-03
Hello!

There has been a long-standing issue with the 990FX series boards from Gigabyte.  I have run in to it on this machine. 

The issue has to do with IOMMU -- Input Output Memory Management Unit.  We need to make sure that the OS controls it rather than the mobo firmware.

open a terminal and issue the following command:

```
gksudo gedit /etc/default/grub
```

Input your password at the prompt.

Find the line that says *GRUB_CMDLINE_LINUX=""* and change it to *GRUB_CMDLINE_LINUX="iommu=soft"*

I also change the line *GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"* to *GRUB_CMDLINE_LINUX_DEFAULT="quiet splash iommu=soft"*

Save the file.

Now you need to update GRUB to use the new settings:

```
sudo update-grub
```

Reboot.  You may or may not have to disable IOMMU in your BIOS/UEFI if you still have problems when you reboot.

---

### Post by br116 on 2016-06-04
Thank you QIII,
That did the trick.
IOMMU was already disabled.

---

