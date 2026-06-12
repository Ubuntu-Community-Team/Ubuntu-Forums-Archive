---
title: "Painfully slow boot times - 2m 26s"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by dudds on 2008-03-14
I have just installed Xubuntu and the boot times are painfully slow!!! So slow in fact that I was just about to reboot my laptop because I thought the process had hung. It takes fully 2 minutes and 56 seconds to boot from the time I turn power on.

During this time the screen is blank but there is disk activity. Not enough to see the disk light solidly hit as when I load a program, but flickering on and off extremely fast.

I have pasted a portion of the output from the dmesg command which to a novice like me seems to be relevant. I installed from the live CD and had an external USB drive connected during the installation process if that makes any difference.

Anyway message output follows. Any help appreciated as this is driving me nuts.

I should also mention that during this bootup period the screen is blank with no indication as to what is happening.

[   30.356794]  sda:<6>input: Logitech USB Receiver as /class/input/input3
[   30.367595] input,hiddev96: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2
[   30.367608] usbcore: registered new interface driver usbhid
[   30.367611] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   30.823588]  sda1 sda2 sda3
[   30.839690] sd 0:0:0:0: [sda] Attached SCSI disk
[   30.843289] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   30.843307] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   30.851848] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   30.851852] Uniform CD-ROM driver Revision: 3.20
[   30.851899] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   31.200449] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040d001002b3d8a]
[   31.935085] Attempting manual resume
[   31.935088] swsusp: Resume From Partition 8:2
[   31.935090] PM: Checking swsusp image.
[   32.031908] PM: Resume from disk failed.
[   32.739572] kjournald starting.  Commit interval 5 seconds
[   32.739581] EXT3-fs: mounted filesystem with ordered data mode.
[  114.239218] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  115.710079] NET: Registered protocol family 17
[  124.111696] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  124.127601] Linux agpgart interface v0.102 (c) Dave Jones
[  124.129929] agpgart: Detected an Intel 855PM Chipset.

---

### Post by dudds on 2008-03-14
For those of you who may be experiencing the same problems out there I fixed this problem by editing the file /etc/usplash.conf.

The settings in this file were:

xres=1280
yres=1024

The yres setting was incorrect for my laptop display. I edited to be:

xres=1280
yres=800

and now boot times are around 45 seconds. Much better. Also while booting up now I can see the Xubuntu screen displayed.

---

