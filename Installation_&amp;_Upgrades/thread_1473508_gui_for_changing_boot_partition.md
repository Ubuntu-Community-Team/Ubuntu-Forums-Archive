---
title: "gui for changing boot partition?"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by zim2dive on 2010-05-05
In prep to do an upgrade from 9.10 to 10.04, I created

- shrank my startup partition (sda1) (moved all my data files out to a different partition)
- created another partition of the same small size (sdb2)
- used CloneZilla do copy my original partition (sda1) to this new (backup/sandbox) partition (sdb2, on a 2nd HDD)

What I'd like to do now is make it so that my machine boots from this other partition.  (at which point I can try the upgrade, and if there are issues, I can just re-point back to my original startup partition)

I'm not quite sure what I need to do.

I suspect I might be able to edit menu.lst, and possibly set the boot flag with gparted, and possibly change the HDD boot order in my BIOS, but my experience from other OSes makes me hope there is a much simpler, and less error prone way to do this.. perhaps a GUI for GRUB? When I look thru the System/Admin menus for 9.10, I don't see any such creature.  Also not sure if I have to install a bootloader on the 2nd HDD?

PS. I never upgraded to GRUB2 when I upgraded from 9.04 to 9.10, in case that matters.

thanks for any pointers! (and/or corrections to my plan for upgrading)

---

