---
title: "No gnome apps running after upgrade to heron"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by kreyszigrocks on 2008-07-06
Hi,

I've also posted recently about gdm hanging after upgrading to heron. i've also found that when using another display manager, such as kde or fluxbox, i can't run any gnome apps at all. when i say gnome apps, i mean just about anything that doesnt start with a K- firefox, gnome-terminal being two examples. Konqueror runs as does Konsole.
any ideas where i can look to try and figure out what is going on? I tail -f syslog as i launch these apps but don't see anything
Do I perhaps need to reinstall gtk?
your help very much appreciated

---

### Post by PmDematagoda on 2008-07-06
Can you post the output of running:-
```
firefox
```
in Konsole?

---

### Post by kreyszigrocks on 2008-07-06
i was just about to update my post with that very information. every gtk app i run tells me
symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_dpgettext

---

### Post by kreyszigrocks on 2008-07-06
I had my own copy of glib installed in /usr/local/lib. removing this seems to have solved the problem.

---

### Post by PmDematagoda on 2008-07-06
> **kreyszigrocks said:**
> I had my own copy of glib installed in /usr/local/lib. removing this seems to have solved the problem.

That might have very well been the problem since Update Manager usually gets rid of any "alien" packages before it commences with the upgrade.

---

