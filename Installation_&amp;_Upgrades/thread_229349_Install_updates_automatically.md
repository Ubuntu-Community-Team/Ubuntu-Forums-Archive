---
title: "Install updates automatically"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by maol62 on 2006-08-04
Almost every morning when I come to my computer there are updates to install since last evening. And everytime I install them by pressing the update icon, then writing the administrator password, and last accepting all uppdates by pressing install.
So my question is: Is there a way of doing this automatically? Some "accept all updates without questioning" function?

---

### Post by stoft on 2006-08-04
> **maol62 said:**
> Almost every morning when I come to my computer there are updates to install since last evening. And everytime I install them by pressing the update icon, then writing the administrator password, and last accepting all uppdates by pressing install.
So my question is: Is there a way of doing this automatically? Some "accept all updates without questioning" function?

Yes. Read up on crontab and apt-get. Using crontab and a script you can call apt-get automagically on a regular basis. There should be a flag for apt-get to run with out questions (even at different levels of questions). The risk should be smaller in Ubuntu compared to less stable distributions, but just autoinstalling everything could lead to breaking dependencies that you won't discover until it's too late.

---

