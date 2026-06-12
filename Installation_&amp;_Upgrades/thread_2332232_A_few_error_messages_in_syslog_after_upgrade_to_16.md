---
title: "A few error messages in syslog after upgrade to 16.04.1"
date: 2016-07-29
forum: Installation &amp; Upgrades
---

### Post by David_Partridge on 2016-07-29
Saw these in syslog:

```
Jul 29 19:02:28 Charon kernel: [   15.849944] BTRFS error (device dm-0): could not find root 8
Jul 29 19:02:28 Charon kernel: [   15.854443] BTRFS error (device dm-0): could not find root 8

Jul 29 19:02:28 Charon gpu-manager[3595]: Error: can't open /lib/modules/4.4.0-31-generic/updates/dkms
Jul 29 19:02:28 Charon gpu-manager[3595]: Error: can't open /lib/modules/4.4.0-31-generic/updates/dkms

Jul 29 19:02:29 Charon gpu-manager[3595]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf

Jul 29 19:02:30 Charon whoopsie[3577]: [19:02:30] GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: No such property 'state'
Jul 29 19:02:30 Charon NetworkManager[3644]: <info>  [1469815350.0970] ofono is now available
Jul 29 19:02:30 Charon NetworkManager[3644]: <info>  [1469815350.0975] bluez: use BlueZ version 5
Jul 29 19:02:30 Charon NetworkManager[3644]: <warn>  [1469815350.1045] failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Jul 29 19:02:30 Charon NetworkManager[3644]: <info>  [1469815350.1051] ModemManager available in the bus
Jul 29 19:02:30 Charon systemd[1]: Starting WPA supplicant...
Jul 29 19:02:30 Charon dbus[3619]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jul 29 19:02:30 Charon wpa_supplicant[3703]: Successfully initialized wpa_supplicant
Jul 29 19:02:30 Charon systemd[1]: Started WPA supplicant.
Jul 29 19:02:30 Charon NetworkManager[3644]: <info>  [1469815350.3380] supplicant: wpa_supplicant running
Jul 29 19:02:30 Charon NetworkManager[3644]: <info>  [1469815350.3381] device (wlan0): supplicant interface state: init -> starting
Jul 29 19:02:30 Charon wpa_supplicant[3703]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Jul 29 19:02:30 Charon wpa_supplicant[3703]: dbus: Failed to construct signal

```

I don't know it they are important or not!

Thanks
Dave

---

