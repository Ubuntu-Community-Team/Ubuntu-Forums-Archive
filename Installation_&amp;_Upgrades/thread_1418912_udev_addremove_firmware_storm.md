---
title: "udev add/remove firmware storm"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by gisborne on 2010-03-01
Just upgraded my mythbuntu box to Karmic. I am now getting lines like the below endlessly, about three lines per second. Periodically (hourly?) I have to sudo killall udevd or I can't use it for anything. Grateful for any advice.

#udevadm monitor
KERNEL[1267443811.520300] remove   /devices/pci0000:00/0000:00:09.0/0000:01:05.0/firmware/0000:01:05.0 (firmware)
UDEV  [1267443811.521995] remove   /devices/pci0000:00/0000:00:09.0/0000:01:05.0/firmware/0000:01:05.0 (firmware)
UDEV  [1267443811.529913] add      /devices/pci0000:00/0000:00:09.0/0000:01:05.0/firmware/0000:01:05.0 (firmware)
KERNEL[1267443812.020483] add      /devices/pci0000:00/0000:00:09.0/0000:01:05.0/firmware/0000:01:05.0 (firmware)
KERNEL[1267443812.025822] remove   /devices/pci0000:00/0000:00:09.0/0000:01:05.0/firmware/0000:01:05.0 (firmware)
UDEV  [1267443812.027113] remove   /devices/pci0000:00/0000:00:09.0/0000:01:05.0/firmware/0000:01:05.0 (firmware)
UDEV  [1267443812.036544] add      /devices/pci0000:00/0000:00:09.0/0000:01:05.0/firmware/0000:01:05.0 (firmware)

---

### Post by gisborne on 2010-03-02
Bump

---

### Post by gisborne on 2010-03-03
Bump. This thing is bringing my system to its knees. No-one can help?

---

