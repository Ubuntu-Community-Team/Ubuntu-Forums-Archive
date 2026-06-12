---
title: "Need Ubuntu entry for FreeBSD's grub2"
date: 2012-02-10
forum: Installation &amp; Upgrades
---

### Post by bingasedu on 2012-02-10
I have a machine with FreeBSD 9.0-RELEASE on one drive, and Ubuntu 10.04 LTS on another drive. The BIOS looks at the FreeBSD drive first when booting, and it doesn't have the ability to change the boot order among different drives. In the past (pre-FreeBSD 9.0), I installed grub on the FreeBSD drive from Ubuntu, added a FreeBSD entry to the grub.d directory and everything worked fine.

Unfortunately, FreeBSD 9.0 uses a GUID partition table, so Ubuntu is no longer able to install grub on the FreeBSD drive. To work around this I booted into FreeBSD 9.0 and installed it's version on grub2 on that drive, but it didn't find Ubuntu on the other drive. How do I go about adding an Ubuntu entry to FreeBSD's grub.d directory? Thanks for any help.

---

### Post by darkod on 2012-02-10
It doesn't detect it even with update-grub?
If it uses grub2 it should detect all OSs automatically with update-grub.

---

### Post by bingasedu on 2012-02-10
Sadly, no. FreeBSD doesn't have update-grub, but I think update-grub is just a stub for grub-mkconfig -o /boot/grub/grub.cfg, which I ran. Perhaps it would have picked up Ubuntu if it were on the same disk, but that's not my setup. I thought perhaps I could use Ubuntu's own entry as a starting point, but I don't understand it well enough to know how to modify it to work on FreeBSD. For what it's worth, Ubuntu's grub was never able to pick up FreeBSD either. I manually created an entry for FreeBSD.

---

