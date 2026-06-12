---
title: "Edgy getting ip, but doing nothing else"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by Mikey7047 on 2006-12-21
Let me first preface this that before this I considered myself pretty good at networking.  I've tried two different setups, and can't get my edgy box to do anything other than get an IP.

The first setup I tried was using Windows XP ICS, and connecting to the Ubuntu box using a crossover.  I used DHCP for the settings at first, it got an IP (192.168.0.2 or something), but I cannot ping the XP computer (gateway) or any other computers on the network.

The second setup was using a wireless gaming adapter to connect the Ubuntu box "directly" to the router.  This resulted in the same problem it got assigned the 192.168.1.108 IP from the router, and I could see it as connected (with no computer name or description) in the router status page.

I can't figure out the problem, I know it's not cabling, etc.  because my Xbox can connect fine using Windows ICS and I tested it with my laptop also, and both worked fine.

---

### Post by PilotJLR on 2006-12-21
Could you pls post the output of:
```

route
ifconfig

```

And also verify the LAN ip address of the nat router...

---

