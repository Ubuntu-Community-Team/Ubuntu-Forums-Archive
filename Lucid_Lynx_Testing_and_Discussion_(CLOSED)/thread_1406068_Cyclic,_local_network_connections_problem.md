---
title: "Cyclic, local network connections problem"
date: 2010-02-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Husio on 2010-02-13
Hi. I have small local network - 6 linux machines + home server. Few days ago, I've upgrade my server with new machine and instead of debian, I've installed ubuntu 10.04 alpha server.
After that change, I have problem with local connections. From time to time, connection to server hangs. Can't find any reason why is that. Can't create new connections, but the old one are still working (for example, ssh session). After ~60s everything is back to normal. So I've checked bind9 and dhcp3 configuration files and can't find any reason for that.

Any ideas how to solve this problem or what should I search for?

---

### Post by Elfy on 2010-02-14
moved to lucid

---

### Post by Husio on 2010-02-15
Ok, I've solve this problem. 

It wasn't software issue. I'm using usb modem, and new machine had lame power supply. From time to time modem was desynchronizing. After replacing with the one from the old pc, everything works fine.

---

