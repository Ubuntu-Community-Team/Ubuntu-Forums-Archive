---
title: "Lirc and mceusb on karmic"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sandos on 2009-10-20
Just upgraded my htpc from jaunty to karmic. My first problem is that lirc does not seem to work. Starting XBMC, it doesn't respond to keys. 'irw' gives my absolutely nothing. After configuring lirc with the correct remote (afaik) dmesg gives this on plugging in the dongle:

> 
[  298.033668] usbcore: deregistering interface driver lirc_mceusb
[  298.035390] lirc_mceusb[2]: usb remote disconnected
[  313.000540] lirc_dev: IR Remote Control driver registered, major 61
[  313.009609] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[  313.009617] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[  313.120083] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[  313.270905] lirc_dev: lirc_register_driver: sample_rate: 0
[  313.276897] lirc_mceusb[2]: Philips eHome Infrared Transceiver on usb3:2
[  313.276977] usbcore: registered new interface driver lirc_mceusb


---

### Post by pezlin on 2009-10-21
I have the same problem after upgrading from Jaunty to Karmic. I have also tried to install Karmic from scratch but no luck. I have the VLsystem mplay remote.

---

### Post by sandos on 2009-10-21
Actually, seems to be working after simply rebooting!

---

### Post by jis on 2009-10-21
Reboot doesn't solve the problem here. I have "VLSystem MPlay Blast" remote. For what it is worth, if I remember right, I have applied some partial upgrades offered by Update Manager; see [http://ubuntuforums.org/showthread.php?t=1286309](http://ubuntuforums.org/showthread.php?t=1286309)

---

### Post by pezlin on 2009-10-22
> **jis said:**
> Reboot doesn't solve the problem here. I have "VLSystem MPlay Blast" remote. For what it is worth, if I remember right, I have applied some partial upgrades offered by Update Manager; see [http://ubuntuforums.org/showthread.php?t=1286309](http://ubuntuforums.org/showthread.php?t=1286309)
I have tried to reinstall Karmic Beta, skipped the partial update but accepted all other updates. Still no luck. I have the VLSystem Mplay Blast as well.

---

### Post by jis on 2009-10-23
I posted a bug report about this at [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/459021](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/459021)

---

