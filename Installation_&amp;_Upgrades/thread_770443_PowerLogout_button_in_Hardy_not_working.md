---
title: "Power/Logout button in Hardy not working"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by raindog21 on 2008-04-27
Hi,

After upgrading to hardy the gnome "power button" is broken.  When i click it gnome freezes up and I don't get the logout/restart/shutdown menu.

Strange enough, it works fine while on a remote X session using nomachine NX.  It's broken only for local X sessions.  

The behavior is the same whether or not I'm using compiz or metacity.

Any suggestions on logs to capture are much appreciated.  For now the only way I have to logout is cntrl-alt-backspace

---

### Post by pixatintes on 2008-04-27
I have the same problem.. :confused:
but I didn't try remote conection..

---

### Post by pixatintes on 2008-04-29
Solved for me. 

Go to System> Preferences> Sessions and in the Startup Programs tab enable gnome-power-manager.

Good Luck,

---

