---
title: "Upgrade to 9.10 login problem"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by Big_Croc7 on 2010-03-06
I've just upgraded to 9.10 (from 9.04, using the Kubuntu tool) and it's messed up my system!  I can't login; when I login from the kdm greeter I get thrown back to the greeter screen after a few seconds - usually, but not always, before the desktop appears (i.e. while the kde login splash screen is showing). I've tried creating a new user - same problem. Logging in in failsafe mode gives the same problem, except it returns to the greeter screen faster, within a second. I can log in in text mode on a tty; this is fine, but then if I run startx, it gets just as far, except the system hangs instead of returning to the greeter (I think it's an x problem - the screen locks up, but the alt+sysreq keys still work).
.xsession_errors says something like 'x_terminal_emulater: Fatal IO error: client killed' after trying failsafe mode, and a similar message but with kdeinit4 instead for the normal mode.
Any help would be much needed! (Oh, and also - I don't have a network connection from kubuntu anymore, since it's wireless only, and I can't make it connect wirelessly from the console - that might just be me though).

---

### Post by Big_Croc7 on 2010-03-07
The problem is related to the new kernel - 17 works fine it seems, but 30 doesn't.

---

