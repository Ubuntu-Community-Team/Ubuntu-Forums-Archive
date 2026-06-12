---
title: "Networking problem after upgrade (7.10 &gt; 8.04)"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by leannonn on 2008-04-28
Hi,

I'm connecting to the net using a dial-up/satellite connection. The dial-up is an USB modem and I use `wvdial` to connect. It works OK and I get a new `ppp0` device when connected. My satellite card is configured and tuned on startup and I have a `dvb0_0` device for it. It also works fine.

In order to make them work together I am using `pptp` to create a VPN connection (e.g. `ppp5`) and then tweak the routing a bit. This did work on 7.10, but it's not working after the upgrade to 8.04 :( That is, the `pptp` itself returns no error (0) and the new routes are added fine - the same as it did on 7.10, but I can not even `ping` anything at all except the local addresses :(

What has changed? Does this have something to do with the new networking policies/authorizations?

Not sure which debug info I should post as I have no clue what this is about... :( Any ideas?


Take care,
Leannonn

---

### Post by leannonn on 2008-04-29
Hi,

Fixed the problem. I forgot to disable the packet filter, so this did the trick:

# echo "0" > /proc/sys/net/ipv4/conf/dvb0_0/rp_filter

And now the Heron truly takes flight for me :)


Take care,
Leannonn

---

