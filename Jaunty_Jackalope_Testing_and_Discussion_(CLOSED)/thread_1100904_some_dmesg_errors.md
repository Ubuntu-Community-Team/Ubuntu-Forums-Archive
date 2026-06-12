---
title: "some dmesg errors"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by excogitation on 2009-03-19
I'm seeing some dmesg errors I don't know what to do about - but maybe someone can tell me (if those even matter).

- sr needs updating
- sd needs updating
- ahci failed with error -22
```
[    1.947408] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.947512] Driver 'sd' needs updating - please use bus_type methods
[    1.947590] Driver 'sr' needs updating - please use bus_type methods
[    1.947720] ahci 0000:00:1f.2: version 3.0
[    1.947740] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.947799] ahci 0000:00:1f.2: PCI INT B disabled
[    1.947848] ahci: probe of 0000:00:1f.2 failed with error -22
```

- tsc unstable
- resume from disk failed
```
[    2.734158] eth0: Tigon3 [partno(BCM95788A50) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:c0:9f:f1:3a:02
[    2.734224] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[1]
[    2.734279] eth0: dma_rwctrl[763f0000] dma_mask[32-bit]
[    2.734357] ohci1394 0000:06:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.784173] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[c8215000-c82157ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.931679] Marking TSC unstable due to TSC halts in idle
[    3.120030] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    3.333838] usb 5-1: configuration #1 chosen from 1 choice
[    3.356029] Clocksource tsc unstable (delta = -371819494 ns)
[    3.485809] PM: Starting manual resume from disk
[    3.485858] PM: Resume from partition 8:6
[    3.485860] PM: Checking hibernation image.
[    3.486002] PM: Resume from disk failed.
```

- ieee80211_crypt: registered algorithm 'NULL'
```
[   18.058977] WARNING: synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   18.101753] ieee80211_crypt: registered algorithm 'NULL'
[   18.114978] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   18.115031] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
```

- `ntpd' uses 32-bit capabilities (legacy support in use)
- eth2: link is not ready
- wlan0: link is not ready
```
[   48.084638] [drm] Initialized drm 1.1.0 20060810
[   48.239493] pci 0000:01:00.0: setting latency timer to 64
[   48.239759] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   49.048855] [drm] Setting GART location based on new memory map
[   49.051368] [drm] Loading R400 Microcode
[   49.051414] [drm] Num pipes: 2
[   49.051422] [drm] writeback test succeeded in 1 usecs
[   49.180259] warning: `ntpd' uses 32-bit capabilities (legacy support in use)
[   51.206725] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   51.228687] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   61.520034] eth1: no IPv6 routers present
[   74.503848] [drm] Num pipes: 2
[   76.949590] [drm] Loading R400 Microcode
[   76.949634] [drm] Num pipes: 2
```

- ACPI: EC: missing confirmations, switch off interrupt mode.
```
[  157.356103] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  157.358338] input: Microsoft Bluetooth Notebook Mouse 5000 as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/bluetooth/hci0/hci0:39/input9
[  157.375370] generic-bluetooth 0005:045E:0700.0001: input,hidraw0: BLUETOOTH HID v1.00 Mouse [Microsoft Bluetooth Notebook Mouse 5000] on 00:1B:DC:01:E5:BE
[  174.692033] ACPI: EC: missing confirmations, switch off interrupt mode.
```

- operation="inode_permission" requested_mask="::rw" denied_mask="::rw"
```
[  436.263117] type=1503 audit(1237485644.521:11): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=6852 profile="/usr/sbin/cupsd"
[  881.696138] type=1503 audit(1237486089.957:12): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=7310 profile="/usr/sbin/cupsd"
[  881.703131] type=1503 audit(1237486089.961:13): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=7312 profile="/usr/sbin/cupsd"
[  881.786840] type=1503 audit(1237486090.045:14): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=7313 profile="/usr/sbin/cupsd"
```

- When trying to suspend
```
[12278.064210] CPU0 attaching NULL sched-domain.
[12278.065007] CPU0 attaching NULL sched-domain.
[12278.455789] CPU0 attaching NULL sched-domain.
[12278.455939] CPU0 attaching NULL sched-domain.
```

[full dmesg]("http://pastebin.com/m76b44ab0")

---

### Post by excogitation on 2009-03-20
So far I can answer these on my onw...

- sr needs updating
- sd needs updating -> [**# 186167**]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/186167")
Seems to be DVD drive related - all I'm doing with it seems to work - so not an issue.

- ahci failed with error -22 -> [**bugzilla 280781**]("https://bugzilla.redhat.com/show_bug.cgi?id=280781")
"This is normal for this controller. It supports both legacy and AHCI mode, and both drivers will be tried."
Guess not a problem then.

- tsc unstable -> [**# 190414**]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190414/")
afair expected for Pentium M

- resume from disk failed -> [**# 317185**]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/317185")
expected for any normal boot

- inode_permission ... tty ... cupsd ->[**# 153003**]("https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/153003/")
only cosmetical

- ACPI: EC: missing confirmations, switch off interrupt mode. -> [**# 284263**]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284263")

---

