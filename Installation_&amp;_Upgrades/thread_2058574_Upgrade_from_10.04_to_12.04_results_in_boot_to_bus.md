---
title: "Upgrade from 10.04 to 12.04 results in boot to busybox"
date: 2012-09-16
forum: Installation &amp; Upgrades
---

### Post by unperson on 2012-09-16
I was running an up-to-date version of Ubuntu lucid 10.04.4 LTS and used update-manager to upgrade to precise 12.04.1 LTS. After the upgrade was completed, a reboot of the system ended midway in a BusyBox prompt. If I type exit at that prompt the boot seems to continue as normal and the system boots to a usable (seemingly normal) desktop session. This behavior repeats on subsequent reboots.  Any clue as to what's going on would be appreciated.  Since the busybox prompt is not directly preceded by an error message I don't know what's causing it.

Looking back at the syslog, here is the bit that immediately preceeds the busybox prompt:
```

Sep 15 22:42:41 dirac kernel: [    1.415089] ata8: port disabled--ignoring
Sep 15 22:42:41 dirac kernel: [    1.421121] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 16
Sep 15 22:42:41 dirac kernel: [    1.421219] firewire_ohci 0000:01:0a.0: PCI INT A -> Link[LNKD] -> GSI 16 (level, low) -> IRQ 16
Sep 15 22:42:41 dirac kernel: [    1.453227] md: bind<sdb3>
Sep 15 22:42:41 dirac kernel: [    1.480163] md: bind<sdb5>
Sep 15 22:42:41 dirac kernel: [    1.484074] firewire_ohci: Added fw-ohci device 0000:01:0a.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
Sep 15 22:42:41 dirac kernel: [    1.660025] usb 4-2: new low-speed USB device number 2 using ohci_hcd
Sep 15 22:42:41 dirac kernel: [    1.898335] input: Microsoft Microsoft Trackball Optical® as /devices/pci0000:00/0000:00:04.0/usb4/4-2/4-2:1.0/input/input3
Sep 15 22:42:41 dirac kernel: [    1.898562] generic-usb 0003:045E:0023.0001: input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft Trackball Optical®] on usb-0000:00:04.0-2/input0
Sep 15 22:42:41 dirac kernel: [    1.898684] usbcore: registered new interface driver usbhid
Sep 15 22:42:41 dirac kernel: [    1.898761] usbhid: USB HID core driver
Sep 15 22:42:41 dirac kernel: [    1.984107] firewire_core: created device fw0: GUID 001e8c0001cac551, S400
Sep 15 22:42:41 dirac kernel: [    2.188015] usb 4-3: new low-speed USB device number 3 using ohci_hcd
Sep 15 22:42:41 dirac kernel: [    2.456443] input: Logitech Logitech Extreme 3D as /devices/pci0000:00/0000:00:04.0/usb4/4-3/4-3:1.0/input/input4
Sep 15 22:42:41 dirac kernel: [    2.457056] logitech 0003:046D:C215.0002: input,hidraw1: USB HID v1.10 Joystick [Logitech Logitech Extreme 3D] on usb-0000:00:04.0-3/input0
Sep 15 22:42:41 dirac kernel: [    2.512451] usb 1-3.2: new high-speed USB device number 3 using ehci_hcd
Sep 15 22:42:41 dirac kernel: [    2.621999] hub 1-3.2:1.0: USB hub found
Sep 15 22:42:41 dirac kernel: [    2.622437] hub 1-3.2:1.0: 4 ports detected
Sep 15 22:42:41 dirac kernel: [    2.696442] usb 1-3.4: new full-speed USB device number 4 using ehci_hcd

```

Then after I exit the busybox prompt the next few messages that follow are
```

Sep 15 22:42:41 dirac kernel: [    2.776891] md: linear personality registered for level -1
Sep 15 22:42:41 dirac kernel: [    2.778736] md: multipath personality registered for level -4
Sep 15 22:42:41 dirac kernel: [    2.780553] md: raid0 personality registered for level 0
Sep 15 22:42:41 dirac kernel: [    2.782525] md: raid1 personality registered for level 1
Sep 15 22:42:41 dirac kernel: [    2.784351] async_tx: api initialized (async)
Sep 15 22:42:41 dirac kernel: [    2.852013] raid6: int64x1   2246 MB/s
Sep 15 22:42:41 dirac kernel: [    2.920016] raid6: int64x2   3131 MB/s
Sep 15 22:42:41 dirac kernel: [    2.988025] raid6: int64x4   2036 MB/s
Sep 15 22:42:41 dirac kernel: [    3.056036] raid6: int64x8   1936 MB/s
Sep 15 22:42:41 dirac kernel: [    3.124019] raid6: sse2x1    3731 MB/s
Sep 15 22:42:41 dirac kernel: [    3.192016] raid6: sse2x2    5017 MB/s
Sep 15 22:42:41 dirac kernel: [    3.260021] raid6: sse2x4    5201 MB/s
Sep 15 22:42:41 dirac kernel: [    3.260023] raid6: using algorithm sse2x4 (5201 MB/s)
Sep 15 22:42:41 dirac kernel: [    3.260485] xor: automatically using best checksumming function: generic_sse
Sep 15 22:42:41 dirac kernel: [    3.280011]    generic_sse:  8436.000 MB/sec
Sep 15 22:42:41 dirac kernel: [    3.280013] xor: using function: generic_sse (8436.000 MB/sec)
Sep 15 22:42:41 dirac kernel: [    3.280772] md: raid6 personality registered for level 6
Sep 15 22:42:41 dirac kernel: [    3.280775] md: raid5 personality registered for level 5
Sep 15 22:42:41 dirac kernel: [    3.280776] md: raid4 personality registered for level 4
Sep 15 22:42:41 dirac kernel: [    3.286453] md: raid10 personality registered for level 10
Sep 15 22:42:41 dirac kernel: [ 1794.858443] EXT3-fs (sda2): recovery required on readonly filesystem
Sep 15 22:42:41 dirac kernel: [ 1794.858523] EXT3-fs (sda2): write access will be enabled during recovery
Sep 15 22:42:41 dirac kernel: [ 1795.595088] kjournald starting.  Commit interval 5 seconds
Sep 15 22:42:41 dirac kernel: [ 1795.595201] EXT3-fs (sda2): recovery complete
Sep 15 22:42:41 dirac kernel: [ 1795.595650] EXT3-fs (sda2): mounted filesystem with ordered data mode
Sep 15 22:42:41 dirac kernel: [ 1816.752507] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 15 22:42:41 dirac kernel: [ 1816.837520] Adding 2176800k swap on /dev/sda5.  Priority:-1 extents:1 across:2176800k 
Sep 15 22:42:41 dirac kernel: [ 1816.846234] lp: driver loaded but no devices found
Sep 15 22:42:41 dirac kernel: [ 1816.859738] i2c i2c-0: nForce2 SMBus adapter at 0x600
Sep 15 22:42:41 dirac kernel: [ 1816.859743] ACPI: resource nForce2_smbus [io  0x0700-0x073f] conflicts with ACPI region SM00 [io 0x700-0x73f]
Sep 15 22:42:41 dirac kernel: [ 1816.859746] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep 15 22:42:41 dirac kernel: [ 1816.981338] wmi: Mapper loaded
Sep 15 22:42:41 dirac kernel: [ 1817.038808] EXT3-fs (sda2): using internal journal

```

In case it's useful I've attached the output of lspci and lsmod, and the output of uname is 

```

$ uname -a
Linux dirac 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by unperson on 2012-09-17
Two points of clarification:
[LIST=1]
[*]The system in question is only running Ubuntu; it is not dual booting.
[*]I realize no one may have a complete answer, but any clue as to potential reasons why the busybox prompt might be coming up would help me at least start troubleshooting.
[/LIST]

---

