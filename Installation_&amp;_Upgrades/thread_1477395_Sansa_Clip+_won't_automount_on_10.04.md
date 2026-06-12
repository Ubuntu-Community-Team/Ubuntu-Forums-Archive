---
title: "Sansa Clip+ won't automount on 10.04"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by jonthysell on 2010-05-08
I just upgraded from 9.10 x64 to 10.04 x64 on my desktop. My Sansa Clip+ (USB mass storage mp3 player with SD card slot) stopped auto mounting. It worked fine in 9.10.

dmesg:
```
[   56.290051] usb 1-5: new high speed USB device using ehci_hcd and address 4
[   56.360222] hub 1-0:1.0: unable to enumerate USB device on port 5
[   58.190018] usb 1-5: new high speed USB device using ehci_hcd and address 5
[   58.341823] usb 1-5: configuration #1 chosen from 1 choice
[   58.349068] scsi5 : SCSI emulation for USB Mass Storage devices
[   58.349303] usb-storage: device found at 5
[   58.349306] usb-storage: waiting for device to settle before scanning
[   63.340330] usb-storage: device scan complete
[   84.131307] usb 1-5: reset high speed USB device using ehci_hcd and address 5
[   84.510099] usb 1-5: reset high speed USB device using ehci_hcd and address 5
```

lsusb:
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e3:070e Genesys Logic, Inc. X-PRO CR20xA USB 2.0 Internal Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 011: ID 0781:74d0 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Any help please? I need to sync FLOSS Weekly!

---

### Post by jonthysell on 2010-05-08
I found the solution. It seems the Clip+ can be used in either MTP or MSC (mass storage) modes. When set to auto-detect, in 9.10 the MSC mode is used. In 10.04, MTP is used.

On the device I chose Settings -> System Settings -> USB Mode -> MSC , and now it mounts perfectly in 10.04.

---

### Post by KegHead on 2010-05-21
Hi!

Thank you so much for this info!

Worked perfectly!

KegHead

---

### Post by Ahunt on 2010-05-24
Thanks for solving this and for posting the answer! The solution worked perfectly!

---

### Post by ubnewbie2 on 2010-05-29
> **jonthysell said:**
> I found the solution. It seems the Clip+ can be used in either MTP or MSC (mass storage) modes. When set to auto-detect, in 9.10 the MSC mode is used. In 10.04, MTP is used.

On the device I chose Settings -> System Settings -> USB Mode -> MSC , and now it mounts perfectly in 10.04.

I have an ebook reader that cannot be switched to a different mode.  Is there a way to tell 10.04 to use MTP like 9.10 did?

---

### Post by KegHead on 2010-05-29
Hi!

What type of reader?

I have a Sony w/no problems.

KegHead

---

### Post by ubnewbie2 on 2010-05-29
> **KegHead said:**
> Hi!

What type of reader?

I have a Sony w/no problems.

KegHead

I solved the problem last night late.   It was a firmware problem.  I updated the firmware and it works again. (it was a Astak/Hanlin/BeBook reader)

---

### Post by saxonjf on 2010-11-27
> **jonthysell said:**
> I found the solution. It seems the Clip+ can be used in either MTP or MSC (mass storage) modes. When set to auto-detect, in 9.10 the MSC mode is used. In 10.04, MTP is used.

On the device I chose Settings -> System Settings -> USB Mode -> MSC , and now it mounts perfectly in 10.04.

Works right.. thanks so much

---

