---
title: "repo's after install to fiesty"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by celticbhoy on 2007-04-19
Just upgraded to fiesty and all works well, but in software sources, can I just re-select all the third party sources with edgy at end or do I need to edit them for fiesty ???

---

### Post by bwhite82 on 2007-04-19
Yes, edit them to feisty, then do a "sudo apt-get update", check for errors upon completion of this. If you see any, note which repo gave you the error and change it back to Edgy, some repos may not have switched over yet.

---

