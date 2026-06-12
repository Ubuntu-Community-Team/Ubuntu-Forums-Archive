---
title: "tty1 console after software update"
date: 2015-03-15
forum: Installation &amp; Upgrades
---

### Post by gasior.tt on 2015-03-15
Ubuntu 14.04.2 . I have nvidia drivers from xorg edgers installed on my machine. After running update manager and updating system I can't login to GUI no more. Boot proccess stops at tty1 console.

Running ubuntu in failsafeX mode gives me this:

[IMG]http://oi57.tinypic.com/29prynq.jpg[/IMG]

Thanks in advance

---

### Post by arunsingh.in on 2015-03-15
It must be a driver mismatch problem, sudo lshw -C display and lspci -nn | egrep VGA Check Your actual hardware settings and download appropriate driver from official site, else use Open source driver.

---

### Post by gasior.tt on 2015-03-22
[IMG]http://s23.postimg.org/u38sw3qzf/20150322_132827.jpg[/IMG]

How to  install the "right" driver?

---

