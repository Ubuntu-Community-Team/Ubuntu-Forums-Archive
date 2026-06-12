---
title: "NTP Fails"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by Pig Monkey on 2005-10-15
I just did a clean install of 5.10. Now, when I boot up, it says it attempts to sync with ntp.ubuntulinux.org but "Fails".
Any ideas why?

The network interface is working fine, so it has internet access. Before I formatted I was running 5.04, which synced without any error on boot, so the network isn't blocking the packets.

---

### Post by Rxke on 2005-10-15
did it fail immediately? An immediate 'fail' is probably because your hardware network i/f might be working fine, but there might be an issue with actually getting connected to the outside world. Can you get webpages, updates etc? If not, you might have to reconfigure your network settings. (DHCP accescodes etc...)


Otherwise, when it fails after a significant delay, it's maybe just a case of timeout...

---

