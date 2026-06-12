---
title: "Prism54 problems"
date: 2005-09-21
forum: Installation &amp; Upgrades
---

### Post by zAo on 2005-09-21
Hello all,

I bought a prism54 card last week, but didn't get it to work. I bought this 3Com card:
```
Network controller: 3Com Corporation 3com 3CRWE154G72 [Office Connect Wireless LAN Adapter] (rev 01)
``` 

When I boot, I get this from iwconfig:
```
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      NOT READY!  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
``` 

dmesg tells me the module is loaded:
```
[4294706.934000] Loaded prism54 driver, version 1.2
``` 

I switched my accespoint to an open network: no WEP, no WPA, no pass and DHCP. Sudo dhclient eth1 gives me:
```
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
SIOCSIFFLAGS: Timer expired
SIOCSIFFLAGS: Timer expired
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:30:b4:00:00:00
Sending on   LPF/eth1/00:30:b4:00:00:00
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
send_packet: Network is down
```

I followed this tutorial for Debian and tried both the latest and v 1.0.3.0 firmware from prism54:
[http://prism54.org/phpwiki?pagename=Prism54%20Debian%20HowTo](http://prism54.org/phpwiki?pagename=Prism54%20Debian%20HowTo)

Who can help me on this?

Thanks,

zAo

---

### Post by zAo on 2005-09-21
Just discovered this:
```
[4295698.349000] eth1: resetting device...
[4295698.349000] eth1: uploading firmware...
[4295698.638000] eth1: firmware version: 1.0.4.3
[4295698.638000] eth1: firmware upload complete
[4295699.638000] eth1: no 'reset complete' IRQ seen - retrying
[4295700.638000] eth1: no 'reset complete' IRQ seen - retrying
[4295700.638000] eth1: interface reset failure
```

---

### Post by mlomker on 2005-09-21
> Who can help me on this?


Not sure that I have a solution for you, but what is the output of **iwconfig** after you set the access point?  It certainly doesn't look normal beforehand.

---

### Post by mlomker on 2005-09-21
> [4295699.638000] eth1: no 'reset complete' IRQ seen - retrying


I found [another thread](http://ubuntuforums.org/archive/index.php/t-11273.html) with the same card and error.  The poster had to use ndiswrapper with the card.

---

### Post by zAo on 2005-09-21
[QUOTE=mlomker]I found [another thread](http://ubuntuforums.org/archive/index.php/t-11273.html) with the same card and error.  The poster had to use ndiswrapper with the card.[/QUOTE]
First of all: thank you for the reply. I bought this card for its prism54-chipset :) I used ndiswrapper on my old card.
After I set up the accesspoint, iwconfig shows me:
```
zao@zao:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      NOT READY!  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``` 

In the threat it says that this card works out-of-the-box on Ubuntu ([http://ubuntuforums.org/showpost.php?p=50961&postcount=11](http://ubuntuforums.org/showpost.php?p=50961&postcount=11))

Any other suggestions?

---

### Post by Zotova on 2005-09-21
Sorry to break it to you but it isn't the standard prism54 chipset. In the latest version 3com used a macless version of the chipset - I don't know the full details behind it but if you google it you will find the latest version of the card (version 2) will not work with the prism54 driver. The only way is ndiswrapper - which I was using myself but found very unreliable. With ndiswrapper it would work for about a week then just give up.

If you can I highly suggest taking the card back and buying a belkin one (or another card which is based on the rt2500 chipset - my new card is working perfectly on the linux driver.

---

