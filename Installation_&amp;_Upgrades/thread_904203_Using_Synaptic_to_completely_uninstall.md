---
title: "Using Synaptic to completely uninstall"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by JustAnotherVagueAnon on 2008-08-29
Hello, I want to completely remove old apps that I had used Add/Remove GUI to remove previously. I'm wondering if there's a way in Synaptic to view all uninstalled apps that have been removed but not "completely" removed including config files. I'm the only user on this comp and have no need for these remnants.

EDIT: I would also like to remove all dependents that weren't completely removed

---

### Post by SunnyRabbiera on 2008-08-29
actually if you are willing to use the terminal try these commands:
sudo apt-get autoclean
sudo apt-get autoremove

---

### Post by Flag on 2008-08-29
Or in synaptic serach for orphan, you'll get two or three hits. Install gtkorphan it will appear in system->admininstration afterwards. In synaptic itself you have the option to check on residual files and check them - delete them.

---

