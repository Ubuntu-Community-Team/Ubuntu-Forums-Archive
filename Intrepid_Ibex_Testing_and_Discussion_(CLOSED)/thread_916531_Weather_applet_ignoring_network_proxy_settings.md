---
title: "Weather applet ignoring network proxy settings"
date: 2008-09-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by alphacrucis2 on 2008-09-11
Not sure if this is specifically a problem in this version but I noticed the weather applet was failing to update the weather, The issue seems to be that it is ignoring the system proxy server settings specified under System/Preferences/Network Proxy. The proxy settings work for the Web browsers I have tried but a trace shows that the weather applet is trying to connect direct to ip address 140.90.128.70:80. The Coy firewall is dropping the connection. May be that this applet has never supported using a proxy server? I don't have an older version of Ubuntu installed to check.

---

### Post by stats on 2008-10-04
i second this.
The weather applet ignores proxy settings. It used to work on hardy.

---

