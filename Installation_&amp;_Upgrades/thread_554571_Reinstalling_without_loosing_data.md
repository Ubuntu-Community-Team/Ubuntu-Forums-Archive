---
title: "Reinstalling without loosing data"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by jobbesat on 2007-09-19
Since i messed everything in compiz, I lost compiz itself, I lost desktop effects and I can't reinstall compiz and desktop effects, is there a way to restart from cd and reinstall only these packages? Or any other good way?
I'd like to do do this because everything else is working fine on my system
Thanks a lot in advance

---

### Post by kellemes on 2007-09-19
What's going wrong with setting up compiz?

---

### Post by jobbesat on 2007-09-19
I installed compiz via apt-get. 2 problems when you can: 1st i don't know how to reinstall "Desktop effect" (infact there's no link under System->Preferences), 2nd if I launch System->Preferences->Compix settings manager I receive tthe following error:
Dbus failed to load. Compiz is not running. The dbus plugin cannot be activated unless compiz is running.

So I did on terminal
compiz
and I got the following:
```
/usr/bin/compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
/usr/bin/compiz.real: No manageable screens found on display :0.0
Avviso del window manager: Il valore «» nel database di configurazione non è valido per la scorciatoia «toggle_shaded»
Avviso del window manager: Il valore «» nel database di configurazione non è valido per la scorciatoia «move_to_workspace_left»
Avviso del window manager: Il valore «» nel database di configurazione non è valido per la scorciatoia «move_to_workspace_right»
Avviso del window manager: Il valore «» nel database di configurazione non è valido per la scorciatoia «move_to_workspace_up»
Avviso del window manager: Il valore «» nel database di configurazione non è valido per la scorciatoia «move_to_workspace_down»
Avviso del window manager: Il valore «» nel database di configurazione non è valido per la scorciatoia «switch_to_workspace_left»
Avviso del window manager: Il valore «» nel database di configurazione non è valido per la scorciatoia «switch_to_workspace_right»
Avviso del window manager: Il valore «» nel database di configurazione non è valido per la scorciatoia «switch_to_workspace_up»
Avviso del window manager: Il valore «» nel database di configurazione non è valido per la scorciatoia «switch_to_workspace_down»
Avviso del window manager: Lo schermo 0 nel display «:0.0» ha già un window manager; utilizzare l'opzione --replace per sostituirlo.
```

Each line, translated from italian, means: Window manager warning: the value «» in configuration database is not valid for the shortcut to xxxxxx»
So I tried with compix --replace but on Compix Settings Manager I still have the dbus error

Any help on both problems, please?
thanks a lot

---

