---
title: "bug 470265, install-grub doesn't work..."
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by wbarrett on 2010-01-20
Ubuntu 9.10, the "karmic" version did not fix grub, which still shows only the two previous versions.

This is on a Dell Inspiron, with two disks, sata-1, 4 and 5.  Vista is on sata-1, Linux on sata 4 and 5.  Linux appears as /dev/sdb5.
I rebuilt /boot/grub/menu-list per instructions, and it looks good, with the 9.10 version in first place.  The kernel is at /boot/vmlinuz-2.6.31-17-generic, and initrd at /boot/initrd-img-2.6.31-17-generic.
[FONT=Courier New]
**sudo grub-install /dev/sdb5**[/FONT] does not install the grub list, although it claims to.  **Don't know why**.

What gets installed is the jackalope version, 2.6.18-16, and it has serious problems, for example, have to change splash to nosplash, and often have to run the "repair" version first, which fails, but then the standard version works.  Audio doesn't work.  

This, I assume, is a consequence of using an old kernel in a new set of utilities -- it barely works.

A workaround:
1. On grub bootup, select the old version, type 'e'
2. Use the editor to change the kernel and initrd lines for the new version.  You may have to examine the names in /boot, though I suppose they will be as above.
3. Type control-X.

This is ugly, and I'm waiting for a fix to install-grub.  It appears that this has to be done each time you shutdown or hibernate.  Standby may keep this kernel.

---

### Post by Leppie on 2010-01-20
> **wbarrett said:**
> This is on a Dell Inspiron, with two disks, sata-1, 4 and 5.  Vista is on sata-1, Linux on sata 4 and 5.  Linux appears as /dev/sdb5.
i think you mean partitions 4 and 5. sdb would be your 2nd sata drive with sdb4 and sdb5 partitions on that drive.

> **wbarrett said:**
> I rebuilt /boot/grub/menu-list per instructions, and it looks good, with the 9.10 version in first place.
if you did a clean install of karmic, rebuilding menu.lst is not going to do any good as karmic ships with grub2 which uses grub.cfg. menu.lst is a grub legacy configuration file. if you're still using grub legacy, you may want to try grub2 (it's actually very nice).

> **wbarrett said:**
> [FONT=Courier New]**sudo install-grub /dev/sdb5**[/FONT] does not install the grub list, although it claims to.  **Don't know why**.
it's actually like this:
```
sudo _***grub-install***_ /dev/sdb5
```
notice the inversion of grub and install. also, installing grub to the boot sector of a partition isn't usually what you want (unless you want to use the windows boot loader).

> **wbarrett said:**
> What gets installed is the jackalope version, 2.6.18-16, and it has serious problems, for example, have to change splash to nosplash, and often have to run the "repair" version first, which fails, but then the standard version works.  Audio doesn't work.
was this an upgrade or clean install?

---

### Post by wbarrett on 2010-01-23
:D  grub2 is needed for Karmic upgrade from Jackalope.
I SOLVED the failure of grub to find the Karmic version on a boot, described in previous message, 1/20/2010.
See the grub2 documentation, install "grub-pc", then follow the directions.
You can get grub2 to accept your previous /boot/grub/menu-list, although that will no longer be used, through sudo upgrade-from-grub-legacy.  Check all the /dev/*** entries that appear in the terminal panel -- use the tab key to select an entry, spacebar to click or unclick.  Tab to the <OK> and press Enter.

---

### Post by Leppie on 2010-01-23
yes, reading the documentation often helps a lot ;)
if this is really solved, use the thread tools to set it to solved.

---

