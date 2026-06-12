---
title: "bittorrent broken"
date: 2008-06-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by LittleKoy on 2008-06-20
(Reading database ... 274597 files and directories currently installed.)
Removing bittorrent ...
xargs: xargs.c:443: main: Assertion `bc_ctl.arg_max <= (131072-2048)' failed.
Aborted
dpkg: error processing bittorrent (--purge):
 subprocess pre-removal script returned error exit status 134
Errors were encountered while processing:
 bittorrent
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)


This is what I get, when trying to remove bittorrent. I also get this when I try to do any other install/remove/upgrade operation, so I'm stuck...

PS: I'm upgrading the system little by little, is it ok or should I do a mass upgrade?

---

### Post by LittleKoy on 2008-06-20
Oh sorry, I just solved by upgrading findutils. Actually libc6 log stated that findutils had been added as a dependence, but wasn't true for me.

---

