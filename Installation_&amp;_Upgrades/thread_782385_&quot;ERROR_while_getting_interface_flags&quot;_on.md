---
title: "&quot;ERROR while getting interface flags&quot; on new install--Unstable Network"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by Polyglot on 2008-05-04
Greetings to all!

My experience with Ubuntu began with their very first release.  Currently, I have a server running 6.06 which I need to upgrade to solve just one issue--multipath_cache something or other that will enable internet load sharing across multiple interfaces when connected to more than one ISP.  

I tested 7.10, and found that it could handle the load sharing very well, but as this is a server application, I waited for the LTS edition to upgrade.  I chose to upgrade on fresh drives, with a new, clean install.  (Right glad am I that I did this, because I was able to go back to the old drives when it failed.)


The failure in 8.04 that I ran into had something to do with the LAN/WAN setup.  In the server I have one interface for LAN, and three for WAN, of which two are PPPoE accounts and one is a Static IP.  The internet connection would not last for more than a few minutes at best, before failing.

We simply could not establish the network.  Sometimes we would get through, but it was not stable.  The internet would last for perhaps 30 seconds or as much as two minutes, and then the connections would fail, and we could not even ping out.  At times, we could ping out from the server, but not from the LAN.  We seemed to have problems with both the connection itself, and with the DNS.  The DNS servers were properly listed in resolv.conf, but that appeared to make no difference.  After restarting the network, the dhcp, the firewall multiple times with the same results, we gave up and put the old SCSIs back in and re-established the network.  We're back to normal, but still no solution to the load balancing!

Doing a network restart would consistently yield messages like this:

ppp1: ERROR while getting interface flags: no such device

However, ifconfig would still show the device some of the time (this was not consistent), and sometimes ip route would display it as well.  In fact, sometimes, the error notwithstanding, it seemed we could get internet through it (I proved this by doing ifdown on the other internet routes first, and then pinging out), but this would be inconsistent and unstable.

I've searched in vain for anyone else with similar problems, which surprises me, because I afterward did a test install an a different machine with the same results.

Here's a few things I've tried:

--Reinstalling fresh without configuring the LAN, only the WAN
--Removing the /etc/udev/rules.d/70-persistent-net.rules file, then rebooting
--Trying such things as: modprobe -r e1000; modprobe e1000
--Searching online for help (got 3 hits in google, two in a foreign language for this search: linux pppoe "ERROR while getting interface flags" "70-persistent-net.rules")

Any ideas?

---

