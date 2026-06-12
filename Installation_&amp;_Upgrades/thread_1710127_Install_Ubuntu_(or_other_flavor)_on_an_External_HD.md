---
title: "Install Ubuntu (or other flavor) on an External HDD."
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by miniCruzer on 2011-03-19
Since the Internal HDD is practically fried (not entirely) on one of my old computers, I want to use my external HDD in replacement (USB 2.0), and be able to mount / boot (whatever term is correct) to the real operating system.

---

### Post by Hedgehog1 on 2011-03-19
> **miniCruzer said:**
> Since the Internal HDD is practically fried (not entirely) on one of my old computers, I want to use my external HDD in replacement (USB 2.0), and be able to mount / boot (whatever term is correct) to the real operating system.

If your old computer's BIOS allows booting off of USB, this can be as easy as changing the boot order in BIOS to try the USB first.

If the system is old enough to not support boot from USB; all is not lost.  The 'plop' CD will allow you to load USB drivers and then still boot from the USB drive.

***The Hedge***

:KS

---

### Post by miniCruzer on 2011-03-19
> **Hedgehog1 said:**
> If your old computer's BIOS allows booting off of USB, this can be as easy as changing the boot order in BIOS to try the USB first.


It does, but I just need to know how to install it to the hard drive. My guess is that I open the installer (boot from CD) and point it to the USB drive, which I'm trying now...

---

### Post by Hedgehog1 on 2011-03-19
Most likely, the external hard drive will be /dev/sdb.  You can install to sdb.

You COULD disconnect the internal hard drive during the external drive install.  /etc/fstab will use UUIDs so it should work just like when I boot off my USB stick.

Just a thought...

***The Hedge***

:KS

---

