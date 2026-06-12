---
title: "Am I missing something (WPA2)"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Arla on 2009-08-18
Trying the live-cd of Kubuntu, figured since I quite liked digiKam that I may move to Kubuntu over Ubuntu. However, I can't for the life of me see a way to setup my wireless to connect to WPA2? I've opened the wireless options, but it only seems to have WEP, WPA-PSK and WPA-ESP?

Is this just a "definiciency" in Kubuntu? Ubuntu can connect just fine to my wireless network.

---

### Post by hanzomon4 on 2009-08-18
Yup... I have the same issue in Jaunty Knetworkmanager the option is there but it won't even try to connect to wpa-eap. wpa-psk works however

---

### Post by graaant on 2009-08-18
I'm running Kubuntu 9.10 - Knetwork manager still seems to hate WPA2.
What I've done is install nm-applet and set that for startup. Works perfectly and I prefer it over wicd (which also works well, however it doesn't seem to like reconnecting after sleep/suspend)

---

