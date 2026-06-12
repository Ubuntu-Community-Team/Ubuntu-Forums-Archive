---
title: "Instalation problem with locale"
date: 2005-10-11
forum: Installation &amp; Upgrades
---

### Post by mjaniak on 2005-10-11
Dear all
I have Ubuntu 5.04 and I've tryed to install it on my PC. By default my Ubuntu installs with locale set pl_PL.UTF8 which I don't like to have. When I change locale to pl_PL in the instalation proces, unfortunatelly it hungs up during the time zone configuration. When I don't perform this change the instalation proces goes to the end with no failure.
Do you have any idea what goes wrong?
I will be thankfull for any sugestions.
Best regards,
Mariusz.

---

### Post by raspa_sete on 2005-10-11
try to install it normally.

and then change the locales setting with
```
sudo dpkg-reconfigure locales
```

---

### Post by LiyunYu on 2005-10-11
You may try to install it using the expert mode.
When you boot off the installation CD, at the boot prompt, type 'linux expert".
that will allow you to select different locale support.

---

