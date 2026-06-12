---
title: "ubuntu 10.04 live USB (and cd) ok - after install KO!!"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by lever63 on 2010-09-17
Hi to all,
I'm using ubuntu on a desktop computer in dual boot; i'm not an expert but ubuntu is easy enough to me. In the past, I've tried many times to install ununtu on my laptop, but I've always had problems with wifi connection; recently I've tried ununtu 10.04; network manager asked me ssid (is hidden), autentication (WEP), the key and,  what a surprise!, wifi works!!! 
Of course I decide to install
after installation, network manager doesn't recognize network card, and there is no way to use it; I've installed WICD and now network card works ("sudo iwlist scan" respond correctly), I can see my wireless network, but I can't connect becouse it respond "password incorrect"; of course I registered the right key.

some information 

the laptop is an acer 5715z
processor is intel pentium dual cpu T2330 1,6GHz
i think it is  64 bit ([http://ark.intel.com/Product.aspx?id=32432](http://ark.intel.com/Product.aspx?id=32432))
memori:  2 GB
wifi card is atheros AR5007EG

I've installed ubuntu 10.04 32 bit

I can't understand why the live version works and when I install it doesn't work!

I've tried 10.10 beta with the same results.

could someone help me?

I've resolved.

the difference between live and installed was in "pppoeconf"; in live mode network works slowly, and in another forum someone suggests to use "pppoeconf" and it works, networks run as fast as allowed by my connection, but this command "destroy" something in wlan configuration, so at first rebooot wlan was unusable; 
I've installed  without run "pppoeocnf" and wlan works, slowly but works; then I solved speed problem with a workaround found in the forum.

---

### Post by mörgæs on 2010-09-18
Here is something to begin with:
[http://madwifi-project.org/wiki/Compatibility/Atheros#AtherosAR5007EG](http://madwifi-project.org/wiki/Compatibility/Atheros#AtherosAR5007EG)

It seems like installing 9.10 or trying ndiswrapper in 10.04 are the best options.

---

