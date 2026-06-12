---
title: "Can't log in as user"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by sdb2028 on 2006-03-09
Here is the exact read from the .xsession-errors file
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "steve"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied
This happened right after I ran:
> 
sudo tar xvzf control.tar.gz and
sudo tar xvzf data.tar.gz
which are the 2 files extracted from the
> libdvdcss2_1.2.9-1_i386.deb file

---

### Post by sdb2028 on 2006-03-09
OK, got it--- had to change the permissions in tmp folder. I'm back to user now.

---

