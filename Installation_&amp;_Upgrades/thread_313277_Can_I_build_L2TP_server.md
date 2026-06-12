---
title: "Can I build L2TP server?"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-12-05
Is there any instruction on how to build an l2tp server?

---

### Post by PilotJLR on 2006-12-05
L2TP is less secure than a more modern IpSec or SSL VPN... you may want to consider using OpenVPN, which can implement a client-based SSL VPN:
[http://openvpn.net/](http://openvpn.net/)
They have a Windows client program too.

A client-less (browser based) SSL VPN option is:
[http://sourceforge.net/projects/sslexplorer/](http://sourceforge.net/projects/sslexplorer/)

---

