---
title: "xp installation on ibex box?"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by Cobbs on 2008-11-30
Would it just be easier to do a clean install of Ubuntu after installing XP, or is there a way to install XP on a computer only running Ubuntu.  I want to dual-boot to run some games, and if I can do this without losing all my ubuntu settings it would be great.  If anyone can point me in the right direction... Otherwise I'm just gonna wipe Ibex and install XP first.

Cheers,

Cobbs

---

### Post by taurus on 2008-11-30
You can use gparted from the LiveCD and shrink your Ubuntu partition, making some  space at the beginning of the harddrive.  Then, create a primary partition out of that space and format it to ntfs.  Now, just install your XP on that.  But of course, XP will wipe GRUB off MBR so you need to reinstall GRUB with the LiveCD again so you can boot both OSes.

---

