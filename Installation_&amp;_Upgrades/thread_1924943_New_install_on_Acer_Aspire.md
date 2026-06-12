---
title: "New install on Acer Aspire"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by Shenarah on 2012-02-13
Hi

I just installed Ubuntu 11.10 on An Acer Inspire which previously had Windows Vista but during the installation it failed to connect to the internet. After completing the installation the system and Firefox can get into all the google sites and a handful of others but not the rest. They just sit there loading indefinitely. I booted from the Ubuntu disk again and tried to access from there but the same thing happened.

Can anyone suggest anything please? 

The PC is connecting to Virgin media.

Thanks

---

### Post by wyliecoyoteuk on 2012-02-13
sounds like it is using IPv6 instead of V4.


[http://www.snowfrog.net/2009/01/09/speed-up-firefox-on-linux-disable-ipv6-lookups/](http://www.snowfrog.net/2009/01/09/speed-up-firefox-on-linux-disable-ipv6-lookups/)

---

### Post by Shenarah on 2012-02-14
Don't really understand that. What should I do?

---

### Post by tamkt on 2012-02-14
you can show
ifconfig
ping gateway
ping 8.8.8.8
ping google.com

---

