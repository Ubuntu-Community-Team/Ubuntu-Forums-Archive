---
title: "CameraMonitor no longer works in Karmic."
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-13
CLI text:
"/usr/bin/cameramonitor:76: DeprecationWarning: os.popen3 is deprecated.  Use the subprocess module.
  text = os.popen3('fuser '+self.video_device, 'r')[1].read()"

This is used to test webcams.

lsusb:
Bus 004 Device 003: ID 046d:092e Logitech, Inc. QuickCam Chat
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 045e:00dd Microsoft Corp. 
Bus 003 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I DO get image with "gstreamer-properties".

---

### Post by emarkay on 2009-10-28
Well it's almost Lucid time - no one else uses webcams here?

---

