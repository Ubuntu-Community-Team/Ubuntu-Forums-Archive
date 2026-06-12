---
title: "[SOLVED] Tasksel has only two packages"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by kromm on 2007-11-18
After having selected the lamp-server in tasksel en by mistake de-selecting the Ubuntu desktop I ruined the installation, Therefore I reinstalled 7.10. Now when I execute tasksel, there are only two packages listed... Ubuntu Desktop and Print Server.. Does anybody know how I can get the other default pre-packaged tasks listed?

---

### Post by kromm on 2007-11-19
Apparantly the basic install of 7.10 does not have more than these two packages available. You will get more packages listed by doing updates through the Synaptic Package Manager. Somehow none of the repositories were selected, so everytime I reloaded to look for upgrades nothing was found.

If you encounter the same problem, do the following:
Go to Desktop Menu --> System / Administration / Synaptic Package Manager
Synaptic Menu --> Settings / Repositories
tab 'Ubuntu Software' --> Select all
tab 'Third-Party Software' --> Select all
tab 'Updates' --> Select 'Important Security' and 'Recommended' updates
Close settings

Press 'Reload' button
Press 'Mark All Upgrades'
Press 'Apply'

Sit back and relax. It will take some time to download and install all updates and upgrades.

Have fun.. :)

---

