---
title: "Need help whit kismet.conf"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by le3000gt on 2008-10-19
this is what I get
le3000gt@le3000gt-laptop:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
Done.

 what I did to kismet.conf and what there now 
source=type,interface,ath0

source=ipw3945,ath0,Wireless Card
then I save it and closed it 
  
this is my iwconfig
ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:10:21:F8
          Bit Rate:36 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=14/70  Signal level=-80 dBm  Noise level=-94 dBm
          Rx invalid nwid:61121  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
i

---

