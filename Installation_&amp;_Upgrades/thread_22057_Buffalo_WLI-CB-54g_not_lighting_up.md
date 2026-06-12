---
title: "Buffalo WLI-CB-54g not lighting up"
date: 2005-03-25
forum: Installation &amp; Upgrades
---

### Post by fallscrape on 2005-03-25
[sorry, moved this to the hardware thread]

OK - I'm new to linux - I've only been using it in drips and drabs over the last 5 or so years ('s a scary thought).

I've managed to install ndiswrapper and have found a site that showed me step by step to install my card using ndiswrapper.  It has sucessfully installed and shows up under the System>Administration>Networking

When I run ndiswrapper -l it says:  netcbg54 Driver present, hardware present

The drivers came off the installation disk.  When I modprobe ndiswrapper, I have no problems reported.

Even so, the lights refuse to come onto the card & altough it is listed as 'active' I don't believe it is.  My intel 2100B has no issues whatsoever and lists the two APs.

I've never installed a PCMCIA/CB card under linux, so I've probably missed something obvious.  It was in the PCMCIA when I install ubuntu for the first time over an hour ago  :D 

Any ideas?

---

### Post by fallscrape on 2005-03-25
Also, the AP I want to connect it to is running WPA PSK AES.  The mac filtering is setup already, however it'd be nice if anyone could tell me how I'm supposed to set this up as I can only see options in the GUI for WEP.

---

### Post by toyfactory on 2005-04-23
Same problem here.

ndiswrapper -l reports:

bcmwl5a driver present, hardware present

iwconfig reports:

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist wlan0 scan reports:

wlan0     No scan results

My AP is configured to broadcast SSID so the fact that scan doesn't pick anything up suggests the adaptor isn't working.  The fact that the power light isn't on probably also suggests the adaptor isn't working...

Currently I have to modprobe -i ndiswrapper manually, later I ought to find how to get it all working automatically.  Incidentally, it works in Windows without a hitch.

Any ideas?

Nick

---

### Post by ElvisThePelvis on 2005-04-23
The ndiswrapper debian package incorrectly sets the RadioState to 1 when 0 actually means enable. I think the ndiswrapper config files is 14E3:4320.conf for that card. To be safe, look in /etc/ndiswrapper/*.conf and change RadioState =0 for all of the conf files. I am going from memory here so you may have to dig around a bit to get it working.

Good luck.

---

### Post by toyfactory on 2005-04-24
Cheers Elvis!  That seemed to be the problem.  I've almost got it working...

Thread continues over here:

[http://www.ubuntuforums.org/showthread.php?t=29160](http://www.ubuntuforums.org/showthread.php?t=29160)

---

