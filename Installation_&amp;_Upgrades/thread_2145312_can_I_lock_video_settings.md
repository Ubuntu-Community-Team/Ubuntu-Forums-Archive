---
title: "can I lock video settings ?"
date: 2013-05-15
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2013-05-15
Every time I upgrade my Ubuntu distribution my graphics go wild.  I have Nvidia GT218 (GEFORCE 310) card in the computer and after upgrading, it will boot correctly about once in every 5 reboots ... but no idea why!  Other times it halts during the boot process or gives a bunch of strange messages.  I know Nvidia is dodgy and won't give the code required to build proper drivers, thus I will never ever buy one again.  

My question is this, is there a way to "fix" the video driver settings when I get it set up correctly (like now) such that it is forced to use these settings upon reboot?

13.04 also doesn't want to shut down properly but that is for another day.

Thanks

J

---

### Post by QIII on 2013-05-15
Are you using the Nvidia driver from the repo, or are you downloading from Nvidia and installing?

---

### Post by jamaas on 2013-05-15
I'm just using whatever Ubuntu chooses, right now I think it is the nouveau kernel driver.  In the past I've tried to download and install some from Nvidia but that just made the problem worse.  Suggestions?  Thanks

---

### Post by carl4926 on 2013-05-15
Question..

Do you have hybrid graphics?

---

### Post by jamaas on 2013-05-15
I think so but am not sure ... how do I find out for sure?  Thanks again! :-)

---

### Post by carl4926 on 2013-05-15
Let us see

```
lspci -nnk
```

---

### Post by jamaas on 2013-05-15
Done !
==============
lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e20] (rev 03)
	Subsystem: Dell Device [1028:0439]
00:01.0 PCI bridge [0604]: Intel Corporation 4 Series Chipset PCI Express Root Port [8086:2e21] (rev 03)
	Kernel driver in use: pcieport
00:1a.0 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
	Subsystem: Dell Device [1028:0439]
	Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
	Subsystem: Dell Device [1028:0439]
	Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
	Subsystem: Dell Device [1028:0439]
	Kernel driver in use: ehci-pci
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
	Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2 [8086:3a42]
	Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3 [8086:3a44]
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
	Subsystem: Dell Device [1028:0439]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
	Subsystem: Dell Device [1028:0439]
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
	Subsystem: Dell Device [1028:0439]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
	Subsystem: Dell Device [1028:0439]
	Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
	Subsystem: Dell Device [1028:0439]
	Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller [8086:3a22]
	Subsystem: Dell Device [1028:0439]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
	Subsystem: Dell Device [1028:0439]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [GeForce 310] [10de:0a66] (rev a2)
	Subsystem: Device [1b0a:9060]
	Kernel driver in use: nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be3] (rev a1)
	Subsystem: Device [1b0a:9060]
	Kernel driver in use: snd_hda_intel
03:00.0 PCI bridge [0604]: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge [10b5:8112] (rev aa)
04:04.0 Multimedia audio controller [0401]: C-Media Electronics Inc CMI8788 [Oxygen HD Audio] [13f6:8788]
	Subsystem: ASUSTeK Computer Inc. Virtuoso 100 (Xonar Essence STX) [1043:835c]
	Kernel driver in use: snd_virtuoso
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Dell Device [1028:0439]
	Kernel driver in use: r8169
=============================

---

### Post by carl4926 on 2013-05-15
It seems not. I only see:
```
[COLOR=#000000]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [GeForce 310] [10de:0a66] (rev a2)[/COLOR]
[COLOR=#000000]Subsystem: Device [1b0a:9060][/COLOR]
[COLOR=#000000]Kernel driver in use: nouveau[/COLOR]
```

I'm not aware of issues with this device.
Normal driver install for nvidia is
```
sudo apt-get install nvidia-current
```
That's all I ever have to do.

---

### Post by jamaas on 2013-05-17
This didn't work, now have big black square around my visible screen and it only boots into low graphics mode, any other suggestions?

---

