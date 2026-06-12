---
title: "Solved odd Jaunty pptp issue"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by snaga on 2009-04-02
I've had a strange issue with vpn on Jaunty for the last few days since I installed it.

I found that even though I had network-manager-pptp installed, that vpn type was not available when I tried to create a vpn connection. I finally figured out that I was missing /etc/NetworkManager/VPN/nm-pptp-service.name

I recreated that file, as it is here:

```
[VPN Connection]
name=pptp
service=org.freedesktop.NetworkManager.pptp
program=/usr/lib/network-manager-pptp/nm-pptp-service

[GNOME]
auth-dialog=/usr/lib/network-manager-pptp/nm-pptp-auth-dialog
properties=libnm-pptp-properties
```

As soon as I added this file, I was able to create a pptp vpn which worked. Not sure why that file wasn't there.

---

