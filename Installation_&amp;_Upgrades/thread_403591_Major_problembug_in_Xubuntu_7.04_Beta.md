---
title: "Major problem/bug in Xubuntu 7.04 Beta"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by CC_machine on 2007-04-07
ok, so i decided to try out Xubuntu 7.04 beta on my desktop... liked it for a while :) until i decided to try upgrading and dist-upgrading.

i did
apt-get update
apt-get upgrade
apt-get dist-upgrade
after i rebooted, I noticed I cant mount, unmount, eject devices!

if i try to, I get the following message:
[B]Failed to unmount "138G Volume".
Failed to execute child process "gnome-umount" (No such file or directory).[/B] (for example)
in a popup dialog.

I can mount and unmount things via the commandline though, but this should work!

---

### Post by pgergely on 2007-04-09
Same here... :( gnome-umount and gnome-eject errors. o.O 
However, manual umount works.

---

### Post by pgergely on 2007-04-12
The last upgrade/dist-upgrade solved the problem, everything works fine now.

---

