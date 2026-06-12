---
title: "Ubuntu runs sooooo slow"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by laquain on 2007-06-30
I'm new to the Ubuntu world and after my first installation of feisty fawn, it took about 30 minutes for the login screen to appear and after logging in i can not get to the desktop (I've been waiting for another thirty minute!)

I'm running an intel P4 2.8Ghz with 1 gig of ram.

Can someone please help me because I really don't want to go back to windows. Thanks in advance

---

### Post by PgR on 2007-06-30
Can you get in through a terminal?

Ctrl-Alt-F1 should bring up a text based login, and sudo /var/log/syslog -f will show what's going on.

That should point you in the right direction.

---

