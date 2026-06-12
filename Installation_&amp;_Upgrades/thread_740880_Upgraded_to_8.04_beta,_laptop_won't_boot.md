---
title: "Upgraded to 8.04 beta, laptop won't boot"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by Danners on 2008-03-31
I've just upgraded from 7.10 to 8.04 beta via the update-manager. When booting now the bar on the splash screen scrolls from left to right, but there's no activity, appears to be doing nothing.

If I press escape and boot kernel 2.6.24-12-386 recovery mode, it gets as far as the line below then stops.

> Time: acpi_pm clocksource has been installed

If I choose kernel 2.6.24-12-386-generic it boots into gnome fine.

Being a bit of a noob with ubuntu, I'm not sure how I report this apparent bug. Can anyone help?

Thanks.

---

### Post by Danners on 2008-03-31
Forgot to mention, I have a Toshiba Portege M200.

---

### Post by Danners on 2008-03-31
For the time being I've changed what option to boot in /boot/grub/menu.lst, anyone have any idea what could cause this and what I'm potentially losing out on booting with a "generic" kernel instead of the i386 one?

Cheers again!

---

### Post by Joeb454 on 2008-03-31
If you're running 32 bit, then no there's not much difference as far as I'm aware :)

Also this is why Hardy (8.04) is still in Beta ;)

---

### Post by Danners on 2008-03-31
Yeah, I was expecting a few issues considering it's still beta, other than this minor problem though it's all been fine!

---

