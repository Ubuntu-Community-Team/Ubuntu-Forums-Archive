---
title: "Hardy Heron - Need to restart NIS and autofs"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by davidkahn on 2008-05-05
Upgraded from Gutsy to Hardy last week.  Rebooted my computer today after installing a bunch of upgrades through the Upgrade Manager.

Automounting started failing to mount my home directory.  So I tried restarting autofs (automount) and saw that was failing because it couldn't get the mount points from NIS, where they are stored.

"ypcat -k auto.home" gave a message that it could not locate my NIS domain.  So I restarted nis on the master server, then restarted nis on my computer, which is a secondary nis server, and ypcat started working again.  This allowed autofs to start  and everything works fine.

Since I don't want to have to restart services manually every time the computers are rebooted, it would be great to solve this.  Is it a Hardy Heron bug?

Thanks.

David

---

### Post by davidkahn on 2008-05-06
I noticed that I am not the only person to have a problem with NIS [http://www.experts-exchange.com/OS/Linux/Setup/Q_23362347.html](http://www.experts-exchange.com/OS/Linux/Setup/Q_23362347.html)

One other NIS issue from /var/log/syslog is a bunch of errors of the form:
[INDENT]May  6 15:47:13 CERTIBY-DEV1 ypserv[11573]: refused connect from 10.10.10.84:36511 to procedure ypproc_match (LAHILLS.CERTIBY.COM,shadow.byname;-1) 
[/INDENT]It's quite odd since 10.10.10.84: is the IP address of CERTIBY-DEV1, which means that the NIS server is refusing connects from the NIS client on the same machine.

---

### Post by davidkahn on 2008-05-06
It also looks like the autofs (automount) problems are being seen by others:
[INDENT] [http://ubuntuforums.org/showthread.php?t=773697](http://ubuntuforums.org/showthread.php?t=773697)
[/INDENT]Hardy Heron needs a few bug fixes. :(

---

### Post by Cyanoacrylate on 2008-05-23
I am also experiencing this issue (and have also experienced it in Feisty).

My sense is that there is something that is out of order in the startup dependencies - I am strongly suspicious that DHCP is not finishing getting the interface set up before NIS tries to come up.

On a hunch, I tried moving the dhcdbd startup process from S24 to S15, and the portmapper from S18 to S17, but still have had no luck getting this to work.

My present workaround is to put the lines:

/etc/init.d/nis restart
/etc/init.d/autofs restart

in my rc.local.  But that is a horrible kludge. :mad:

Anyone who understands the ubuntu DHCP boot process better know how to fix this?

Thanks!

---

### Post by Cyanoacrylate on 2008-05-23
Bah.  My workaround in rc.local doesn't work either.

:mad:

I've run out of time to try to fix this today.  Will open a bug report...

---

