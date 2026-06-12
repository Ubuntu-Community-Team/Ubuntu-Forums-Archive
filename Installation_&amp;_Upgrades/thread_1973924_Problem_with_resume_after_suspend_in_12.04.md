---
title: "Problem with resume after suspend in 12.04"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by btedm on 2012-05-05
I recently installed 12.04.  When the PC is left for a time it goes into suspend mode.  When I try to restart I enter my password and select "Unlock".  It then starts "checking" and this process never ends.  I have found that I can bring back the menu with "escape".  If I choose "Switch User" instead of "Unlock", it brings up the login screen and I can start.  In previous versions I did not have this circus -- I just moved the mouse or hit a key and it resumed without requiring any password.  In both cases, I have automatic login and there is only one user.  What can I try?

---

### Post by btedm on 2012-05-05
I just found the setting under System Settings -- Brightness and Lock.  It was set to require my password when waking from suspend.  Apparently it was set in this install and not in previous ones.  I removed the check and it resumes without asking for a password.

---

