---
title: "USB Drive"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by elky10 on 2005-10-17
I have a 256mB SanDisk cruzer mini flash drive, and I just upgraded to Breezy.  Before, I would put it in, and I would get a link for the drive.  Now, nothing. What gives?

---

### Post by Murgle on 2005-10-17
does anything appear on the desktop?  it should, that and a nautilus window should pop up...  also if that doesn't work can you show us your 'dmesg' output, there should be a few lines at the very end talking about your flash drive, for example mine says 

 Initializing USB Mass Storage driver...
[4333612.269000] scsi2 : SCSI emulation for USB Mass Storage devices
[4333612.271000] usb-storage: device found at 3
[4333612.271000] usb-storage: waiting for device to settle before scanning
[4333612.271000] usbcore: registered new driver usb-storage
[4333612.271000] USB Mass Storage support registered.
[4333617.271000]   Vendor: PNY       Model: Attache 2.0       Rev: 4.70
[4333617.271000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4333617.279000] usb-storage: device scan complete
[4333617.451000] SCSI device sda: 239872 512-byte hdwr sectors (123 MB)
[4333617.451000] sda: Write Protect is off
[4333617.451000] sda: Mode Sense: 45 00 00 08
[4333617.451000] sda: assuming drive cache: write through
[4333617.455000] SCSI device sda: 239872 512-byte hdwr sectors (123 MB)
[4333617.455000] sda: Write Protect is off
[4333617.455000] sda: Mode Sense: 45 00 00 08
[4333617.455000] sda: assuming drive cache: write through
[4333617.455000]  /dev/scsi/host2/bus0/target0/lun0: p1
[4333617.459000] Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
[4333619.429000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

Edit: 
it seems that in breezy it no longer appears on the desktop, but it appears on the places menu and in nautilus on the sidebar.

---

### Post by elky10 on 2005-10-17
Nothing shows up, but here's my dmesg:

```
a on isa0060/serio0).
[4302858.363000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302858.867000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302858.867000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302859.111000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302859.111000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302859.303000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302859.303000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302859.657000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302859.657000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302859.884000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302859.884000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302860.248000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302860.248000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302860.442000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302860.442000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302860.773000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302860.773000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302860.944000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302860.944000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302861.196000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302861.196000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302861.651000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302861.651000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302861.804000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302861.804000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302862.861000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302862.861000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302862.889000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302862.889000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302863.274000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302863.274000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302863.559000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302863.559000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302863.835000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302863.835000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302864.117000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302864.117000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302864.279000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302864.279000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302869.319000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302869.319000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302869.952000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302869.952000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302870.239000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302870.239000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302870.950000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302870.950000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302871.207000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302871.207000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302871.429000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302871.429000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302871.620000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302871.620000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302872.260000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302872.260000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302872.497000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302872.497000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302873.426000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302873.426000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302873.849000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302873.849000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302874.892000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302874.892000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302875.213000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302875.213000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302875.951000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302875.951000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302878.395000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302878.395000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302879.068000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302879.068000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302879.287000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302879.287000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302879.460000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302879.460000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302879.587000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302879.587000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302880.575000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302880.575000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302880.842000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302880.842000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302881.220000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302881.220000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302881.421000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302881.421000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302881.959000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302881.959000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302882.229000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302882.229000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302882.967000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302882.967000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302883.705000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302883.705000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302883.970000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302883.970000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302884.217000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302884.217000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302884.849000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302884.849000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302885.127000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302885.127000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302885.918000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302885.918000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302886.420000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302886.420000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302887.114000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302887.114000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302887.389000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302887.389000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302888.253000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302888.253000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302888.516000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302888.516000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302889.162000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302889.162000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302889.376000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302889.376000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302890.062000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302890.062000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302890.283000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302890.283000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302891.037000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302891.037000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302891.195000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302891.195000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302891.707000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302891.707000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302891.949000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302891.949000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302892.651000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302892.651000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302893.219000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302893.219000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302893.446000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302893.446000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302893.670000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302893.670000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302893.832000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302893.832000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302894.056000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302894.056000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302894.240000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302894.240000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302894.673000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302894.673000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302894.865000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302894.865000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302895.094000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302895.094000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302895.261000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302895.261000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302895.519000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302895.519000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302895.694000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302895.694000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302895.913000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302895.913000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302896.672000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302896.672000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302896.919000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302896.919000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302897.767000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302897.767000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302901.445000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302901.445000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302901.608000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302901.608000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302902.739000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4302902.739000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302909.179000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302909.179000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303112.276000] usb 1-1: new full speed USB device using uhci_hcd and address 6[4303112.408000] scsi2 : SCSI emulation for USB Mass Storage devices
[4303112.411000] usb-storage: device found at 6
[4303112.411000] usb-storage: waiting for device to settle before scanning
[4303117.413000]   Vendor: SanDisk   Model: Cruzer Mini       Rev: 0.2
[4303117.413000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4303117.421000] SCSI device sda: 501759 512-byte hdwr sectors (257 MB)
[4303117.425000] sda: Write Protect is off
[4303117.425000] sda: Mode Sense: 03 00 00 00
[4303117.425000] sda: assuming drive cache: write through
[4303117.439000] SCSI device sda: 501759 512-byte hdwr sectors (257 MB)
[4303117.444000] sda: Write Protect is off
[4303117.444000] sda: Mode Sense: 03 00 00 00
[4303117.444000] sda: assuming drive cache: write through
[4303117.444000]  /dev/scsi/host2/bus0/target0/lun0: p1
[4303117.454000] Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
[4303117.457000] usb-storage: device scan complete

```

---

### Post by Murgle on 2005-10-17
when you look at the places menu is there anything there?  mine shows up in the same group as computer.  it is also default mounted to /media/nameofdrive you should check there as well.

---

