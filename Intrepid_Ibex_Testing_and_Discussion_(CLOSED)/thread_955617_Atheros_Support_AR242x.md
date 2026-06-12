---
title: "Atheros Support AR242x"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by 000dom000 on 2008-10-22
Hi, I currently have today's build of Intrepid installed. When I installed, atheros HAL drivers were enabled in restricted drivers. I disabled these when they didn't work as before because Ubuntu apparently misidentifies my card. I heard also that the ath9k drivers would be in Intrepid. There is evidence of these drivers, for example, wlan0 is listed as an interface, but I am unable to scan with nm-applet or wifi-radar.

lspci gives me 

```
Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

iwlist scan gives me
```
wlan0 No scan results
```

sudo iwlist scan gives me
```
wlan0     Interface doesn't support scanning : Network is down
```

Anyone got any ideas what might be going on? From experience, atheros drivers usually meant you had an ath0 device but that is not shown on iwconfig.

Thanks for any help!

---

### Post by 000dom000 on 2008-10-22
Bump. I noticed this thread [http://ubuntuforums.org/showthread.php?t=938385&highlight=atheros+242x+intrepid](http://ubuntuforums.org/showthread.php?t=938385&highlight=atheros+242x+intrepid) which suggests that everything is working fine. Is there anything I might be missing?

---

### Post by Teamgeist on 2008-10-22
Is the package ```
linux-firmware
``` installed on your system? If not, install it and resart.

---

### Post by Thricemin on 2008-10-22
I have the same atheros hardware ar242x.

Download ndiswrapper and here is the ar242x driver

---

### Post by 000dom000 on 2008-10-22
> **Teamgeist said:**
> Is the package ```
linux-firmware
``` installed on your system? If not, install it and resart.

It already is, thanks anyway.

As for ndiswrapper, I will use it as a last resort but I like to have native drivers. Looks more likely though.

---

### Post by teddks on 2008-10-22
This card isn't working with ath5k yet, at least the AR242x I have, with this response from lspci -n:
```
03:00.0 0200: 168c:001c (rev 01)
```

There have seen some reports of it working under ath5k, but with very limited speed. This branch of the madwifi HAL works with it: [http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6](http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6)

---

