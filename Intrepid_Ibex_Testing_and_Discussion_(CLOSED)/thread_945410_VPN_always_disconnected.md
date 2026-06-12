---
title: "VPN always disconnected"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by VirtualEdgar on 2008-10-12
I'm using NM to connect to you Windows VPN server at work. I was able to connect successfully but always got disconnected in 5 to 10 minutes. Checked the logs and here is what I saw before the hangup.

> Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.

Using wlan0 to connect to the internet by the way. Anyone experienced this?

Thanks!

---

### Post by spiderbatdad on 2008-10-12
Not sure if this is the problem, but generally an idle session will disconnect unless keepalive time is set somewhere. In putty for example,under the connection menu you would set seconds to keep alive 120. This makes sure the connection doesn't go idle. Similarly in sshd.config TCPKeepAlive=yes.

---

### Post by wolfie2x on 2008-10-12
I had the same problem (different error msg though) and the .deb from the following link worked for me.

[https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/206673/comments/4]("https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/206673/comments/4")

the related bug report:  [https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/206673]("https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/206673")

---

### Post by VirtualEdgar on 2008-10-12
Thanks for the reply sirs!

Will try the deb files wolfie2x.

By the way, i'm using Intrepid Ibex. :)

---

### Post by VirtualEdgar on 2008-10-12
> **wolfie2x said:**
> I had the same problem (different error msg though) and the .deb from the following link worked for me.

[https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/206673/comments/4]("https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/206673/comments/4")

the related bug report:  [https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/206673]("https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/206673")

Problem solved! Thanks to you!

---

### Post by jack frost on 2008-10-19
> **wolfie2x said:**
> I had the same problem (different error msg though) and the .deb from the following link worked for me.

[https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/206673/comments/4]("https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/206673/comments/4")

the related bug report:  [https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/206673]("https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/206673")
Thanks for that post.. my vpnc kept disconnecting after  30 secs.. went to that link and now I can connect to my work computer just fine.. I now do not have to use XP virtual box to connect.. All I need now is a good phone that can sync in Ubuntu and I can be 100% windows free.

---

