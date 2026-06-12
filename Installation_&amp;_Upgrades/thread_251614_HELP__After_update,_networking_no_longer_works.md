---
title: "HELP:  After update, networking no longer works"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by theosib on 2006-09-05
I just performed an update, and suddenly, I have no networking.  I have gkrellm (a system monitoring tool), and it can't even see there being an eth0.  It's like the kernel got updated or something, and I no longer have support for networking devices.

Can anyone help?

---

### Post by theosib on 2006-09-05
I think I figured out what happened.  I have two network controllers.  One is an onboard VIA Rhine (that I don't use), and the other is a PCI Intel 10/100.  As best as I can tell, before the upgrade, the Intel was eth0, but now it's eth1, so I when I fiddled around in the system config program and dis/enabled things correctly, I came back online.  That's messed up.

---

