---
title: "Very slow boot with 15.04"
date: 2015-05-02
forum: Installation &amp; Upgrades
---

### Post by howard-gilbrt on 2015-05-02
Here is the part of dmesg that seems to identify the an 80 second time gap  but I don't know what it means or how to solve.  Please help if you can.
================================
[   20.029532] audit: type=1400 audit(1430583089.274:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=533 comm="apparmor_parser"
[   20.029540] audit: type=1400 audit(1430583089.274:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=533 comm="apparmor_parser"
[   20.110982] audit: type=1400 audit(1430583089.358:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=533 comm="apparmor_parser"
[   20.110991] audit: type=1400 audit(1430583089.358:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=533 comm="apparmor_parser"
[   20.110995] audit: type=1400 audit(1430583089.358:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=533 comm="apparmor_parser"
[   20.111000] audit: type=1400 audit(1430583089.358:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=533 comm="apparmor_parser"
[   20.245007] audit: type=1400 audit(1430583089.490:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=533 comm="apparmor_parser"
[   20.245016] audit: type=1400 audit(1430583089.490:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=533 comm="apparmor_parser"
[   20.245021] audit: type=1400 audit(1430583089.490:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=533 comm="apparmor_parser"
[   20.245025] audit: type=1400 audit(1430583089.490:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=533 comm="apparmor_parser"
[  101.828267] cfg80211: Calling CRDA to update world regulatory domain
[  101.873286] cfg80211: World regulatory domain updated:
[  101.873291] cfg80211:  DFS Master region: unset
[  101.873293] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  101.873295] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  101.873297] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  101.873298] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[  101.873299] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  101.873301] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  102.196203] r8169 0000:01:00.0 eth0: link down
[  102.196221] r8169 0000:01:00.0 eth0: link down
[  103.867220] r8169 0000:01:00.0 eth0: link up
=========================================
Thanks

---

### Post by howard-gilbrt on 2015-05-03
Found the problem.  the uuid for swap was wrong in fstab,  

thanks to askubuntu.com/questions/612600/15-04-very-slow-boot.

---

