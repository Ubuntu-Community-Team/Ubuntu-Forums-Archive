---
title: "configure: error: Package requirements (ortp)"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by Wael.A.ELbreky on 2011-06-27
[SIZE=3][COLOR=DarkRed]how can i solve this error[/COLOR][/SIZE][SIZE=3][COLOR=DarkRed]?[/COLOR][/SIZE]


configure: error: Package requirements (ortp) were not met:

No package 'ortp' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ORTP_CFLAGS
and ORTP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

[SIZE=3][COLOR=DarkRed] thanks in advanced[/COLOR][/SIZE]

---

### Post by jerrrys on 2011-06-27
what package are you trying to install that requires this?

---

### Post by Wael.A.ELbreky on 2011-06-28
> **jerrrys said:**
> what package are you trying to install that requires this?


[SIZE=3][COLOR=DarkRed]i want to run the code of open BTS and when i make ./configure this error appear.
[/COLOR][/SIZE]

---

### Post by oldos2er on 2011-06-28
> **Wael.A.ELbreky said:**
> [SIZE=3][COLOR=DarkRed]how can i solve this error[/COLOR][/SIZE][SIZE=3][COLOR=DarkRed]?[/COLOR][/SIZE]


configure: error: Package requirements (ortp) were not met:

No package 'ortp' found

It's probably looking for libortp-dev

---

### Post by Wael.A.ELbreky on 2011-06-29
> **oldos2er said:**
> It's probably looking for libortp-dev



[SIZE=3][COLOR=DarkRed]thanks alot[/COLOR][/SIZE]

---

