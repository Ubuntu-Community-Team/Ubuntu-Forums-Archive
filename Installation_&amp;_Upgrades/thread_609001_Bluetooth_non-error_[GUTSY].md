---
title: "Bluetooth non-error [GUTSY]"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by DocFox on 2007-11-10
Hi

Not sure if this is the correct forum for this - mods free to move it.

Just set up my phone to pair with bluetooth on 7.10, using the standard interface (Bluetooth Applet 0.14). Exchange keys fine and each device sees the other.

When I try to connect in either direction, the connection fails. Computer>phone I get the message:
> 
"obex://[00:1b:59:ae:b9:e5]" is not a valid location.

syslog says:

> Nov 10 20:56:46 nutmeg hcid[1064]: pin_code_request (sba=00:11:67:04:E7:9A, dba=00:1B:59:AE:B9:E5)
Nov 10 20:56:49 nutmeg hcid[1064]: link_key_notify (sba=00:11:67:04:E7:9A, dba=00:1B:59:AE:B9:E5)
Nov 10 20:56:50 nutmeg NetworkManager: <debug> [1194721010.032141] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1131_1001_noserial_if0_bluetooth_hci_bluetooth_hci').
Nov 10 20:56:52 nutmeg NetworkManager: <debug> [1194721012.702942] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1131_1001_noserial_if0_bluetooth_hci_bluetooth_hci').
Nov 10 20:56:53 nutmeg NetworkManager: <debug> [1194721013.441102] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1131_1001_noserial_if0_bluetooth_hci_bluetooth_hci').
Nov 10 20:57:02 nutmeg network[1153]: /org/bluez/network: org.bluez.network.Manager.ListConnections()
Nov 10 20:57:02 nutmeg input[1072]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 10 20:57:02 nutmeg audio[1073]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Nov 10 21:07:39 nutmeg hcid[1064]: link_key_request (sba=00:11:67:04:E7:9A, dba=00:1B:59:AE:B9:E5)
Nov 10 21:07:39 nutmeg NetworkManager: <debug> [1194721659.951271] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1131_1001_noserial_if0_bluetooth_hci_bluetooth_hci').
Nov 10 21:07:40 nutmeg NetworkManager: <debug> [1194721660.363006] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1131_1001_noserial_if0_bluetooth_hci_bluetooth_hci').
Nov 10 21:17:01 nutmeg /USR/SBIN/CRON[1848]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 10 21:28:49 nutmeg NetworkManager: <debug> [1194722929.533139] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1131_1001_noserial_if0_bluetooth_hci_bluetooth_hci').
Nov 10 21:28:49 nutmeg hcid[1064]: link_key_request (sba=00:11:67:04:E7:9A, dba=00:1B:59:AE:B9:E5)
Nov 10 21:28:50 nutmeg NetworkManager: <debug> [1194722930.085946] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1131_1001_noserial_if0_bluetooth_hci_bluetooth_hci').
Nov 10 21:29:52 nutmeg input[1072]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 10 21:29:52 nutmeg network[1153]: /org/bluez/network: org.bluez.network.Manager.ListConnections()
Nov 10 21:29:52 nutmeg audio[1073]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Nov 10 21:34:52 nutmeg hcid[1064]: remove_name_listener: no listener for :1.97
Nov 10 21:34:52 nutmeg NetworkManager: <debug> [1194723292.495715] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1131_1001_noserial_if0_bluetooth_hci_bluetooth_hci').
Nov 10 21:34:58 nutmeg NetworkManager: <debug> [1194723298.370723] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1131_1001_noserial_if0_bluetooth_hci_bluetooth_hci').
Nov 10 21:35:43 nutmeg NetworkManager: <debug> [1194723343.370215] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1131_1001_noserial_if0_bluetooth_hci_bluetooth_hci').
Nov 10 21:35:43 nutmeg NetworkManager: <debug> [1194723343.715815] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1131_1001_noserial_if0_bluetooth_hci_bluetooth_hci').
Nov 10 21:35:46 nutmeg NetworkManager: <debug> [1194723346.286279] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1131_1001_noserial_if0_bluetooth_hci_bluetooth_hci').
Nov 10 21:36:03 nutmeg NetworkManager: <debug> [1194723363.212749] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1131_1001_noserial_if0_bluetooth_hci_bluetooth_hci').
Nov 10 21:39:31 nutmeg NetworkManager: <debug> [1194723571.554913] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1131_1001_noserial_if0_bluetooth_hci_bluetooth_hci').
Nov 10 21:39:31 nutmeg hcid[1064]: remove_name_listener: no listener for :1.98
Nov 10 21:39:39 nutmeg NetworkManager: <debug> [1194723579.196238] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1131_1001_noserial_if0_bluetooth_hci_bluetooth_hci').


I presumed this meant that i had a problem with bluetooth and I wasted an hour looking for a solution, i discovered that the connection 'just works' - i.e. i can send/receive files in both directions with no problem.

So no bug after all, except that i can't browse the cellphone from my PC (not a life ruining loss but I like to have things working).

Ideas?

ps. otherwise 7.10 installed beautifully. well done to all involved.

---

