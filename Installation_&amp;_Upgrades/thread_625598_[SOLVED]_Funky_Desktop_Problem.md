---
title: "[SOLVED] Funky Desktop Problem"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by finni on 2007-11-28
I've got this funky problem with my desktop. My desktop home directory is actually a symbolic link and that symbolic link does not automatically work - it needs a working network connection with NFS. With Feisty all worked fine after logging in second time after NFS connections were around, but with Gutsy things changed. With Gutsy I seem to be having my home directory as my desktop directory with it's files for an very unobvious reason. Is there a place I can change the desktop directory of Gnome manually back to point to the symbolic link directory /home/USERNAME/desktop ?

Thanks in forehand if you happen to know the answer. :guitar:

---

### Post by finni on 2007-11-30
Where is the Desktop directory setting of Gnome/Nautilus? Does anybody know?

I've tried looking through files under .gconf, .gconfd, .gnome, .nautilus, with no luck. :confused:

---

### Post by finni on 2007-11-30
Found the answer / bug:

[https://bugzilla.redhat.com/show_bug.cgi?id=251301#c2](https://bugzilla.redhat.com/show_bug.cgi?id=251301#c2)

The desktop directory setting was located in this file:
~/.config/user-dirs.dir

---

