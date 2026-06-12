---
title: "PPPoE and my username"
date: 2005-04-05
forum: Installation &amp; Upgrades
---

### Post by zeu on 2005-04-05
When I installed ubuntu it failed to establish dhcp over ethernet, so I input some dns information manually.

However the problem is I have a dynamic IP and I have to log in to my isp with a username and password.

I went all over networking setup to find any kind of place to insert my username but to no avail.
Could someone just explain to me how to do this?

Thanks in advance.

---

### Post by stepper on 2005-04-05
i think $ sudo pppoeconf

---

### Post by zeu on 2005-04-05
[QUOTE=stepper]i think $ sudo pppoeconf[/QUOTE]
 now i have another problem.

i did pppoeconf, it scanned the eth0 for some interface thing, found it, asked me for my username and password and some other stuff, i hit ok, it said do you want to start the connection now? i said yes, gave it a few moments.

then i did ifconfig ppp0 like it said, it showed just like ifconfig did, my ip address and it had received packets.
it even added a second dns server in my eth0 network config.

but guess what?
i can't access anything online.
it's stuck at "resolving.." i tried a bunch of apps but nothing worked.

---

