---
title: "gksu taking too long to validade password after upgrading from Xubuntu 7.04 to 7.10"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by danielrech on 2008-03-10
In Xubuntu 7.04, gksu would validate my pass in less than 5 secs. Now that I've upgraded to 7.10, it is taking about 30-40 secs. 

Is there any way for me to fix/configure it?

Thanks in advance.

---

### Post by Rmantingh on 2008-03-15
You probably have 'compositor' on in 'Window Manager Tweaks'.
This causes problems when gksu tries to grab the desktop (screen goes darker
when it asks for the password). I don't know why this is a problem but
there are 2 workarounds:-
1) Disable compositor
2) Set an alias for the gksu command in your local .bashrc file:
    alias gksu='gksu -g'
I'm using the second option as I don't understand why gksu has to lock the
desktop anyway (very annoying) and now the screen does not go dark
anymore and acceptance of the password is very quick again.

---

