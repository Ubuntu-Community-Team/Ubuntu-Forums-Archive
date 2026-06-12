---
title: "OK! Reinstalled windows and you know what happened :)"
date: 2005-09-20
forum: Installation &amp; Upgrades
---

### Post by kzu on 2005-09-20
So how can I return Grub so I could boot to Ubuntu again? I have ubuntu live cd and others, just tell me what to do :)

---

### Post by SilentCacophony on 2005-09-20
Hello. Look [here](http://ubuntuforums.org/showthread.php?t=24113).

---

### Post by az on 2005-09-20
Losta different ways of doing it on that thread!

I think the safest is to boot, chroot and run grub install.

Boot the installer and let it detect all your hardware (when you see the partitionner, Hit CTRL-ALT-F2 to enter a terminal)

type mount /dev/hda5 /mnt 

# Now, I am assuming that hda5 is where you had installed ubuntu.  Be sure to put the appropriate device there!

Type chroot /mnt
grub-install /dev/hda
#Again, assuming hda !  Put whatever is appropriate!


Reboot.

---

