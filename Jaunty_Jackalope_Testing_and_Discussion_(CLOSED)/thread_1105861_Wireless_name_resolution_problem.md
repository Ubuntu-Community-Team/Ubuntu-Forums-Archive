---
title: "Wireless name resolution problem"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nickmcg on 2009-03-25
I'm using a ralink rt2870 wireless network adapter, and I can no longer resolve names for the internet.

If I boot with the Jaunty alpha6 CD everything works ok, but when I boot normally, nslookup works & correctly gives the ip address. I can ping the ip address, but if I attempt to ping the name, I get 'unknown host'.

Computer names on the LAN resolve correctly.

Is this a Jaunty problem?

Is this a wetware problem (have I fouled things up)?

Should I post this in the network section?

Any help greatly appreciated.

Nick

---

### Post by hugmenot on 2009-03-25
```
cat /etc/resolv.conf
```

That is: who is serving you domain names? Are your DNS/domain  properly configured?

---

### Post by nickmcg on 2009-03-25
resolv.conf correctly reports the name servers from the router - and nslookup works too.

---

### Post by nickmcg on 2009-03-25
I have removed the wins entry from the hosts line in /etc/nsswitch.conf
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
was 
```
hosts:          files mdns4_minimal wins [NOTFOUND=return] dns mdns4
```

This allows me now to resolve internet names, but not LAN names on my mixed network.

Bug?

Nick

---

### Post by nickmcg on 2009-03-25
It would appear that if the 'wins' entry is placed **at the end** of the hosts line in /etc/nsswitch.conf, everything ***seems*** to work again.

This change seems to have occurred in the last two days' updates.

Nick

---

