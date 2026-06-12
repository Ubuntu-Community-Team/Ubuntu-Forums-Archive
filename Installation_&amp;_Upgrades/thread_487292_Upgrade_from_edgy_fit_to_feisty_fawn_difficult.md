---
title: "Upgrade from edgy fit to feisty fawn difficult"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by klugja on 2007-06-28
I used the upgrade gui tool.  It got lots of isntall errors.  When I first booted, it couldn't find the root drive.

I messed around with changing device.map, and things got worse.  Then the normal boot said that my cylinder was beyond the maximum number supported by the BIOS.

It does boot from recovery mode, but I noticed that /etc/inittab is missing.

When I initially booted, root was on /dev/hdc2, but it used to be /dev/hda2 before the upgrade.  Recpvery mode fixed this.

If I do telinit 5, I get the GUI (gnome).

The update manager says my system is up to date.

So how do I get the default boot to work?

I assume I have to do something wtih grub?

---

### Post by klugja on 2007-07-02
I put UUID's into fstab to take care of the traveling root problem.  I also noticed that initab is supposed to be gone, and the new default run level is 2, and the upgrade didn't care what the old defalut run level was before the upgrade.

The upgrade fixed HAL, which always aborted with an error in Edgy.

---

