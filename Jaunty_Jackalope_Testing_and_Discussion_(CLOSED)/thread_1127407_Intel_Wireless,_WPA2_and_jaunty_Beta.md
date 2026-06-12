---
title: "Intel Wireless, WPA2 and jaunty Beta"
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dazedandconfused on 2009-04-16
Hi All,

I've hit a brick wall with Jaunty Beta and my Intel wifi. I've stumbled across various people with the same problem on various Ubuntu releases in the past and have tried running it via the interfaces file instead of Network Manager, installing the open source Intel firmware etc., but still have had no joy (12 hours of trying). WEP works fine but WPA generates the following in dmesg:

 [  244.541545] wlan0: direct probe to AP f62c96b8 try 1
[  244.543367] wlan0 direct probe responded
[  244.543375] wlan0: authenticate with AP f62c96b8
[  244.544964] wlan0: authenticated
[  244.544972] wlan0: associate with AP f62c96b8
[  244.547789] wlan0: RX ReassocResp from eacfa026 (capab=0x471 status=0 aid=3)
[  244.547796] wlan0: associated
[  248.548142] wlan0: beacon loss from AP f62c96b8 - sending probe request
[  248.552643] wlan0: deauthenticated (Reason: 1)
[  249.555377] wlan0: direct probe to AP f62c96b8 try 1
[  249.557178] wlan0 direct probe responded
[  249.557183] wlan0: authenticate with AP f62c96b8
[  249.558629] wlan0: authenticated
[  249.558636] wlan0: associate with AP f62c96b8
[  249.561459] wlan0: RX ReassocResp from f35e1026 (capab=0x471 status=0 aid=3)
[  249.561466] wlan0: associated
[  253.563015] wlan0: deauthenticated (Reason: 1)
[  254.561099] wlan0: direct probe to AP f62c96b8 try 1
[  254.562901] wlan0 direct probe responded
[  254.562907] wlan0: authenticate with AP f62c96b8
[  254.564672] wlan0: authenticated
[  254.564680] wlan0: associate with AP f62c96b8
[  254.567521] wlan0: RX ReassocResp from eadca026 (capab=0x471 status=0 aid=3)
[  254.567529] wlan0: associated
[  258.572068] wlan0: beacon loss from AP f62c96b8 - sending probe request
[  264.496049] wlan0: deauthenticated (Reason: 7)


while network manager shows packets being sent but not received.

The router is a Belkin wireless G, lspci gives me this info about the wifi card:

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1011
	Flags: bus master, fast devsel, latency 0, IRQ 2298
	Memory at f8000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

and upon initial loading I get this from dmesg:

[   20.063701] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.065945] iwl3945 0000:04:00.0: firmware: requesting lbm-iwlwifi-3945-2.ucode
[   20.134571] iwl3945 0000:04:00.0: loaded firmware version 15.28.2.8
[   20.179157] Registered led device: iwl-phy0::radio
[   20.179180] Registered led device: iwl-phy0::assoc
[   20.179238] Registered led device: iwl-phy0::RX
[   20.179257] Registered led device: iwl-phy0::TX
[   20.183178] ADDRCONF(NETDEV_UP): wlan0: link is not ready


BTW, laptop is a Lenovo n200 3000, core2 duo.


Interesting thing as well is that when I upgraded from 8.10 to 9.04, I could run the wireless in my account, but if I added a user and tried to set it up in theirs, they'd get the same problem as above so whatever were hanging around on my login still worked. A clean install however, has killed all wireless.
 
Any ideas gratefully received.

Cheers,

jools

---

### Post by Taiebot65 on 2009-04-16
delete your autonetwork
Try to manually add your network.

enter your SSID address and your password

check on your router do not have a button to activate

---

### Post by paradigm2 on 2009-04-16
wpa2-personal or wpa2 enterprise?

I have read that enterprise is NOT working at all.  However personal works perfectly for me.

```

248.548142] wlan0: beacon loss from AP f62c96b8 - sending probe request

```

^ This is suspicious.  It is acting as if has a very shaky signal.  Does getting closer to the router make a difference?  When you connect using WEP, what signal strength do you get as measured by the connection manager icon (in the upper right hand corner).

Does wpa2 work okay on another computer using the same router (in order to isolate the problem to being your computer, nto the router's settings)?

---

