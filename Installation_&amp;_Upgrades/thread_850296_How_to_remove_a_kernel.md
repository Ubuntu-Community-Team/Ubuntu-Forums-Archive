---
title: "How to remove a kernel?"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by ravenpi on 2008-07-05
Because of a module package that's not in 2.6.22-15-server (but is in 2.6.22-14-server), I need to downgrade from the one to the other.  So, great, I just swap a few things around in /boot/grub/menu.lst, and it boots up into 2.6.22-14-server.

But.

For whatever reason, some behind-the-scenes magic doesn't happen.  And lo, my lvm2 partitions won't mount.  A re-install of lvm2 has it regen the initrd... for 2.6.22-15-server.  D'oh!  So I say, "Well, just uninstall 2.6.22-15-server, and then a re-install of lvm2 will regen initrd for the right kernel."  But nooooo:

root@virtual-4:/boot/grub# dpkg --remove linux-image-2.6.22-15-serverdpkg: dependency problems prevent removal of linux-image-2.6.22-15-server:
 linux-image-server depends on linux-image-2.6.22-15-server.

So... how do I either remove it gracefully, or force a removal?  I'm kinda stumped, here.

Thanks!

---

### Post by PmDematagoda on 2008-07-05
About the initrd problem, why not try updating all init images? You can do that with:-
```
sudo update-initramfs -c all -u
```

---

### Post by ravenpi on 2008-07-05
Small point of order; the syntax is actually:
sudo update-initramfs -c -k all -u

Big point of order: it worked like a champ!  Thanks so much; I'd never re-genned an initrd using update-initramfs before; I've rolled by hand, and boy, is that a PITA.  

Again, thanks!!

-Ken

---

### Post by PmDematagoda on 2008-07-05
Whoops, I knew something was wrong there. Anyway, I'm glad that you figured it out:).

---

