---
title: "Can't access after upgrade"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by fiftyfour123 on 2010-10-17
I just upgraded my server with Ubuntu 9.04 desktop to 10.04 over VNC. Installation wen't smooth, then it asked to reboot. I clicked reboot and now I cannot connect to the server at all. No apache, ssh, ftp, vnc, nothing. I assume I just need to hook it up to a monitor and change some network settings. Hopefully I'm wrong as I'm 400 miles away and won't have access to it for a month and a half. Is there anything I can do remotely, or will I just have to wait?

---

### Post by yeats on 2010-10-17
Unless you have someone who can physically visit the machine to investigate, you'll probably have to wait, sorry to say...

---

### Post by fiftyfour123 on 2010-10-17
> **chrissharp123 said:**
> Unless you have someone who can physically visit the machine to investigate, you'll probably have to wait, sorry to say...

Yeah, I thought so. But I just found out from someone who is on the same LAN as the server that he was able to access websites that are being hosted on the server.

What could have happened in the upgrade to 10.04 that would cause the server to only be available on the LAN?

All the ports are forwarded so that's not the problem.

EDIT: I can connect to the router that the server is connected to and I don't see the server's MAC address in the list of connected clients. How can this be possible? Is the person who said the site was working just mistaken?

---

### Post by fiftyfour123 on 2010-10-17
Oh wait, now it is showing up in the router. So if it has internet, why can't I connect to it?

---

### Post by fiftyfour123 on 2010-10-18
anyone?

---

### Post by fiftyfour123 on 2010-10-18
Fixed it. I just had to run

```
sudo route add default gw 192.168.1.1
```

---

