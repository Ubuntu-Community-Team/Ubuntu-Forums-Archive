---
title: "Fails to upgrade from 10.10 to 11.04"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by Accidus on 2011-08-30
I wish to upgrade from 11.04 to 10.10. Below are the attached log files (the term.log file is empty).

Some more information:
I probably really garbled package dependencies by accidentally adding an oneiric PPA and upgrading packages from it. 

Right now synaptic doesn't complain on any broken packages though, after removing some broken packages (like emacs23 and texlive-base).

I can supply more information/diagnosis if needed.

---

### Post by dino99 on 2011-08-30
first be sure to only use Natty genuine ubuntu repo, deactivate third parties repo from /etc/sources.list, then update

---

### Post by Accidus on 2011-08-30
They were disabled. I've removed the multiverse ones as well, but upgrading still fails.

---

