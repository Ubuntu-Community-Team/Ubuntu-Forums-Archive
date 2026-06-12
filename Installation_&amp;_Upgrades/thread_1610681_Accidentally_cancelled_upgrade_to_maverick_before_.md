---
title: "Accidentally cancelled upgrade to maverick before it finished"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by tr333 on 2010-11-01
I accidentally cancelled the upgrade (ctrl-c) to maverick before it finished on one of my servers.  It was during one of the questions about installing an updated config file.  If I run "sudo apt-get dist-upgrade", it complains that it can't lock the directory /var/lib/dpkg.  What can I do to recover this and continue with the upgrade?

EDIT: forgot to say this system is running ubuntu-server with no GUI

---

### Post by garvinrick4 on 2010-11-01
I imagine you are going to have to chroot into install and run all the 
sudo apt-get -f install
dpkg --configure -a
sudo aptitude update && sudo aptitude dist-upgrade
Basically just hope you can save it with the normal commands in chroot in live cd.
make a directory
mount your install
copy etc/resolv.conf to install
chroot into (will now be in root)
run the:
apt-get -f install
dpkg --configure -a
aptitude update
aptitude dist-upgrade
Maybe it starts installing:
If you need full commands leave your sda#

---

### Post by tr333 on 2010-11-01
Thanks for the help.  I managed to get it going again by killing the dpkg process that was still going (no idea why it was still there) and running "dpkg --configure -a".

---

