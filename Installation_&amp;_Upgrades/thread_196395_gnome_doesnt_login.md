---
title: "gnome doesnt login"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by galileon on 2006-06-14
hello everyone,
i had a system setup as follows:
sda1 - ubuntu root / -reiser
sda2 - /mnt/woes  -ext3
sda5 - swap
sda6 - /home - reiser
sda7 - /tmp - ext2

the ext2 on /tmp was because i thought i might need a fast filesystem at some point, so i could copy anything there if i needed...

i changed my mind and set sda7 to ext3, and sda2 to reiser...

then i restored my / on sda1 from a backup using partimage

now my gnome doesnt login:

cat ~/.xsession-errors
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.XServers" -h "" -l ":0" "galileon"
/etc/gdm/Xsession: begining session setup
mkdtemp: private socket dir: permission denied


i seem to undersatand there's a permission problem somewhere - i tried to setup a different user with adduser, and logging in with that, but same problem

i've corrected the filesystems in /etc/fstab, is there anywhere else i might need to do that?

thanks a lot,

Galileon.

---

### Post by galileon on 2006-06-14
update: forget it, i nuked my / and reinstalled.....definitely not the linux way of doing things, i know!

---

