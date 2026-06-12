---
title: "Add/Remove Error Message"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by pilotguy777 on 2008-01-03
Upon clicking the check box next to any program in the Add/Remove Program list, I receive a dialog box that says "The list of applications is not available".  It gives the option to "reload", but does not solve the problem.  This happens with all programs.  Any ideas?

---

### Post by taurus on 2008-01-03
You need to enable more repos in your /etc/apt/sources.list before you can install more stuff.  Close Add/Remove and the click

System -> Administration -> Synaptic Package Manager -> Settings -> Repositories

and put a check mark in front of all the lines _except_ the last one, Source code and the CDROM at the bottom window.  Then, Close it and hit Refresh.  Now, you can close down synaptic and try to install whatever you planned to install earlier with Add/Remove.

---

