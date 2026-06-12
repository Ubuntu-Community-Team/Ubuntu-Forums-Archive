---
title: "Installing another distro alongside Ubuntu"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by dizzy1234 on 2005-10-25
Just out of curiousity, if I decide I want to use a different distro (I don't, yet, but I'm curious about this) if I install it on the disk that currently has the lovely Ubuntu, will I be able to keep the same files, setup, applications etc. without massive disruption?

---

### Post by brentoboy on 2005-10-25
no.

the only thing you can do without serious disruptions, (or at least significant pre-planning and wisdom) is have /home be on its own partition, and use it with both distros.

Each distro really ought to have its own partition for just about everythine else.

---

### Post by rickmans on 2005-10-25
[QUOTE=dizzy1234]Just out of curiousity, if I decide I want to use a different distro (I don't, yet, but I'm curious about this) if I install it on the disk that currently has the lovely Ubuntu, will I be able to keep the same files, setup, applications etc. without massive disruption?[/QUOTE]

it is possible. You could create a new empty partition for the other distro (with i.e. gparted) and you could install the other distro on this new partition. You could you a bootloader like GRUB to create a dual (or more) boot system.

---

### Post by aysiu on 2005-10-25
[QUOTE=brentoboy]
the only thing you can do without serious disruptions, (or at least significant pre-planning and wisdom) is have /home be on its own partition, and use it with both distros.[/QUOTE] I wouldn't advise this. Different distros handle config files differently sometimes--you may run into conflicts. I'd just copy over the "main" config files (email and internet) and tweak the rest manually. For example, if you use Thunderbird and Firefox, you'd copy over your /home/dizzy1234/.mozilla and /home/dizzy1234/.mozilla-thunderbird folders to the new distro.

If you don't have time to tweak a new distro, you don't have time to try a new distro.

---

