---
title: "Belkin Wireless G appears as RaLink2500, Can't Connect"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by etali on 2009-10-04
========= EDITED - FINE WITH JAUNTY =======
Since I needed this box up and running, I decided to dig out my old Jaunty CD and installed that instead.  The wireless works great with Jaunty (even with the WEP turned back on :)

I'll keep checking the beta though - Karmic was running very well (and booting quickly!), just a shame about the wireless.
===========================================

Hi All

I've built a spare desktop using Ubuntu 9.10 beta.  It has a Belkin Wireless G PCI card in it.

According to lshw, the card is being recognised as a RaLink RT2500.

lshw says that it's using driver 8139too
driverversion=0.9.28

I've been following the troubleshooting guide, and this is what I've got so far... (Please forgive any typos, the wireless box has no other connection, so I'm typing the messages out on my netbook.  Oh for a floppy drive on this thing :) )

iwconfig says:

wlan0    IEEE 802.11bg  ESSID:"myrouters"
Mode: Managed  Frequency:2.442 Ghz  Access Point: Not-Associated
Tx-Power=20 dBm
Retry long limit:7  RTS thr:off  Fragment thr:oof
Power Management:on
Link Quality:0 Signal level:0  Noise level:0
Rx invalid nwid: 0 Rx invalid crypt: 0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

The device shows in the Devices - Network Tools dialog under wlan0, but there's no Wireless Connections in the Network Connections Gui.

If I try to add one, I get:
Error editing connection property %s / %s invalid %d
NMSettingWireless

I've tried restarting the wireless, and using dhconfig to request an ip address.  Neither works.

I originally had security (WEP - because there are a couple of old devices on the network that can't handle WPA) turned on, I've temporarily turned off security, that hasn't helped.


Other threads about the Belkin card have suggested ndiswrapper - should I download that and use it instead of the RaLink drivers? The troubleshooting guide implies that ndiswrapper is only for if Ubuntu doesn't recognize the card at all.  

There are some suggestions of other wireless managers.  Does anyone have a link to those so that I can download them on another PC? 

Any other suggestions would be much appreciated.

Thanks

---

### Post by etali on 2009-10-04
Just an update.  I took the box to bits to check the model number - the card is an F5D7000 V3000 - which apparently does use a RaLink chipset.  Therefore there's no need for ndiswrapper?

Any thoughts as to why the card is appearing in Network Tools, but won't let me add anything in Network Manager would be much appreciated.

---

### Post by TheMixtureMedia on 2009-10-06
I am having the same issue with Dlink

---

