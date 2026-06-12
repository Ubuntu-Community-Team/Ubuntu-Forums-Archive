---
title: "Automatically Starting Firewire (IEEE-1394) Network On Boot?"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by wkulecz on 2012-01-04
I'm using Synergy over a 1394 (Firewire) private network.  Everything is fine, except I can't get the Firewire Ethernet to startup automatically.

None of the 10.04 network tools seem to do it.


After I login if I do:

```
sudo ifconfig eth3 192.168.0.1 netmask 255.255.255.0 up
```

Then everything is fine.

How do I get the 1394 network to come up automatically?

---

### Post by wkulecz on 2012-01-06
Bump.

No ideas?

Should I file a bug report on the network setup tools? or am I not using the "right" ones?

---

### Post by wkulecz on 2012-05-14
Bump, again I'm in the process of moving to 12.04 and would much appreciate a solution.

My 1394 network is 192.168.0.x my wired network is 192.168.1.x (behind a Linksys NAT router so I can run local servers not accessible from the internet at large for my development and testing.  There is also an unconnected second Ethernet port on the motherboard.

---

