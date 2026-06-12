---
title: "Slow boot with fresh Ubuntu 20.04"
date: 2021-02-02
forum: Installation &amp; Upgrades
---

### Post by memdisk on 2021-02-02
Hello,

I did a fresh install with Ubuntu 20.04 on a Thinkpad X1C and experience a slow boot time. With **systemd-analyse** I found the delay is in the kernel part which takes 33 seconds. Checking the dmesg log shows this suspicious line:

```
[Di Feb  2 16:38:24 2021] hidraw: raw HID events driver (C) Jiri Kosina
[Di Feb  2 16:38:24 2021] ish-hid {33AECD58-B679-4E54-9BD9-A04D34F0C226}: [hid-ish]: enum_devices_done OK, num_hid_devices=2
[Di Feb  2 16:38:24 2021] hid-generic 001F:8086:0001.0001: hidraw0: <UNKNOWN> HID v2.00 Device [hid-ishtp 8086:0001] on 
[Di Feb  2 16:38:24 2021] hid-generic 001F:0000:0000.0002: hidraw1: <UNKNOWN> HID v2.00 Device [hid-ishtp 0000:0000] on 
[Di Feb  2 16:38:24 2021] usb 1-8: New USB device found, idVendor=04f2, idProduct=b5c1, bcdDevice= 0.04
[Di Feb  2 16:38:24 2021] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[Di Feb  2 16:38:24 2021] usb 1-8: Product: Integrated Camera
[Di Feb  2 16:38:24 2021] usb 1-8: Manufacturer: Chicony Electronics Co.,Ltd.
[Di Feb  2 16:38:24 2021] usb 1-9: new full-speed USB device number 5 using xhci_hcd
[Di Feb  2 16:38:24 2021] psmouse serio1: synaptics: queried max coordinates: x [..5678], y [..4754]
[Di Feb  2 16:38:24 2021] psmouse serio1: synaptics: queried min coordinates: x [1262..], y [1098..]
[Di Feb  2 16:38:24 2021] psmouse serio1: synaptics: Your touchpad (PNP: LEN0058 PNP0f13) says it can support a different bus. If i2c-hid and hid-rmi are not used, you might want to try setting psmouse.synaptics_intertouch to 1 and report this to linux-input@vger.kernel.org.
[Di Feb  2 16:38:24 2021] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.2, id: 0x1e2b1, caps: 0xf002a3/0x940300/0x12e800/0x0, board id: 3144, fw id: 2059155
[Di Feb  2 16:38:24 2021] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[Di Feb  2 16:38:24 2021] usb 1-9: New USB device found, idVendor=138a, idProduct=0090, bcdDevice= 1.64
[Di Feb  2 16:38:24 2021] usb 1-9: New USB device strings: Mfr=0, Product=0, SerialNumber=1
[Di Feb  2 16:38:24 2021] usb 1-9: SerialNumber: 216f80ed1493
[Di Feb  2 16:38:24 2021] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[Di Feb  2 16:38:25 2021] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
** [Di Feb  2 16:38:25 2021] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input7**
[Di Feb  2 16:38:56 2021] EXT4-fs (nvme0n1p2): mounted filesystem with ordered data mode. Opts: (null)
```

For me it seems the bolded line with the trackpoint driver adds this unnecessary delay of about 30 seconds. Before there was 16.04 installed on the system which booted fast without this delay.

How can I debug/solve this boot delay issue?

---

### Post by memdisk on 2021-02-06
I was able to solve this issue. As I thought earlier it was **not** the trackpoint causing the delay.

It turned out the delay was caused by a wrong swap partition in **/etc/initramfs-tools/conf.d/resume** which the kernel was searching for about 30s until it timed out.

---

### Post by CelticWarrior on 2021-02-06
Ubuntu 20.04 doesn't need a swap partition, it uses by default a swapfile. Of course, if it finds a swap partition it'll use that instead of the swap file.
Keep this in mind for a future reinstallation.

---

