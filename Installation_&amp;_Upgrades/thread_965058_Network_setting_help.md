---
title: "Network setting help"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by trumpcouptimmy on 2008-10-31
1) I upgraded from hardy using update-manager -d.
2) On both wired and wireless, it appears that we can't get an ip address. Hardware is fine because I'm using it now running the Intrepid live cd.
3) The same thing happens on a different user so it isn't user dependent
4) On hardy I was running the network manager 0.7 with no problems except that it wouldn't remember the network key and it never asked about the keyring. I had to manually enter it when it asked for it.
5) After the upgrade, I can get telnet to connect after using

iwconfig wlan0 essid sample
iwconfig wlan0 key key
dhclient wlan0

telnet works but firefox doesn't for some reason. I tried other browswers and they didn't connect either. It must be some little setting somewhere but I don't know which one and where. Someone probably has a bright idea!

---

