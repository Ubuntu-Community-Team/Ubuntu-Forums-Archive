---
title: "Keyring bug?"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kernco on 2010-03-09
Does anyone else have this issue?

I have automatic login setup, but the keyring needs to ask for my password each time so it can access my wireless WPA key.  Here's what happens currently in 10.04

[LIST=1]
[*]Computer boots
[*]Gnome desktop loads
[*]Keyring password box appears
[*]I type in my password and hit enter
[*]Suddenly, I'm on the gdm login screen.
[*]I choose my username and type in my password to log in
[*]The Gnome desktop loads again (keyring doesn't ask me for my password this time)
[/LIST]

Obviously, steps 5, 6, and 7 should not happen.

edit: Clarification for step 7.  The Gnome desktop really does load again with a new session, it doesn't just reappear with the session that loaded in step 2.

---

### Post by anders_c_ on 2010-03-09
Check this thread:
[http://ubuntuforums.org/showthread.php?t=1418022&highlight=keyring](http://ubuntuforums.org/showthread.php?t=1418022&highlight=keyring)

---

