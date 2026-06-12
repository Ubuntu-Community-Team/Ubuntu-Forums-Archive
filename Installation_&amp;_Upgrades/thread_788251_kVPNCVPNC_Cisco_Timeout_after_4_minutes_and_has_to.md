---
title: "kVPNC/VPNC Cisco Timeout after 4 minutes and has to be restarted."
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by rapidwiz on 2008-05-09
Hi,

I can't see to find any related topics which assist it resolving this issue.

I have just upgraded to 8.04 and have a timeout issues with KVPNC after approximately 4 minutes. I have played with all the settings and found some information that seems to reference to the NAT udp/tcp settings. 

I have also tried to run vpnc off the command, but seem to be unable to ping any networks in question.

My old server had KVPNC 0.8.5.1 had no issues with the timeout. KVPNC 0.9.0 seems to be issue and timesout. I have tried to install the older versions to no available. Any help would be appreciate, else I may have to downgrade :(

I also tried the vpnc --dpl-idle 0, but again a routing issue, possibly to do with NAT.

I have to uncheck "Use UDP (NAT-T)", else I cannot ping anything, unchecking this allows me to ping the network.

Any help would be appreciated.

Thanks

---

