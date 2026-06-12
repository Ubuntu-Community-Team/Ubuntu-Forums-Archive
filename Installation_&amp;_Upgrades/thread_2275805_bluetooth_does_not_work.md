---
title: "bluetooth does not work"
date: 2015-04-28
forum: Installation &amp; Upgrades
---

### Post by kbuntu1 on 2015-04-28
I have a new install of Xubuntu 15.04 on a new IdeaPad Z50/70. Bluetooth is not working: the service won't start. I can manually start the service on the command line, but the bluetooth manager does not see the device.

When I start the service, it shows:
```

bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2015-04-28 19:08:32 BST; 2min 1s ago
 Main PID: 2276 (bluetoothd)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;2276 /usr/sbin/bluetoothd -n

Apr 28 19:08:32 laptop bluetoothd[2276]: Failed to init alert plugin
Apr 28 19:08:32 laptop bluetoothd[2276]: Failed to init thermometer plugin
Apr 28 19:08:32 laptop bluetoothd[2276]: bluetoothd[2276]: Failed to init proximity plugin
Apr 28 19:08:32 laptop bluetoothd[2276]: bluetoothd[2276]: Failed to init time plugin
Apr 28 19:08:32 laptop bluetoothd[2276]: bluetoothd[2276]: Failed to init alert plugin
Apr 28 19:08:32 laptop bluetoothd[2276]: bluetoothd[2276]: Failed to init thermometer plugin
Apr 28 19:08:32 laptop bluetoothd[2276]: Failed to init gatt_example plugin
Apr 28 19:08:32 laptop bluetoothd[2276]: Bluetooth Management interface initialized
Apr 28 19:08:32 laptop bluetoothd[2276]: bluetoothd[2276]: Failed to init gatt_example plugin
Apr 28 19:08:32 laptop bluetoothd[2276]: bluetoothd[2276]: Bluetooth Management interface initialized

```

Note that dmesg  and lspci show nothing about a bluetooth device.

---

### Post by kbuntu1 on 2015-04-28
lsusb shows a device with no description:
```

Bus 001 Device 004: ID 105b:e065  

```
Web searching suggests this is my bluetooth device, but I'm unsure how to get this recognized/

---

### Post by kbuntu1 on 2015-04-28
I found a solution for Debian Jesse [http://www.gnebehay.com/blog/lenovo-flexpad-bluetooth-debian/](http://www.gnebehay.com/blog/lenovo-flexpad-bluetooth-debian/) that seems to work.

---

