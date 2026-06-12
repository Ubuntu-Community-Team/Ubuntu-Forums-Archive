---
title: "[SOLVED] ubuntu updater wont download."
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by neba on 2008-09-12
hello. my computer shows that i have up dates ready to be installed, but when i start to install them this messages pops up

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

then the installation is canceled. what is wrong. how can i fix it. i restarted my computer, and that didnt work. 
thanks

---

### Post by pwicken on 2008-09-12
Open a terminal

Enter ```
sudo dpkg --configure -a
```
Press Enter
When promted enter your password.

At least that is what the error message is trying to tell you.

---

### Post by Neo_The_User on 2008-09-12
I recommend doing whatever the error tells you to do unless you know what you are doing.

---

### Post by neba on 2008-09-13
thank you. i tried 'sudo dpkg --configure -a' yesterday and it didnt work. so today i was able to restart my computer and now it works. your awesome, thanks again.

---

