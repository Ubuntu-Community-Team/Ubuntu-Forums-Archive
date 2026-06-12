---
title: "Backgrounding ifup commands if not dhcp response received"
date: 2005-08-16
forum: Installation &amp; Upgrades
---

### Post by haldrik on 2005-08-16
Hi!
I have a little annoyance that I'd like to resolve. Basically, I use both ethernet and wireless g to connect to networks, as I move my little laptop around quite a bit. The problem I have is that if I'm using wireless today, and have wlan0 setup as the principle network adapter, I have a very long pause when booting if I happen to be away from my wireless network and use ethernet instead. If I have ethernet setup as the primary network device, then there's a long pause once I move back to wireless (after booting, I would just change my networking prefs back to wireless, but there's always that one long pause after a switch of locations.

Now I know I can just set it up to not try to log on to any networking (then of course there's a long pause when Ubuntu tries to sync the clock with some networked time service), but then I have to manually turn on whichever network device I need at that particular boot time.

Suse linux (which I used before) would simply background (but not give up) trying to get an IP address from a DHCP server if it took more than say 2 seconds to get an answer, so that the rest of the boot process could carry on while the DHCP server takes its time. 

So is there a way at boot time to tell Ubuntu to first try getting an IP address from eth0, if it doesn't get one in 3 seconds to then use wlan0 instead and to background the whole process so the rest of the boot doesn't have to wait on these functions?

Thanks for any hints...

---

