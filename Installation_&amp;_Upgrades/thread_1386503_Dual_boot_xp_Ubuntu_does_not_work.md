---
title: "Dual boot xp Ubuntu does not work"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by goatrance on 2010-01-20
Hi,
 
i tried to install ubuntu as dual boot with xp. xp was installed first, second ubuntu. Installation worked perfect.
 
The boot does not work, because xp is booted only as before the installation. There apears no but menu of grub. Therefore i am not able to start ubuntu.
 
I describe the hard disk from the view of windows as follows:
 
Device 0: Raid (Mirror)
Device 1: non raid disk, but system partition of windows
 
On Device 1 i created a second partition for ubuntu and a third one for swap partition.
 
The view of ubuntu was i the installation from ubuntu live cd as follows:
 
/dev/sdc2: ext4 as "/" (root)
/dev/sdc5: swap
 
In live cd installation you can press a button advanced before the installation begin. There you can entry where the boot manager has to be installed. Ubuntu suggested hd0. I keept this entry and began to install. The result is, that windows is booted immediately after restart and no grub menu appeared.
 
What I made wrong?
 
Greatings,
 
Stephan.

---

### Post by goatrance on 2010-01-21
Hi,

the problem is solved. I only need to click on advanced button of live cd installation to second hard disk. Now the grub menu is displayed after reboot with xp as dual boot. Both OS could be loaded.

Greatings,

Stephan.

---

