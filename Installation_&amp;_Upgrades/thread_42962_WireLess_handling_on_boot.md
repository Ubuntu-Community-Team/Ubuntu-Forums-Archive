---
title: "WireLess handling on boot"
date: 2005-06-20
forum: Installation &amp; Upgrades
---

### Post by biscuit on 2005-06-20
I managed to install ndiswrapper and got my wireless working, but on subsequent boots although the wireless connection is active it is set to essid="WLAN" which is not ssid in question.
Using the network manager menu option I can simply disable and re-enable wlan0 and everything is fine.

However if I boot and log on as root the wireless is configured correctly without any extra work. Naturally I dont want to log on as root all the time therefore is there any way I can get the wireless to come up correctly when non-root and without further manual intervention?

---

### Post by biscuit on 2005-06-29
Well I guess its totally random. Sometimes it boots up configured correctly and some times it doesnt, as root or not. So I guess the culprit is ndiswrapper, but then why does it always connect 100% of the time when manually done thru that Network Manager?

BTW is it because my question is too darn stupid or too darn hard that I got no replies?

Are these forums just masquerading as some help or is it the blind leading the blind?

Why do I bother with ubuntu?

Why should you?

---

