---
title: "After upgrade to trusty, cell phones won't mount as storage devices."
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by swajime on 2014-05-13
Before the upgrade, my cell phones (an HTC Vivid and a Samsung Note II) mounted just fine when I connected them via USB.  Now, the phones give no sign of being connected and Nautilus no longer launches with the drive contents.

From syslog:
May 13 18:06:55 desktop kernel: [519374.712067] usb 1-6: new high-speed USB device number 11 using ehci-pci
May 13 18:06:55 desktop kernel: [519374.844930] usb 1-6: New USB device found, idVendor=0bb4, idProduct=0cbb
May 13 18:06:55 desktop kernel: [519374.844938] usb 1-6: New USB device strings: Mfr=2, Product=3, SerialNumber=4
May 13 18:06:55 desktop kernel: [519374.844943] usb 1-6: Product: Android Phone
May 13 18:06:55 desktop kernel: [519374.844948] usb 1-6: Manufacturer: HTC
May 13 18:06:55 desktop kernel: [519374.844952] usb 1-6: SerialNumber: HT1B3VJ03406
May 13 18:06:55 desktop kernel: [519374.846896] usb-storage 1-6:1.0: USB Mass Storage device detected
May 13 18:06:55 desktop kernel: [519374.847025] scsi9 : usb-storage 1-6:1.0
May 13 18:06:55 desktop mtp-probe: checking bus 1, device 11: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6"
May 13 18:06:55 desktop mtp-probe: bus: 1, device: 11 was not an MTP device
May 13 18:06:56 desktop kernel: [519375.844711] scsi 9:0:0:0: Direct-Access     HTC      Android Phone    0000 PQ: 0 ANSI: 2
May 13 18:06:56 desktop kernel: [519375.845202] scsi 9:0:0:1: Direct-Access     HTC      Android Phone    0000 PQ: 0 ANSI: 2
May 13 18:06:56 desktop kernel: [519375.845621] sd 9:0:0:0: Attached scsi generic sg2 type 0
May 13 18:06:56 desktop kernel: [519375.845903] sd 9:0:0:1: Attached scsi generic sg3 type 0
May 13 18:06:56 desktop kernel: [519375.849949] sd 9:0:0:0: [sdb] Attached SCSI removable disk
May 13 18:06:56 desktop kernel: [519375.855586] sd 9:0:0:1: [sdc] Attached SCSI removable disk

Output from lsusb:
     Bus 001 Device 010: ID 0bb4:0cbb HTC (High Tech Computer Corp.)

How do I fix this?

---

### Post by squakie on 2014-05-13
There is a bug report on launchpad for this - it goes beyond just your phone - many devices are affected.  There is a work-around that works for some:

[https://bugs.launchpad.net/ubuntu/+s...s/+bug/1296275](https://bugs.launchpad.net/ubuntu/+s...s/+bug/1296275)

---

### Post by swajime on 2014-05-14
Thank you.  I hope this gets fixed soon.

---

### Post by monkeybrain20122 on 2014-05-14
> **squakie said:**
> There is a bug report on launchpad for this - it goes beyond just your phone - many devices are affected.  There is a work-around that works for some:

[https://bugs.launchpad.net/ubuntu/+s...s/+bug/1296275](https://bugs.launchpad.net/ubuntu/+s...s/+bug/1296275)

Your link doesn't work.

---

### Post by ubfan1 on 2014-05-14
Try [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1296275](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1296275)
Also try installing mtp-tools and mtpfs

---

### Post by ubfan1 on 2014-05-14
Try [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1296275](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1296275)
Also try installing mtp-tools and mtpfs
The below worked for my Kindle, which initially didn't show:

The dmesg tail does not show any usb storage when Kindle is plugged in.
Double check the cable.  Only the true data USB-microUSB works, some power adapter
cables do not.

sudo mtpfs /mnt/mtp 
successfully mounts the Kindle.

lsusb should show the device 1947:0007

Unmount with:
sudo fusermount -u /mnt/mtp

---

### Post by squakie on 2014-05-17
BTW - I was looking at this thread because of a similar problem with a USB camera.  lsusb shows my camera as always.  probe-mtp fails saying it isn't an mtp device, so there are no mtp devices to mount (the mtpfs /mnt/mtp mounts the first available mtp device).  As a result still not able to access my camera.  Only adding this here in case someone with a cell phone has a similar problem and are looking at this thread.

---

