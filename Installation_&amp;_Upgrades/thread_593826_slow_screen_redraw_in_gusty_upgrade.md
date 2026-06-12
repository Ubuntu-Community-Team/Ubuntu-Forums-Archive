---
title: "slow screen redraw in gusty upgrade"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by bmckeon on 2007-10-27
I installed Ubuntu Feisty for the first time last spring (so I am still relatively new), and my computer ran fine.  Last night I upgraded to gusty, and now my screen redraw is extremely slow.  Here is my graphics card info:

82915G/GV/910GL Integrated Graphics Controller (Intel)

Any thoughts on how I can get my screen redraw to be fast again like it was in Feisty?

Thanks for the help.

Brian

---

### Post by pizzy on 2007-10-27
I've got a similar card to you.  I had similar problems and this fixed it.

1.  Uninstall compiz, delete any third party repos.
2.  Uninstall XGL.
3.  Install Compiz.
XGL doesn't work well with these cards, make sure when you run compiz --replace that you get the following

compiz --replace
Checking for Xgl: not present.

---

### Post by bmckeon on 2007-10-31
Excellent!  That fixed it.

Thanks for the help.
Brian

---

