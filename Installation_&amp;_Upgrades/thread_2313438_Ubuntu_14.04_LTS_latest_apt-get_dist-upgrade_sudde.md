---
title: "Ubuntu 14.04 LTS latest apt-get dist-upgrade suddenly locks the account"
date: 2016-02-12
forum: Installation &amp; Upgrades
---

### Post by my_name7 on 2016-02-12
Hi,

I was just running the latest apt-get (dist-)upgrade on default Ubuntu 14.04 LTS and saw something that has not happened to me before. The Upgrade is running in the terminal and suddenly I'm locked out of the
account and the login screen appears. I can log in again and system boots ok, but why is it that I got locked out?

Cheers

---

### Post by grahammechanical on 2016-02-12
You want a guess?

A package was upgraded that changed the lock screens settings or the turn screen off settings. Perhaps taking them back to the default settings and the screen timed out.

Regards.

---

### Post by my_name7 on 2016-02-12
Thank you for your response. I narrowed it down to the upgrade of one of following three packages: libpam-systemd, libsystemd-daemon0 or systemd-services. I can see that pam is related
to login, but the immediate lockdown is still rather unexpected.

---

