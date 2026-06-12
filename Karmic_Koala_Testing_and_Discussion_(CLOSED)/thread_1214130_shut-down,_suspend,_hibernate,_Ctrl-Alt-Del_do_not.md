---
title: "shut-down, suspend, hibernate, Ctrl-Alt-Del do not work"
date: 2009-07-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zika on 2009-07-15
If I try to Shut-down, Suspend, Hibernate, Reboot all I get is restart of X. Ctrl-Alt-Del that worked before does only abrupt and unclean restart of X ... Similar is with the System->ShutDown ... I have to reboot or shutdown from tty (Ctrl-Alt-Fx) ... 
I can not log-in as usual on the gnome greeting screen since my pass is rejected ... I have to use AutoLogin option. My pass is OK either in tty or in GDM once I get into it ...
Any ideas ...?

---

### Post by Xamiga on 2009-07-15
<sudo shutdown> worked for me when this happened.  Updating last night fixed it.

---

### Post by zika on 2009-07-16
> **Xamiga said:**
> <sudo shutdown> worked for me when this happened.  Updating last night fixed it.Yes, that is what I meant by "I have to reboot or shutdown from tty" ... I'll see what upgrades carry for me this morning ...
...No, everything is the same ...
Well, not everything. I've remembered how choosing transparent background in panels disabled Alt-{F1,F2} so I reverted back to Human theme and viola, I have now Suspend and Hibernate but ReStart and ShutDown are greyed ... I still can not log-in on GDM Greeter window but have to use AutoLogin ... That is the only place where my pass is not accepted ... :)

---

### Post by jppr on 2009-07-16
Quit, log out and then shut down

---

### Post by zika on 2009-07-16
> **jppr said:**
> Quit, log out and then shut downI've tried that but it is a problem to LogOut when that just bounces back to desktop ... A bit of juggling with /etc/gdm/custom.conf solved that ...
The problem with LogIn is solved now: somehow it changed keyboard layout .. I have to change it every time I try to LogIn ... It is an improvement... I just have to find out the way to change that LogIn keyboard layout. (I have Serbia(Latin) and Serbia(Cyrillic) ...)

---

### Post by chrisccoulson on 2009-07-16
The problems with shutting down from System -> Shutdown are [https://bugs.edge.launchpad.net/ubuntu/+source/gnome-session/+bug/399531]("https://bugs.edge.launchpad.net/ubuntu/+source/gnome-session/+bug/399531").

That will be fixed now if you upgrade.

---

### Post by zika on 2009-07-16
> **chrisccoulson said:**
> The problems with shutting down from System -> Shutdown are [https://bugs.edge.launchpad.net/ubuntu/+source/gnome-session/+bug/399531](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-session/+bug/399531).
That will be fixed now if you upgrade.Thank You, I'll see what upgrade is carrying now ... I'm still in search of place where to change keyboard layout for that LogIn screen ... Globally, keyboard layout is set OK, just there it is the one that is "wrong" and that is used occasionally ... I know, I might remove it and add it just when it is needed but that proved to be always in the worst of all times ...

---

