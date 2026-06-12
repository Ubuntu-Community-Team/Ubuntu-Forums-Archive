---
title: "Programs shutting down since upgrade to 8.10"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by fenderuser on 2008-11-05
Since upgrading from 8.04 to 8.10 I am having problems with running applications suddenly vanishing (shutting down) for no apparent reason. In particular, the problem occurs with Kompozer every time I use it and occasionally with OpenOffice Presentation. 

When using Kompozer it will usually vanish/shut down with the first addition/insert of anything (eg an image). It suddenly disappears and is not running. I have checked (ps -aux) to see what processes are there, but Kompozer has gone.

A similar thing occasionally happens with Presentation, after some time it too will suddenly disappear/shut down.

I have run Kompozer through terminal, and when it 'crashes' I get an error message:

pure virtual method called

terminate called without an active exception

Aborted


Previously running with 8.04 I had no problems whatsoever, only with the upgrade to 8.10 has this occurred.

Any suggestions/ideas?

---

### Post by crjackson on 2008-11-10
As a test only you might try running kompozer from the terminal using sudo. I'm at work right now and can't test this or I would. If that works, it would seem to indicate POSSIBLY a permissions issue. If that is the case, you may be able to find the offending folder and change the permissions to fix this.

I'll check it out later this week and see if it works.

---

### Post by AndrewS on 2008-11-13
I have the same problem with Kompozer under 8.10, but it was/is fine with 8.04.  Running it as sudo from a terminal does not fix it.

AndrewS

---

