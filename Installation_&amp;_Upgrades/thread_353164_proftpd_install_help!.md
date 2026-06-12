---
title: "proftpd install help!"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by PhineasFreak on 2007-02-04
Hi Guys. I've just installed uduntu 6x server and although new to it have a reasonable understanding of how Linux works, just not to any great depth. 

I'm trying to install proftpd but whenever I type, as root:

**apt-get install proftpd**

I receive the following:

[B]Reading Package Lists ... Done
Building dependency tree
Reading state informaion... Done
E: Couldn't find package proftpd[/B]

Anyone able to help?

Many thanks.

---

### Post by el_rata on 2007-02-15
you must uncomment the universe/multiuniverse repositories in the /etc/apt/sources.list.

---

### Post by asheville on 2007-02-28
I have uncommented the lines for both the universe and multiverse repositories and apt-get still can't locate proftpd.  Do I need to force apt-get to reread source.list or something?  Any help would be appreciated.
Thanks

---

### Post by el_rata on 2007-03-20
run: ```
sudo apt-get update
``` and the run: ```
sudo apt-get install proftpd
```

or, after you uncomment the *universe* and *multiuniverse* repositories open the *synaptic package manager* and find the button that says *reload* and then search for *proftpd* ... anyway i think you may have it working now

---

