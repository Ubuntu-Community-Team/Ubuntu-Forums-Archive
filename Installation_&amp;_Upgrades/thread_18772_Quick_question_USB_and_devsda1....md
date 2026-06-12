---
title: "Quick question: USB and /dev/sda1..."
date: 2005-03-08
forum: Installation &amp; Upgrades
---

### Post by total-noob on 2005-03-08
USB memory sticks have never really been working on my Ubuntu box (but it does with Windows  :-x  ). I didn't have any /dev/sda or /dev/sda1 (I have six ports, but only use one), so I created these:
```

sudo mknod /dev/sda b 8 0
sudo mknod /dev/sda1 b 8 1
```/proc/bus/usb does exist and looks almost right to me, even though I have a feeling that a drivers file is missing:
```

dr-xr-xr-x    2 root     root            0 2005-03-08 15:48 001
dr-xr-xr-x    2 root     root            0 2005-03-08 15:48 002
dr-xr-xr-x    2 root     root            0 2005-03-08 15:48 003
-r--r--r--    1 root     root            0 2005-03-08 15:48 devices
```But when I look for /proc/scsi, it doesn't exist - isn't it suppose to be there to support the USB memory stick as a SCSI device? What about you guys? Don't you have that  /proc/scsi on your systems?

Anxiously awaiting feedback - desperately need to this USB stuff sorted out!  :-?

---

### Post by alastair on 2005-03-08
What version of Ubuntu? I don't think the device nodes /need/ creating - this is something the hotplug/udev subsystem should take care of - at least on Hoary.

For instance - on my laptop - no /dev/sda1.

If I plug in a USB key, I see the following in my /var/log/syslog :

```

Mar  8 23:29:13 muse kernel: usb 2-1: new full speed USB device using uhci_hcd and address 2
Mar  8 23:29:14 muse usb.agent[10128]:      usb-storage: loaded successfully
Mar  8 23:29:19 muse kernel: SCSI subsystem initialized
Mar  8 23:29:19 muse kernel: Initializing USB Mass Storage driver...
Mar  8 23:29:19 muse kernel: scsi0 : SCSI emulation for USB Mass Storage devices
Mar  8 23:29:19 muse kernel: usbcore: registered new driver usb-storage
Mar  8 23:29:19 muse kernel: USB Mass Storage support registered.
Mar  8 23:29:19 muse kernel: usb-storage: device found at 2
Mar  8 23:29:19 muse kernel: usb-storage: waiting for device to settle before scanning
Mar  8 23:29:19 muse kernel:   Vendor: LEXAR     Model: DIGITAL FILM      Rev: /W1.
Mar  8 23:29:19 muse kernel:   Type:   Direct-Access                      ANSI SCSI revision: 02
Mar  8 23:29:19 muse kernel: usb-storage: device scan complete
Mar  8 23:29:19 muse kernel: SCSI device sda: 125952 512-byte hdwr sectors (64 MB)
Mar  8 23:29:19 muse scsi.agent[10282]:      sd_mod: loaded sucessfully
Mar  8 23:29:19 muse udev[10325]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sda' becomes '%k'
Mar  8 23:29:19 muse udev[10325]: creating device node '/dev/sda'
Mar  8 23:29:19 muse udev[10338]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sda1' becomes '%k'
Mar  8 23:29:19 muse udev[10338]: creating device node '/dev/sda1'

```

and I have a /dev/sda1 created.

Have a shell open and "tail -f" your system log i.e.

sudo tail -f /var/log/syslog

Then plug in the USB device. Anything printed?

---

### Post by total-noob on 2005-03-09
I plugged the UBS memory stick in after having booted and logged in, and the LED in the Memory stick did not even turn on. Using the tail command gave no result at all.    :sad: 

Searching through my /var/log/syslog, I have found faint indications that there should be some USB support:

```
Mar  9 16:30:11 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
...
Mar  9 16:30:11 localhost kernel: P0P1 UAR1 USB0 USB1 USB2 USB3 AC97 SLPB 
...
Mar  9 16:30:11 localhost kernel: usbcore: registered new driver usbfs
Mar  9 16:30:11 localhost kernel: usbcore: registered new driver hub
Mar  9 16:30:11 localhost kernel: USB Universal Host Controller Interface driver v2.2
Mar  9 16:30:11 localhost kernel: ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
Mar  9 16:30:11 localhost kernel: uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB (ICH4) USB UHCI #1
Mar  9 16:30:11 localhost kernel: PCI: Setting latency timer of device 0000:00:1d.0 to 64
Mar  9 16:30:11 localhost kernel: uhci_hcd 0000:00:1d.0: irq 169, io base 0000e800
Mar  9 16:30:11 localhost kernel: uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Mar  9 16:30:11 localhost kernel: hub 1-0:1.0: USB hub found
Mar  9 16:30:11 localhost kernel: hub 1-0:1.0: 2 ports detected
Mar  9 16:30:11 localhost kernel: ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 177
Mar  9 16:30:11 localhost kernel: uhci_hcd 0000:00:1d.1: Intel Corp. 82801DB (ICH4) USB UHCI #2
Mar  9 16:30:11 localhost kernel: PCI: Setting latency timer of device 0000:00:1d.1 to 64
Mar  9 16:30:11 localhost kernel: uhci_hcd 0000:00:1d.1: irq 177, io base 0000e880
Mar  9 16:30:11 localhost kernel: uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Mar  9 16:30:11 localhost kernel: hub 2-0:1.0: USB hub found
Mar  9 16:30:11 localhost kernel: hub 2-0:1.0: 2 ports detected
Mar  9 16:30:11 localhost kernel: ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
Mar  9 16:30:11 localhost kernel: uhci_hcd 0000:00:1d.2: Intel Corp. 82801DB (ICH4) USB UHCI #3
Mar  9 16:30:11 localhost kernel: PCI: Setting latency timer of device 0000:00:1d.2 to 64
Mar  9 16:30:11 localhost kernel: uhci_hcd 0000:00:1d.2: irq 185, io base 0000ec00
Mar  9 16:30:11 localhost kernel: uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Mar  9 16:30:11 localhost kernel: hub 3-0:1.0: USB hub found
Mar  9 16:30:11 localhost kernel: hub 3-0:1.0: 2 ports detected
Mar  9 16:30:11 localhost kernel: ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 193
Mar  9 16:30:11 localhost kernel: ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB (ICH4) USB2 EHCI Controller
Mar  9 16:30:11 localhost kernel: ehci_hcd 0000:00:1d.7: BIOS handoff failed (104, 1010001)
Mar  9 16:30:11 localhost kernel: ehci_hcd 0000:00:1d.7: can't reset
Mar  9 16:30:11 localhost kernel: ehci_hcd 0000:00:1d.7: init 0000:00:1d.7 fail, -95
Mar  9 16:30:11 localhost kernel: ehci_hcd: probe of 0000:00:1d.7 failed with error -95
```What is it all about with the errors?

Okay, I tried rebooting with the memory stick plugged in and things were quite different. This time it was detected as seen in /var/log/syslog below:

```
Mar  9 17:11:02 localhost kernel: usb 3-1: new full speed USB device using address 2
Mar  9 17:11:02 localhost kernel: SCSI subsystem initialized
Mar  9 17:11:02 localhost kernel: Initializing USB Mass Storage driver...
Mar  9 17:11:02 localhost kernel: scsi0 : SCSI emulation for USB Mass Storage devices
Mar  9 17:11:02 localhost kernel:   Vendor: GENERIC   Model: USB FLASH DISK    Rev: 0302
Mar  9 17:11:02 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 02
Mar  9 17:11:02 localhost kernel: USB Mass Storage device found at 2
Mar  9 17:11:02 localhost kernel: usbcore: registered new driver usb-storage
Mar  9 17:11:02 localhost kernel: USB Mass Storage support registered.
Mar  9 17:11:02 localhost kernel: SCSI device sda: 32000 512-byte hdwr sectors (16 MB)
Mar  9 17:11:02 localhost kernel: sda: Write Protect is off
Mar  9 17:11:02 localhost kernel: sda: Mode Sense: 00 00 00 00
Mar  9 17:11:02 localhost kernel: sda: assuming drive cache: write through
Mar  9 17:11:02 localhost kernel:  /dev/scsi/host0/bus0/target0/lun0: p1
Mar  9 17:11:02 localhost kernel: Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
Mar  9 17:11:02 localhost kernel: ehci_hcd 0000:00:1d.7: BIOS handoff failed (104, 1010001)
Mar  9 17:11:02 localhost kernel: ehci_hcd 0000:00:1d.7: can't reset
Mar  9 17:11:02 localhost kernel: ehci_hcd 0000:00:1d.7: init 0000:00:1d.7 fail, -95
Mar  9 17:11:02 localhost kernel: ehci_hcd: probe of 0000:00:1d.7 failed with error -95
Mar  9 17:11:02 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Mar  9 17:11:02 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar  9 17:11:02 localhost kernel: shpchp: shpc_init : shpc_cap_offset == 0
Mar  9 17:11:02 localhost kernel: shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar  9 17:11:02 localhost kernel: pciehp: PCI Express Hot Plug Controller Driver version: 0.4
```Earlier I had added this to /etc/fstab:

```
none /proc/bus/usb usbdevfs defaults 0 0
```The memory stick was mounted and ready for use as I wanted - but I don't like the idea of rebooting to get access. Pulling out the memory stick and inserting a new one fails.    :neutral:  

Any ideas? Shouldn't all of this have been handled automatically?

---

### Post by alastair on 2005-03-09
Yes, it should happen automatically but things are still progressing in Linux land. But believe me, they ARE progressing.

I think it is generally hard to support so much different hardware nowadays but we're getting there.

I assume this is "warty"? I hope, and expect, things to be much better once you upgrade to the next version "Hoary". 

I am running Hoary and things seem to generally work for me. I don't mount "usbdevfs" explicitly - but this is now "usbfs" anyway. Even though my fstab does not mount this, I still have :

root@muse:/home/alastair # mount
....
usbfs on /proc/bus/usb type usbfs (rw)

So, things should look up for you soon.

---

