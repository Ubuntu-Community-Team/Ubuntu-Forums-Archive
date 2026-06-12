---
title: "How do I set up Network Throttling in Ubuntu?"
date: 2005-07-16
forum: Installation &amp; Upgrades
---

### Post by limbus on 2005-07-16
Hello all,
Is there an easy way (I mean, using the GUI utilities) to throttle the maximum network i/o  throughput in a specific interface, like eth0? I would like to limit the bandwidth that my notebook is consuming in my home ADSL network, for instance, to a maximum of 128kbps.

Thanks for any advice.

---

### Post by smoon on 2005-07-16
[QUOTE=limbus]Hello all,
Is there an easy way (I mean, using the GUI utilities) to throttle the maximum network i/o  throughput in a specific interface, like eth0? I would like to limit the bandwidth that my notebook is consuming in my home ADSL network, for instance, to a maximum of 128kbps.

Thanks for any advice.[/QUOTE]

As far as I know there are no GUI utils to configure traffic shaping. If you really want to do it read the [Linux Advanced Routing & Traffic Control HOWTO](http://lartc.org/howto/) and use their so called [Wonder Shaper](http://lartc.org/wondershaper/).

I tried it several times on my selfmade Woody router and had nothing but trouble with it. Two or so month ago I found [m0n0wall](http://www.m0n0.ch/wall/), which "is based on a bare-bones version of FreeBSD, along with a web server, PHP and a few other utilities". I gave it a try and found out that it includes a traffic shaper which is configurable through m0n0wall's great webinterface. It was very easy to set the traffic shaping up since it has a setup wizard for setting this up as well. Finally: It works really great (both m0n0wall as a whole and its traffic shaper) and I never had any problems with that again.

So, maybe, this is an option for you as well? (It has wlan support as well)

---

