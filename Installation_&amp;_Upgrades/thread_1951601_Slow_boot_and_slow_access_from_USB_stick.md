---
title: "Slow boot and slow access from USB stick"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by OliverHaslam on 2012-04-02
Hi,

I've had Ubuntu 11.10 installed on a USB stick for a while now, but recently I have noticed a couple of performance issues.

The machine takes a long time to boot. Everything is fine until I get the Ubuntu purple booting screen. Nothing else pops up, and it seems to sit there for a couple of minutes before kicking back into action.

I have also noticed that opening Chrome, or even just folders feels sluggish. Apps in general feel slow to react.

Like I say, the whole machine feels slower than it used to when I first set the disk up. possibly an update has changed something?

Any ideas?

---

### Post by nd456 on 2012-04-02
I would start with clearing cash and history. Any recent installs?

---

### Post by OliverHaslam on 2012-04-03
> **nd456 said:**
> I would start with clearing cash and history. Any recent installs?

Clear Chrome's Cache? It's not just Chrome that's slow.

---

### Post by OliverHaslam on 2012-04-03
Here's my dmesg log with an interesting 20s delay.

```
[    2.601302] sd 4:0:0:0: [sdc] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.601334] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    2.601375] sd 4:0:0:0: [sdc] Write Protect is off
[    2.601377] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.601410] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.717888]  sdc: sdc1
[    2.718191] sd 4:0:0:0: [sdc] Attached SCSI disk
[    2.920036] ata6: SATA link down (SStatus 0 SControl 300)
[    3.240035] ata7: SATA link down (SStatus 0 SControl 300)
[    3.560034] ata8: SATA link down (SStatus 0 SControl 300)
[    3.560980] Initializing USB Mass Storage driver...
[    3.563673] scsi10 : usb-storage 1-1:1.0
[    3.565482] usbcore: registered new interface driver usb-storage
[    3.565485] USB Mass Storage support registered.
[    4.565065] scsi 10:0:0:0: Direct-Access     SanDisk  Cruzer Blade     1.20 PQ: 0 ANSI: 5
[    4.588611] sd 10:0:0:0: Attached scsi generic sg4 type 0
[    4.590046] sd 10:0:0:0: [sdd] 31266816 512-byte logical blocks: (16.0 GB/14.9 GiB)
[    4.591291] sd 10:0:0:0: [sdd] Write Protect is off
[    4.591295] sd 10:0:0:0: [sdd] Mode Sense: 43 00 00 00
[    4.592041] sd 10:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    4.596990]  sdd: sdd1
[    4.600160] sd 10:0:0:0: [sdd] Attached SCSI removable disk
[    8.708296] EXT4-fs (sdd1): INFO: recovery required on readonly filesystem
[    8.708301] EXT4-fs (sdd1): write access will be enabled during recovery
[    8.902325] EXT4-fs (sdd1): recovery complete
[    8.905416] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
[   28.058234] udevd[329]: starting version 173
[   28.095604] lp: driver loaded but no devices found
[   28.226938] EXT4-fs (sdd1): re-mounted. Opts: errors=remount-ro
[   28.277324] nvidia: module license 'NVIDIA' taints kernel.
[   28.277327] Disabling lock debugging due to kernel taint
[   28.282961] parport_pc 00:07: reported by Plug and Play ACPI
[   28.283013] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   28.372516] lp0: using parport0 (interrupt-driven).
[   28.600402] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.600410] nvidia 0000:01:00.0: setting latency timer to 64
[   28.600415] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   28.600634] NVRM: loading NVIDIA UNIX x86 Kernel Module  295.33  Sat Mar 17 14:56:23 PDT 2012
[   28.605132] ppdev: user-space parallel port driver
```

---

### Post by garvinrick4 on 2012-04-03
> I've had Ubuntu 11.10 installed on a USB stick for a while now,
Flash drives do get slower after a time.

Get new flash drive:
Get USB drive (faster)

---

### Post by OliverHaslam on 2012-04-03
> **garvinrick4 said:**
> Flash drives do get slower after a time.

Get new flash drive:
Get USB drive (faster)

Thanks, but I'm not sure that's it. The drive is only a couple of months old. Notice the delay in mounting it, though?

---

### Post by OliverHaslam on 2012-04-03
Just to add: I've cloned the USB stick to a spare 160GB SATA drive and got it running from there.

Looking at the log file, the same gap appears, although I swear the system boots considerably quicker. Am I misunderstanding the logs?

New log:

```
Apr  3 11:29:55 kirk kernel: [    1.742255] generic-usb 0003:0B38:0010.0001: input,hidraw0: USB HID v1.10 Keyboard [HID 0b38:0010] on usb-0000:00:1a.1-1/input0
Apr  3 11:29:55 kirk kernel: [    1.765799] input: HID 0b38:0010 as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.1/input/input3
Apr  3 11:29:55 kirk kernel: [    1.765916] generic-usb 0003:0B38:0010.0002: input,hidraw1: USB HID v1.10 Device [HID 0b38:0010] on usb-0000:00:1a.1-1/input1
Apr  3 11:29:55 kirk kernel: [    1.765932] usbcore: registered new interface driver usbhid
Apr  3 11:29:55 kirk kernel: [    1.765934] usbhid: USB HID core driver
Apr  3 11:29:55 kirk kernel: [    1.860305] input: Microsoft Microsoft IntelliMouse® Explorer as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input4
Apr  3 11:29:55 kirk kernel: [    1.860391] generic-usb 0003:045E:001E.0003: input,hidraw2: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse® Explorer] on usb-0000:00:1a.1-2/input0
Apr  3 11:29:55 kirk kernel: [    1.996535] ata7.01: ATAPI: LITE-ON DVDRW SOHW-832S, VS01, max UDMA/33
Apr  3 11:29:55 kirk kernel: [    2.012539] ata7.01: configured for UDMA/33
Apr  3 11:29:55 kirk kernel: [    2.036048] ata5: SATA link down (SStatus 0 SControl 300)
Apr  3 11:29:55 kirk kernel: [    2.036089] ata6: SATA link down (SStatus 0 SControl 300)
Apr  3 11:29:55 kirk kernel: [    2.037037] scsi 6:0:1:0: CD-ROM            LITE-ON  DVDRW SOHW-832S  VS01 PQ: 0 ANSI: 5
Apr  3 11:29:55 kirk kernel: [    2.039243] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Apr  3 11:29:55 kirk kernel: [    2.039246] cdrom: Uniform CD-ROM driver Revision: 3.20
Apr  3 11:29:55 kirk kernel: [    2.039401] sr 6:0:1:0: Attached scsi CD-ROM sr0
Apr  3 11:29:55 kirk kernel: [    2.039489] sr 6:0:1:0: Attached scsi generic sg3 type 5
Apr  3 11:29:55 kirk kernel: [    7.061382] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
Apr  3 11:29:55 kirk kernel: [   24.406986] lp: driver loaded but no devices found
Apr  3 11:29:55 kirk kernel: [   24.524306] parport_pc 00:07: reported by Plug and Play ACPI
Apr  3 11:29:55 kirk kernel: [   24.524349] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr  3 11:29:55 kirk kernel: [   24.537293] nvidia: module license 'NVIDIA' taints kernel.
Apr  3 11:29:55 kirk kernel: [   24.537296] Disabling lock debugging due to kernel taint
Apr  3 11:29:55 kirk kernel: [   24.577427] type=1400 audit(1333448994.049:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=464 comm="apparmor_parser"
Apr  3 11:29:55 kirk kernel: [   24.577787] type=1400 audit(1333448994.049:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=464 comm="apparmor_parser"
Apr  3 11:29:55 kirk kernel: [   24.578016] type=1400 audit(1333448994.049:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=464 comm="apparmor_parser"
Apr  3 11:29:55 kirk kernel: [   24.640395] lp0: using parport0 (interrupt-driven).
Apr  3 11:29:55 kirk kernel: [   24.874416] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  3 11:29:55 kirk kernel: [   24.874425] nvidia 0000:01:00.0: setting latency timer to 64
Apr  3 11:29:55 kirk kernel: [   24.874430] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Apr  3 11:29:55 kirk kernel: [   24.875073] ppdev: user-space parallel port driver
Apr  3 11:29:55 kirk kernel: [   24.876956] NVRM: loading NVIDIA UNIX x86 Kernel Module  295.33  Sat Mar 17 14:56:23 PDT 2012
Apr  3 11:29:55 kirk kernel: [   24.913541] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr  3 11:29:55 kirk kernel: [   24.913584] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
Apr  3 11:29:55 kirk kernel: [   24.913608] HDA Intel 0000:00:1b.0: setting latency timer to 64
Apr  3 11:29:55 kirk kernel: [   25.153964] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
Apr  3 11:29:55 kirk kernel: [   25.328100] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Apr  3 11:29:55 kirk kernel: [   25.367065] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
Apr  3 11:29:55 kirk kernel: [   25.367068] vesafb: scrolling: redraw
Apr  3 11:29:55 kirk kernel: [   25.367071] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Apr  3 11:29:55 kirk kernel: [   25.368425] vesafb: framebuffer at 0xd0000000, mapped to 0xfa880000, using 5120k, total 5120k
Apr  3 11:29:55 kirk kernel: [   25.368500] fbcon: VESA VGA (fb0) is primary device
Apr  3 11:29:55 kirk kernel: [   25.368586] Console: switching to colour frame buffer device 160x64
Apr  3 11:29:55 kirk kernel: [   25.368617] fb0: VESA VGA frame buffer device
```

---

