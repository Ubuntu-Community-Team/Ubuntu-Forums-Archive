---
title: "frostwire has detected a router firewall"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by Franscisco on 2007-04-14
Does any know what I can do, so Frostwire can connect to the network?
there is a firewall blocking Frostwire, so I want to know if there is a way to let Frostwire connect to the network.

---

### Post by mhansen on 2007-04-14
Well, I'm not familiar with Frostwire or what port(s) is uses, but it sound like you just have to configure your router firewall to allow that traffic.  I know my router, by default, blocked darn near EVERYTHING.

I have a 2wire router, for example, and I use my browser to connect to [https://192.168.1.254](https://192.168.1.254) to make any changes.  That IP will vary depending on your make/model/ISP.  You can call your ISP for the info, or look thru any of several config or log files that will give you that info.  For instance, I connect using dhcp, and in /var/lib/dhcp3 I find a file called dhclient.eth0.leases which contains my router info as such: option routers 192.168.1.254.  Running sudo arp -a usually also works....there are a bunch of ways to get it...

Best bet is to probably call your ISP, because it's probably passworded anyway, and if you didn't set it, I'm guessing you don't know it.



Regards,
Mike

---

