---
title: "Triple Boot: XP, SUSE, Ubu8.04"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by Phlll on 2008-06-26
I've been dual-booting for a while with XP and Ubuntu, and can make that work very well. Today I'm trying to add an openSUSE partition and am having a few issues.  Just looking for some help for the following:

1. Linux sees the whole volume as one drive, obviously.  Is there any way to tell the distros to ignore each other?

1a.  If there is no way to have the distros ignore each other, how can I use the same account name without borking one of the installs?

2. Since only one distro will be running at a time, is it OK if I only have one swap partiton?

Hoping to hear something soon!

---

### Post by logos34 on 2008-06-26
yes to 1a & 2.  You can also use the same name and even password (i do) for each OS.

not sure what you mean in 1...When you install suse, it will detect the other OSs and add entries for them to both /boot/grub/menu.lst and /etc/fstab.  You can remove the fstab entries for windows and ubuntu in the suse fstab if you don't want it to mount those partitions.  But you will have to make a choice which grub you want to use--ubuntu's or suse's.  If the latter (probably the easiest since last installed), let suse overwrite the MBR with it's own grub.  On reboot grub menu screen should lists all 3 OS choices.

---

### Post by Phlll on 2008-06-26
Thanks!  I'll try that later today.  I'll probably just reinstall Ubu so everything is nice and tidy.

:)

---

