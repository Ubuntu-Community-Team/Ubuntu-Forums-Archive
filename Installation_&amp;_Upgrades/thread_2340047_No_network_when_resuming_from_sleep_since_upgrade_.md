---
title: "No network when resuming from sleep since upgrade to 16.10"
date: 2016-10-15
forum: Installation &amp; Upgrades
---

### Post by castor_fou on 2016-10-15
Hello

When returning from sleep, everything works except for network.

Here is what I see in /var/log/syslog :

```
Oct 15 12:40:16 XPS systemd[1]: Starting Network Manager Script Dispatcher Service...
Oct 15 12:40:16 XPS dbus[946]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 15 12:40:16 XPS systemd[1]: Started Network Manager Script Dispatcher Service.
Oct 15 12:40:16 XPS nm-dispatcher: req:1 'down' [wlan0]: new request (2 scripts)
Oct 15 12:40:16 XPS nm-dispatcher: req:1 'down' [wlan0]: start running ordered scripts...
Oct 15 12:40:16 XPS nm-dispatcher[5639]: /etc/network/if-post-down.d/ubuntu-fan: 29: /etc/network/if-post-down.d/ubuntu-fan: /usr/sbin/fanctl: not found
Oct 15 12:40:16 XPS nm-dispatcher[5639]: run-parts: /etc/network/if-post-down.d/ubuntu-fan exited with return code 127
Oct 15 12:40:16 XPS nm-dispatcher: req:1 'down' [wlan0], "/etc/NetworkManager/dispatcher.d/01ifupdown": complete: failed with Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Oct 15 12:40:16 XPS NetworkManager[954]: <info>  [1476528016.5196] device (wlan0): state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Oct 15 12:40:16 XPS wpa_supplicant[1147]: nl80211: deinit ifname=wlan0 disabled_11b_rates=0
Oct 15 12:40:16 XPS NetworkManager[954]: <warn>  [1476528016.6003] dispatcher: (5) 01ifupdown failed (failed): Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
```

Perhaps this error :  /usr/sbin/fanctl: not found is fatal to resume network ?

Have you experienced the same ?

Only solution for the moment is to reboot.

Guillaume

---

