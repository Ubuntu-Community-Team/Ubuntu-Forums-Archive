---
title: "get a list of pre-installed packages"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by magowiz82 on 2011-06-10
Hi,
I'm working on a script that keeps track of user explicitly installed packages (no deps, no default packages), where can I found a list of ubuntu natty preinstalled packages ? Is there some file in the filesystem or in installation disc ?

---

### Post by zvacet on 2011-06-13
I really don't know where (and if) you can find page with that list.You can do other way.if it is not too much time to invest install Natty in vbox and if you don't want any thing outside of disk don't install ubunut-restricted-exstras and stuff like that.So ,suppose you installed Natty in vbox just run

```
 aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages
```

You will find file in your home directory with a list of all installed packages.

---

### Post by magowiz82 on 2011-06-13
Yes I also thought to this solution, so I ran my vbox with fresh installed natty and get the list with dpkg -l 
Thanks for the suggestion, I think your command will display it in a better format.

---

### Post by zvacet on 2011-06-13
AFAIK  command I posted is recommended.

---

