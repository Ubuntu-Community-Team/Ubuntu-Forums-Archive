---
title: "rabbitmq-server not stopping during upgrade"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by fisch246 on 2011-10-14
It has been more than 15 minutes, and it has still not stopped. I am upgrading from 11.04 to 11.10. Is this normal? I can't seem to get a terminal running, so is there a way I can stop it outside of a terminal? Should I wait longer? I can get a live-usb, back stuff up, and install it if need be. I'd rather not do this obviously.

---

### Post by fisch246 on 2011-10-14
ok so i went into tty1 and logged in, tried to stop it with upstart, but it said it was an unknown job... anyone know the job title of rabbitmq-server?

---

### Post by fisch246 on 2011-10-14
found out i did the command wrong. sigh. unfortunately it says "no nodes running rabbitmq-server" -__- so something is going wrong with the upgrade program it seems

---

### Post by fisch246 on 2011-10-14
ah found the real issue... the upgrade program froze...

---

