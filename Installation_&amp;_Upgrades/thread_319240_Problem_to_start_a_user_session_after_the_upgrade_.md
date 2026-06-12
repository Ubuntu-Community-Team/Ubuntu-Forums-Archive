---
title: "Problem to start a user session after the upgrade from breezy to dapper"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by ivromero on 2006-12-15
Hi!
I upgrade from brezzy to dapper, but I can't start a user session. The message that appear is: "Your session had lasted less than 10 seconds. If you have'nt finished the session is possible that this mean that there are any mistake in the installation or that there is no sufficient space in disk. Try with some of the fail session to see if possible to fix this problem" 

The details of the file ~/.xsession-errors are:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm//PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.XServers" -h "" -l ":0" "duncan"
/etc/gdm/XSession: Beginning session setup
mkdtemp: private socket dir: No space left on device  

I try to enter to Gnome fail session but the session does'nt start. I don't know what can I do.

The steps that I had do to upgrade from breezy to dapper were:
1.   I update the sources.list with dapper repositoy adresses.
2.   apt-cdrom add
3.   apt-get update
4.   apt-get dist-upgrade

Thanks a lot if any person can help me.

---

