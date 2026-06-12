---
title: "I updated Intrepid with Hardy sources - How to correct?"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by sofasurfer on 2008-11-01
I ran update/upgrade using my old Hardy sources.list. Now that I caught my mistake, and am ready to edit my sources.list to install Intrepid updates, what is the proceedure to first remove Hardy updates/upgrades? Or is there anything special I need to do?

---

### Post by lemming465 on 2008-11-02
You can either run "sudo update-manager -d" from a command line, or go into System -> Administration -> Sources ... and allow non-LTS upgrades.  Then the GUI update manager should offer Intrepid Ibex 8.10 as an option.  Either method will rewrite /etc/apt/sources.list for you automatically.

---

