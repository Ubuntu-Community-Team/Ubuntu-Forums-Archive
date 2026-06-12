---
title: "Uninstall Kubuntu"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by lagaile on 2008-05-07
I need to uninstall Kubuntu. My husband doesn't care for it. Is there an easy way to do this? I don't want to destroy my system. I've read alot of negative things about uninstalling it.

---

### Post by lemming465 on 2008-05-10
When you say *uninstall kubuntu* it's not clear if you mean "switch to the ubuntu desktop because a Gnome fan hates KDE", "remove it from the disk", or "just boot the other OS".

Switching to the ubuntu Gnome desktop could be as simple as "apt-get install ubuntu-destop".  You can either leave the kubuntu-desktop package installed (which is what I do), or remove it if you really need to eradicate kde for some reason, e.g. not enough disk space.

If you want Ubuntu off the disk, and it dual boots windows xp or something, the easiest thing would be to reformat the Kubuntu partition.  That is best done from a live linux CD, perhaps the one you installed from.  You'd need to run some kind of boot recovery steps afterwards; the details vary depending on which version of the other OS (windows 2000? xp? vista?) is involved.  This is a little tricky but quite doable.  I think the gparted from a live CD might be able to expand NTFS partitions if you wanted to reclaim the Linux space as part of a c: partition

If the object is to simply hide the kubuntu boot option, edit /boot/grub/menu.lst to make sure that the number after the "default" line corresponds to the OS you want booted (grub counts from 0, not 1), and remove the "#" from the "#hiddenmenu" line.

I'm not sure if this helped any; if it didn't, please describe what you are trying to do in more detail.

---

