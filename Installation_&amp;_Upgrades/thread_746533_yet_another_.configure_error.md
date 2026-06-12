---
title: "yet another ./configure error"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by Periswell on 2008-04-05
hi again

ive done another try at ./configure and found my self stoped with the error of:

checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!

this happens on all ./configures i try to do

please help

josh

---

### Post by StOoZ on 2008-04-05
what are you trying to install?
where did you get it from?

---

### Post by Periswell on 2008-04-05
kguitar for this exaple but it happens on all installations

---

### Post by StOoZ on 2008-04-05
ok so install these packages:
> x-dev
libx11-dev
xlibs-dev


and if you have them installed already ,try installing :
> kdebase-dev.

---

### Post by TheWizzard on 2008-04-05
> **StOoZ said:**
> ok so install these packages:


and if you have them installed already ,try installing :

just open a terminal and type:
sudo aptitude install kguitar

or select kguitar from synaptic

---

### Post by TheWizzard on 2008-04-05
> **Periswell said:**
> hi again

ive done another try at ./configure and found my self stoped with the error of:

checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!

this happens on all ./configures i try to do

please help

josh

only very rare software needs to be compiled from source. nowadays virtually everything is in the repos.

---

