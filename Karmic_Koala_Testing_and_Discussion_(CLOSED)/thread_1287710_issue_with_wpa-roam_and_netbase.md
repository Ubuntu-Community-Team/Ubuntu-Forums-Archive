---
title: "issue with wpa-roam and netbase"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tekknokrat on 2009-10-10
Hi I am using the karmic-beta and have issue with netbase using the wpa-roam facility.

The network is not started on bootup but is working when started manually by invoking networking.

My interface file looks like this:

```

auto lo
iface lo inet loopback

auto wlan0

iface wlan0 inet manual
#  wireless-power off
  wpa-driver wext
  wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf

iface zuhause inet dhcp
iface sis inet dhcp

```

wpa_supplicant.conf:

```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1

# reading passphrase from stdin
network={
	id_str="zuhause"
	ssid = ******
	#psk = *****
	psk = *****
}
network={
        id_str="sis"
	ssid = ******
	#psk = *****
	psk = *****
}
```

Card is BCM4312 using wl driver. Some changes I missed during upgrade from jaunty?

---

