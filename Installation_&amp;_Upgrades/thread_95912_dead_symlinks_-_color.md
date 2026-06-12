---
title: "dead symlinks - color?"
date: 2005-11-27
forum: Installation &amp; Upgrades
---

### Post by chris_pmf on 2005-11-27
Hi,

how can I choose a color for dead symlinks in my bash / konsole?

Thanks :)

---

### Post by PypeBros on 2008-01-14
This is achieved through setting up the LS_COLORS environment variable (thus dependent on ls rather than a specific shell/terminal). the code for dead links ("orphan") is or=<ansi color>, but it seems like the "dircolors" program can help you customizing your .bashrc :

ORPHAN 40;31;01 # symlink to nonexistent file
would e.g. make it red-on-black.

HTH.

---

### Post by chris_pmf on 2008-01-14
Thanks, I solved it some time ago.

---

