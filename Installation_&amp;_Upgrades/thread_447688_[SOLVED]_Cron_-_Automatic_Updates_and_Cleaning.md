---
title: "[SOLVED] Cron - Automatic Updates and Cleaning"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by altonbr on 2007-05-18
My current cron tab for root looks like so:

> 15 9 * * * aptitude update && aptitude upgrade -y && aptitude autoclean  >/dev/null 2>&1 

That is supposed to be 9:15am correct? It doesn't seem to be doing it's job whatsoever. When I 'su root' and then run 'aptitude update && aptitude upgrade -y && aptitude autoclean', it works perfectly.

Does anyone know what's going on here?

---

### Post by altonbr on 2007-09-16
Well apparently bash doesn't understand '&&' so there is a blueprint here: [https://blueprints.launchpad.net/ubuntu/+spec/auto-update](https://blueprints.launchpad.net/ubuntu/+spec/auto-update) and a wiki note here: [https://wiki.ubuntu.com/auto-update-blueprint](https://wiki.ubuntu.com/auto-update-blueprint)

---

