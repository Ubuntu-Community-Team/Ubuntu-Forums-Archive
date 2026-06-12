---
title: "Apt &amp; Proxy"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by opticalfiber on 2007-04-17
Hi guys,
I tried to install ubuntu at work, but there's a problem, we have a proxy and i can't download packages. how can I set-up a proxy in order to exit the the local network? Also with adept (kubuntu - which is not able to use kde proxy settings, konqueror work, but not adept) and also the ubuntu package manager. thx a lot. :guitar:

---

### Post by Gevatter Tod on 2007-04-20
Adept will only use the proxy settings from the root user. So you must start konqueror as root (sudo konqueror) and set your proxy there. Then adept will work. 

To use apt in your console, you can set the proxy settings in /etc/apt/apt.conf
with Acquire::http::Proxy "http://192.168.0.2:3128";

replace IP and port with your settings.

Regards,
Gevatter

---

