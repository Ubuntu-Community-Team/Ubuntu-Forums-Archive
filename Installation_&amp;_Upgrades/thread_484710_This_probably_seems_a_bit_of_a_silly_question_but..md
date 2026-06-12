---
title: "This probably seems a bit of a silly question but...."
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by netsurfau on 2007-06-26
How do I access applications I've installed with the "Synaptic Package Manager"?

I've tried to find the few I have, but with no luck.  I thought they would've appeared in the Applications
menu, but they're not the.

Could someone point me in the right direction to find these apps?

---

### Post by coxc24 on 2007-06-26
I don't run Gnome but in KDE (Kubuntu) the applications that are installed via the package manager are placed on the K-Menu under their relevant area. This could be Internet for web browsers, communications and so on. Other stuff might go under System or Utilities. It depends what you installed.

I am sure the same should happen in Gnome (Ubuntu).

---

### Post by dfreer on 2007-06-26
It does, for most programs. However, some programs don't have GUI interfaces, and others that do have GUI's just don't have an .desktop entry in /usr/share/applications (or they have a malformed one).
Another possibility if you just installed them, is that the gnome-panel hasn't refreshed itself yet. Either reboot or you can try a:
```
sudo killall gnome-panel
```

What programs in particular? You could always try typing the program name into the terminal, might be able to find it in your PATH.

---

### Post by mneisen on 2007-06-26
At least under KDE you have to logoff and login again (or kill and restart kmenu) to see the newly installed applications.

Regards
Martin

---

