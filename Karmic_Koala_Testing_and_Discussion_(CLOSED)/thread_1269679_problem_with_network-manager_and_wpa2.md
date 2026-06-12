---
title: "problem with network-manager and wpa2"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gertpozzo on 2009-09-18
Hi all.
I've already posted a bug report on launchpad about this.

The problem is that I can't connect to the WPA2 network of my university using network-manager. If I set all the parameters and click "Connect" nothing happen. The daemon.log file says: 
```

Sep 18 17:34:47 homer wpa_supplicant[1796]: CTRL-EVENT-SCAN-RESULTS 
Sep 18 17:35:47 homer wpa_supplicant[1796]: CTRL-EVENT-SCAN-RESULTS 
Sep 18 17:36:17 homer NetworkManager: user_connection_updated_cb: assertion `old_connection != NULL' failed
Sep 18 17:36:17 homer NetworkManager: <WARN>  user_connection_get_settings_cb(): Couldn't retrieve connection settings: Method "GetSettings" with signature "" on interface "org.freedesktop.NetworkManagerSettings.Connection" doesn't exist#012.
Sep 18 17:36:18 homer NetworkManager: <WARN>  user_connection_get_settings_cb(): user_connection_get_settings_cb: Invalid connection: 'NMSetting8021x' / 'client-cert' invalid: 2
Sep 18 17:36:23 homer NetworkManager: <WARN>  wait_for_connection_expired(): Connection (2) /org/freedesktop/NetworkManagerSettings/0 failed to activate (timeout): (0) Connection was not provided by any settings service
Sep 18 17:36:47 homer wpa_supplicant[1796]: CTRL-EVENT-SCAN-RESULTS 

```However I can connect manually without any problem using wpa_supplicant with the following wpa_supplicant.conf:

```

ctrl_interface=/var/run/wpa_supplicant
network={
      ssid="unimib"
      scan_ssid=1
      key_mgmt=WPA-EAP
      pairwise=CCMP TKIP
      group=CCMP TKIP
      eap=TLS
      identity="xxxxxxx"
      ca_cert="xxxxxxxx"
      client_cert="xxxxxxx"
      private_key="xxxxxxxxx"
      private_key_passwd="xxxxxxxxxx"
}

```I can also use network-manager without any problem to connect to my home wep network.

With a clean installation of alpha 5 all works well. The problem started after an update in-between alpha 5 and alpha 6.

Any clues?

---

### Post by Vanishing on 2009-09-18
eh...im using wpa2 and have no problem...
i guess its your config?

---

### Post by gertpozzo on 2009-09-18
It can't be my config, becouse the alpha 5 with exactly the same config works well.

---

### Post by Vanishing on 2009-09-18
> **gertpozzo said:**
> It can't be my config, becouse the alpha 5 with exactly the same config works well.

ugh...o.o
so recent network-manager updates broke on your machine?
Then try wicd in the mean time while waiting for the bug to be solved.

---

### Post by gertpozzo on 2009-09-18
Yes. I'm already using Wicd. It works well, but I prefer network-manager.
I'll wait for an answer to my bug report on launchpad...

Thanks

---

