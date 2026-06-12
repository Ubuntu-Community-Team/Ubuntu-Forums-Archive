---
title: "Asus Wireless Network 8.04 upgrade issue"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by bcummings on 2008-04-29
I am passing this along in the "for what it is worth" catagory.  

I have a home built computer with an Asus P5GD2 Deluxe motherboard.  The motherboard came with an onboard WiFi-g wireless LAN adapter.  I first installed Ubuntu 7.10 on the computer and struggled to get the wireless LAN adapter to work.  However, after a little research, I installed "ndiswrapper", then downloaded and installed the Windows XP driver. Viola! After a few minutes farting around.....I was wireless again.  

Upon installing the upgrade from 7.10 to 8.04, my wireless connection, busted.  I was extrememly bummed, but I persisted.  What I found was that this.  While using 7.10 the configuration for the wireless adapter had to be set to manual.  I then had to manually configure the wireless adapter to work.  If I checked the box next to enable roaming mode the wirless adapter would not work.  After the upgrade, it is the complete opposite.  I enabled roaming mode and whamo!  I'm wireless again.

I don't know why...seems odd that the setting would change, but for those of you struggling with wireless, I hope this might be of some use.  ndis wrapper was the original saviour for me and has performed flawlessly with the ASUS provided driver.  fiddeling with the settings fixed the issue the second time around. 

Thank you to the Ubuntu developers for a superior product.

---

### Post by patrickes on 2009-05-19
I have this same motherboard, and after installing ubuntu I enabled the onboard wifi, but I can't see any wireless networks.
I only see a wired connection option.
What do I need to do?

Thanks!!

---

