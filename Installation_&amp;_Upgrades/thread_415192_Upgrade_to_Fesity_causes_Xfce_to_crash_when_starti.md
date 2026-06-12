---
title: "Upgrade to Fesity causes Xfce to crash when starting"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by rrwo on 2007-04-20
I upgraded to Feisty, but now most of the time when I log in, Xfce gets caught up in the Starting Desktop Manager stage. The only way to get out is to Ctrl-Alt-Backspace to restart X and log in to Gnome.

I'd like to get Xfce working. Hpow do I fix this?

---

### Post by rrwo on 2007-04-20
I should add that I sometimes can log in to Xfce.

Also, I use the XFapplet to run the Gnome System Monitor in the Xfce panel.  The CPU monior showed nearly 100% usage of the Xfapplet when I did first log in.  I killed the applet and re-added it to the panel, and it's running fine.  I don't know if that's related or not.

---

### Post by dotnick on 2007-04-20
I also have this problem, however it sounds like you get further.  My XFCE install will not load the first app and has a segfault error shortly after I try to launch the session.  Which means I'm back at gnome or kde (depends on my mood).

---

### Post by rrwo on 2007-04-21
I actually had Xfce 4.4.1 installed from [www.xfce.org](www.xfce.org) in /usr/local (which is where I thought Dapper and Etch installed it).  Feisty installed it's version in /usr, so there was possibly a conflict. I'm in the process of removing both versions and reinstalling it.

---

### Post by rrwo on 2007-04-21
I wiped all traces of Xfce from my system and installed the version that comes with Feisty. 

I still have the same problem.

---

### Post by rrwo on 2007-05-03
I installed Feisty from scratch, and so far no problems.

---

### Post by dotnick on 2007-05-03
It's odd that an upgrade is broken when a clean install works fine when they use the same repositories.  Mine is still broken, but I'm not wanting to do a clean install.  I think I'll just wait it out until someone else figures out what is going on and releases a patch or the XFCE packages get updated (and things magically work again :) )

---

### Post by rrwo on 2007-05-04
It's likely that there's somthing on the system that conflicts. Maybe one library  in /usr, another in /usr/local, so it's using inconsistent versions. Compare files in the bin, lib, and libexec directories of /usr and /usr/local to see if there are duplicates.

Anyhow, a clean install fixed Xfce, but there are still problems with Feisty...

---

