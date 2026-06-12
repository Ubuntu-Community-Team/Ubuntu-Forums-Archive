---
title: "Edgy Eft: Grub menu hidden and invisible"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by tnilsson on 2007-01-02
I have done  a dist-upgrade from Dapper to Edgy Eft on tree of my machines.
Discovered that the grub menu i hidden and INVISIBLE.
When I press Escape to see the menu, I only see the mouse pointer in 
the upper left corner, if I use the arrow keys I can choose another
line in the grub menu (but it is invisible).

This problem does not occur after a fresh install.
Does anyone has a solution on this problem?

:confused:

---

### Post by bernied on 2007-01-02
Is this because of the grub splash image? You can test this by commenting out the splashimage line in /boot/grub/menu.lst
Perhaps grub is not reinstalled properly on a dist-upgrade.

---

