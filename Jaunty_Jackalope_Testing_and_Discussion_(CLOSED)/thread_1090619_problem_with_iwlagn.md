---
title: "problem with iwlagn"
date: 2009-03-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by biasquez on 2009-03-08
frequently, my pc has broken internet connection (that freeze my pc sometimes) , iwlagn is the problem:

Mar  8 19:36:34 omg kernel: [ 2973.172827] iwlagn: Microcode SW error detected.  Restarting 0x2000000.
Mar  8 19:36:34 omg kernel: [ 2973.200836] iwlagn: Can't stop Rx DMA.
Mar  8 19:36:35 omg kernel: [ 2974.798631] Registered led device: iwl-phy0:radio
Mar  8 19:36:35 omg kernel: [ 2974.798645] Registered led device: iwl-phy0:assoc
Mar  8 19:36:35 omg kernel: [ 2974.798655] Registered led device: iwl-phy0:RX
Mar  8 19:36:35 omg kernel: [ 2974.798666] Registered led device: iwl-phy0:TX
Mar  8 19:36:36 omg kernel: [ 2974.982434] CE: hpet increasing min_delta_ns to 22500 nsec
Mar  8 19:37:02 omg kernel: [ 3000.940051] CE: hpet increasing min_delta_ns to 33750 nsec
Mar  8 19:38:11 omg kernel: [ 3070.193215] CE: hpet increasing min_delta_ns to 50624 nsec
Mar  8 19:38:39 omg kernel: [ 3098.897695] CE: hpet increasing min_delta_ns to 75936 nsec
Mar  8 19:39:59 omg kernel: [ 3178.013048] mac80211-phy0: failed to remove key (0, 00:11:50:0d:78:83) from hardware (-22)
Mar  8 19:39:59 omg kernel: [ 3178.014179] wlan0: direct probe to AP 00:11:50:0d:78:83 try 1
Mar  8 19:39:59 omg kernel: [ 3178.105941] wlan0: disassociating by local choice (reason=3)
Mar  8 19:40:00 omg kernel: [ 3179.629288] Registered led device: iwl-phy0:radio
Mar  8 19:40:00 omg kernel: [ 3179.629343] Registered led device: iwl-phy0:assoc
Mar  8 19:40:00 omg kernel: [ 3179.629382] Registered led device: iwl-phy0:RX
Mar  8 19:40:00 omg kernel: [ 3179.629419] Registered led device: iwl-phy0:TX
Mar  8 19:40:00 omg kernel: [ 3179.645177] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

