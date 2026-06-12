---
title: "xp on seperate harddrive"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by psykotrol on 2007-12-11
how would I go about installing windows xp home on a seperate harddrive with ubuntu on the primary harddrive? id rather not make a partition, just the whole drive, is that possible?

is it as simple as installing it on another harddrive, and using grub to boot from it? any configurations/tweaks id have to do?

---

### Post by Emerzen on 2007-12-11
The best way, IMHO:

1.  Install XP to the first drive on your system and install it first.
2.  Then install Ubuntu to the second drive.

By doing it this way you simplify your life.  By installing XP first, when Ubuntu installs, it recognizes XP and configures GRUB to load either OS.  If you install XP after, XP very rudely ignores Ubuntu, and overwrites the MBR w/ it's own bootloader.  You'll have to use a recovery disk to restore GRUB if you do it this way.  It's not complicated, but why bother?

---

### Post by PmDematagoda on 2007-12-11
Yes you can, it should not pose a problem when installing XP(Just make sure you install XP in the right place or else you might lose Ubuntu).

But after installing XP you will need to reinstall GRUB to the MBR, you can use [Super GRUB]("http://supergrub.forjamari.linex.org/?section=download") to do this, after you reinstall GRUB you can then add the necessary entry required to boot XP into the menu.lst file, that should complete the dual-boot setup.

---

