---
title: "help needed with the package manager"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by umarali on 2007-12-30
i was updating my Ubuntu and when i was installing the updates there was a power failure and the pc got turned off. Now everytime i try installing the updates from the right click menu of the small orange icon on the system tray i get this error message :
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report"
the synaptic package manager give the same error and closes down.
i tired typing "dpkg --configure -a" in the termial but it said i need superuser priviliges for that purpose...but im the admin :S
please help :(
thank you
ps: im quite new to ubuntu

---

### Post by Partyboi2 on 2007-12-30
try it with sudo in front. It will ask for you password, type it in (you will not see anything on screen)
```
sudo dpkg --configure -a
```
Sudo gives you admin rights to complete a task.
You can read more about it here:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by umarali on 2007-12-30
worked like a charm!
thank you :D

---

