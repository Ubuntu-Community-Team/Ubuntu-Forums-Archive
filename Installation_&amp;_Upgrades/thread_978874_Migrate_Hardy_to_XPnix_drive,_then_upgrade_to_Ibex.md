---
title: "Migrate Hardy to XP/*nix drive, then upgrade to Ibex"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by spaceboy909 on 2008-11-11
While I'm not a new Linux user anymore, I am still somewhat green on tech stuff, so If my primary objective is just going to be way too messy and problematic, then I can simply do a fresh install of Ibex.

Here's what I want to do:

1) Copy/Migrate my old, and inactive (no longer in the Grub menu) Hardy from my secondary drive

.....TO......

My primary drive which presently has XP/Mint on it.

I will simply reformat the Mint partitions to make way for Hardy, if that will work

I've become very comfortable with basic, single distro partitioning and install/reinstalls, but I imagine this will be different.

2) Once I have migrated Hardy to the main drive, then I will upgrade it to Ibex, unless there are any unforeseen factors that the migration brings to this.

Any help is appreciated.  Even just pointing me to the appropriate, up to date guides on how to do this will be fine.  TIA!

---

### Post by logos34 on 2008-11-12
You can use the [Gparted copying function.]("http://gparted.sourceforge.net/larry/move/move.htm")

Either before or afterward (from the live cd) edit /boot/grub/menu.lst 'groot' and 'root' lines to show the new location of hardy and windows.

Reinstall Grub to the MBR (see link my sig).

good luck

---

