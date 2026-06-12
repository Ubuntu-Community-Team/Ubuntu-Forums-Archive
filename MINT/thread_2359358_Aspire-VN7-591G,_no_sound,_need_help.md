---
title: "Aspire-VN7-591G, no sound, need help"
date: 2017-04-23
forum: MINT
---

### Post by tomaasj on 2017-04-23
Dear all,

after a clean install, the sound comes only from a single speaker.

The hardware must be OK since all speakers (I guess, there are four built-in) were functioning normally under Windows 10.

I followed the troubleshooting guides concerning sound issues and Ubuntu, checked numerous posts, installed pavucontrol, alsamixer to check what is going on, but to no avail.

I hope that there is somebody out there who can help me figure out what is going on.


See specifics below and the two screenshots attached.

Thanks in advance,

Tamás


```
Aspire-VN7-591G

Linux tamas-Aspire-VN7-591G 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC283 Analog [ALC283 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
	Subsystem: Acer Incorporated [ALI] Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: ie31200_edac

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 26
	Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d0000000-d0ffffff
	Prefetchable memory behind bridge: 00000000a0000000-00000000bfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] 4th Gen Core Processor Integrated Graphics Controller
	Flags: bus master, fast devsel, latency 0, IRQ 33
	Memory at d1000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
	Subsystem: Acer Incorporated [ALI] Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 36
	Memory at d1710000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05) (prog-if 30 [XHCI])
	Subsystem: Acer Incorporated [ALI] 8 Series/C220 Series Chipset Family USB xHCI
	Flags: bus master, medium devsel, latency 0, IRQ 29
	Memory at d1700000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Acer Incorporated [ALI] 8 Series/C220 Series Chipset Family MEI Controller
	Flags: bus master, fast devsel, latency 0, IRQ 34
	Memory at d1718000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei_me
	Kernel modules: mei_me

00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] 8 Series/C220 Series Chipset Family USB EHCI
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at d171d000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] 8 Series/C220 Series Chipset High Definition Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 35
	Memory at d1714000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Memory behind bridge: d1600000-d16fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d1500000-d15fffff
	Prefetchable memory behind bridge: 00000000d1400000-00000000d14fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] 8 Series/C220 Series Chipset Family USB EHCI
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d171c000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation HM86 Express LPC Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] HM86 Express LPC Controller
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Acer Incorporated [ALI] 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 30
	I/O ports at 5088 [size=8]
	I/O ports at 5094 [size=4]
	I/O ports at 5080 [size=8]
	I/O ports at 5090 [size=4]
	I/O ports at 5060 [size=32]
	Memory at d171b000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] 8 Series/C220 Series Chipset Family SMBus Controller
	Flags: medium devsel
	Memory at d1719000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 5040 [size=32]
	Kernel modules: i2c_i801

01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 860M] (rev a2)
	Subsystem: Acer Incorporated [ALI] GM107M [GeForce GTX 860M]
	Flags: bus master, fast devsel, latency 0, IRQ 32
	Memory at d0000000 (32-bit, non-prefetchable) [size=16M]
	Memory at a0000000 (64-bit, prefetchable) [size=256M]
	Memory at b0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 4000 [size=128]
	Expansion ROM at b2000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau

07:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)
	Subsystem: Foxconn International, Inc. AR9462 Wireless Network Adapter
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d1600000 (64-bit, non-prefetchable) [size=512K]
	Expansion ROM at d1680000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
	Flags: bus master, fast devsel, latency 0, IRQ 31
	I/O ports at 3000 [size=256]
	Memory at d1500000 (64-bit, non-prefetchable) [size=4K]
	Memory at d1400000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169
```

---

### Post by howefield on 2017-04-23
What exactly is the version of Ubuntu ?

```
cat /etc/*-release
```

---

### Post by tomaasj on 2017-04-23
Correct:  it is linux mint

Should this make a difference?

It was my understanding that they are essentially the same?

```
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=18.1
DISTRIB_CODENAME=serena
DISTRIB_DESCRIPTION="Linux Mint 18.1 Serena"
NAME="Linux Mint"
VERSION="18.1 (Serena)"
ID=linuxmint
ID_LIKE=ubuntu
PRETTY_NAME="Linux Mint 18.1"
VERSION_ID="18.1"
HOME_URL="http://www.linuxmint.com/"
SUPPORT_URL="http://forums.linuxmint.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/linuxmint/"
VERSION_CODENAME=serena
UBUNTU_CODENAME=xenial
cat: /etc/upstream-release: Is a directory
```

---

### Post by howefield on 2017-04-23
> **tomaasj said:**
> Should this make a difference?

It makes a difference to the organisation and searching of the forums..

> Forum: General Help
All your general support questions for Ubuntu, Kubuntu, Edubuntu, Xubuntu, Lubuntu, UbuntuGnome, Ubuntu Mate, and Ubuntu Kylin. 

> Forum: MINT
For all your Linux Mint questions.

You are more than welcome to post Mint questions here in this sub forum. However I have to say it might make better sense to support the forums and other support avenues relating to your distribution of choice.

Thread moved to the "*MINT*" forum.

---

### Post by tomaasj on 2017-04-23
OK,

thanks

---

