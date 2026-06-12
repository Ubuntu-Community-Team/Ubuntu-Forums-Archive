---
title: "Ubuntu + XP + Vista"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by danielcs on 2006-07-01
Hello everybody, I'm not sure but I guess this is the correct section to ask.

I already have a dual boot system with Ubuntu and XP.
Now I also want to install Windows Vista BETA 2 and have the 3 OSes at the same time.

I'm almost sure that if I install Vista it will remove GRUB and install it's own boot loader. I'm also aware that it is possible to [reinstall GRUB]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

So now what I need to know is if GRUB can detect Vista too.

Thanks in advance.

---

### Post by rbalfour on 2006-07-01
The most recent posts I have seen, stated that the GRUB is having issues with Vista. You could try using QEMU or XEN to test vista. It may not be the quickest thing, but at least it's safe.

---

### Post by danielcs on 2006-07-01
Thank you rbalfour, very helpful.
I'll see if I can play with QEMU or XEN. :)

---

