---
title: "mount unetbootin filesystems?"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by gregwm on 2010-10-13
on top of ole xp (all covered with cheese), first i tried lucid wubi but it crashed, wouldn't start.  so i (frugal) installed xubuntu lucid via netbootin, then (full) installed lucid via netboot.  no cd used.  works great.  anyway my question, now that i'm here, i'm interested to mount the unetbootin user filesystem that's still hiding in ntfs.  how might i find and mount it?  i suspect there's some deep voodoo re unionfs, but still i'd expect it to boil down to a couple commands with a little light shed...?

---

### Post by sgosnell on 2010-10-13
What filesystem are you talking about?  Unetbootin has no filesystem, it's just a program that writes a .iso to a disk.  If you mean the .iso filesystem, that's easy enough to mount.  Just navigate to it through Places, right-click on the .iso and select 'Open with Archive Mounter'.  It will show up as a drive in Nautilus.

---

### Post by gregwm on 2010-10-14
hi thanks yeah i got the squashfs ok but i was thinking (dreaming?) there was a persistent filesystem for saving user data.  hmm.  could well be i'm mixing my memories.

---

### Post by sgosnell on 2010-10-14
The Ubuntu startup disk creator allows making the USB drive perisistent for saving user data, but it has nothing to do with unetbootin.

---

