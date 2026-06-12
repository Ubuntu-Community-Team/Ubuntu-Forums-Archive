---
title: "Dual boot using boot.ini(windows xp)"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by wengkhin on 2008-06-06
................

---

### Post by Sef on 2008-06-06
> How can i dual boot windows xp and ubuntu using windows xp boot loader.Too bad now i cant reverse it because i have remove the ubuntu boot loader.And now i have to do this only,i even cant access into ubuntu but i still can access to windows xp......ty

You can't.  Windows only recognizes other Windows OSes.  You have to use GRUB or another boot loader to dual boot.  To reinstall GRUB, use the [Super GRUB Disk]("http://www.supergrubdisk.org/").

---

### Post by logos34 on 2008-06-06
> **Sef said:**
> You can't.  Windows only recognizes other Windows OSes.  You have to use GRUB or another boot loader to dual boot.[/URL].

Actually you can use windows to boot linux (edit boot.ini + grldr).  The easiest way is probably [WinGrub]("http://users.bigpond.net.au/hermanzone/p9.html").

But unless you have a compelling reason to use Windows bootloader, it's best to stick with Grub.  It's a lot better and more versatile.

---

