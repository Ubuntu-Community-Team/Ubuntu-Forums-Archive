---
title: "Heavy permissions problem"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by v3rtigo on 2008-08-15
Ok everything start that i want to change something and did sudo nautolius
and by accident i don't even know how, everything got so bad, i couldn't do anything anymore got permission denied to everything too.

so i rebooted, and even on boot time i got permission denied almost on everything, so i took a livecd to check the problem with chroot
but guess what i couldn't even chroot, i got permission denied even when i tried to chroot, problem was i couldn't use /bin/bash.

so as a last resort, i mounted my root dir in the livecd, and just did
chmod -R 777 root

so basically all my file system is owned by root and have chmod 777, i loged back in to my system without a problem except some gnome warning to start restoring (manually) everything but from some reason i couldn't use sudo, everything i tried i just got
must be setuid root

so now i'm stuck.

and btw, whats the permissions i need for all my filesystem?

and what user should own it?

and how do i chown all folders and files that are in some folder?

and basically what i need to do except reinstall?

---

