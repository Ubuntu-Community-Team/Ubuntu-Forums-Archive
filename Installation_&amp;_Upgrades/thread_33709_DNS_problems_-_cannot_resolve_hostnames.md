---
title: "DNS problems - cannot resolve hostnames"
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by Buntu on 2005-05-11
I'm using a Linksys WEP-11 wireless bridge to connect to a linksys wifi router. The bridge is connected to my Ubuntu machine on eth0 (copper). I'm using the bridge because the D-Link wifi card I use under Windows is not supported under Linux.

Anyway, my Ubuntu machine is getting an IP through DHCP, and also a list of DNS servers. I can ping all the DNS servers, and I can login to the wifi router, but I cannot resolve names. I can go to any website, as long as I know its IP address. For instance, Google (66.102.7.104) works fine.


/etc/resolv.conf contains the Comcast search domain of my ISP, and the DNS servers obtained through DHCP, but when I ping a host name, like [www.google.com](www.google.com), it comes back immediately with a unkown host message. Same when I launch firefox.

I compared settings with another linux box that's plugged into the same router by ethernet cable, and everything looks the same.

What am I missing here?

---

### Post by harryc on 2005-05-11
What's the result of the following command as run from a terminal as user;

```
cat /etc/resolv.conf
```

---

### Post by Buntu on 2005-05-12
cat /etc/resolv.conf

comcast.net
nameserver 216.148.227.68
nameserver 204.127.202.4

I can ping them too.

---

### Post by harryc on 2005-05-12
Make sure the following are installed on your system, try reinstalling them.

dhcp3-client
dhcp3-common

---

