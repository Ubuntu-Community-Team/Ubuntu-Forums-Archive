---
title: "No keyboard or mouse function after upgrade to 8.10"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Roobert on 2008-10-25
I've just upgraded to 8.10 this afternoon. Everything proceeded fine until I logged in (automatic login, no password required) and found that the mouse and keyboard are both unresponsive. I can't tab around, or use keyboard shortcuts to access menu commands.

However, I CAN use the keyboard to Alt-F2 to a command line. How can I troubleshoot these problems with only access to command line utilities?

~ Eric.

---

### Post by steveydoteu on 2008-10-25
Distribution upgrade or a fresh install?

---

### Post by Roobert on 2008-10-25
> **steveydoteu said:**
> Distribution upgrade or a fresh install?

Fresh install using the 8.10 install CD. I would have done a distro upgrade from 8.04, but I didn't have enough room on my root partition to do the upgrade. I only had 10GB allocated, all of which as used except for about 500MB. So I had to burn the install iso to CD in order to use gparted to expand the root partition at the expense of /home. Then I proceeded to use the install option from the CD.

Not sure if this error message helps, but here's what I see as the last kernel message printed to the screen after login:

```
FATAL: Could not load /lib/modules/2.6.24-16-generic/modules.dep: No such file or directory

update-binfmts: warning: Couldn't load the binfmt_misc module.

```

---

### Post by Roobert on 2008-10-27
Well, the problem appears to be fixed; I did a fresh install of Hardy Heron again, overwriting the problematic installation of 8.10; then did a dist-upgrade as the Ubuntu home page suggests, and everything works wonderfully. Very nice! Congrats and thanks to all the devs for putting together such a slick product.

---

