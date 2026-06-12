---
title: "App interface post 15.10 upgrade"
date: 2015-11-02
forum: Installation &amp; Upgrades
---

### Post by lynwode on 2015-11-02
Hey Folks.
I'm sure this is a quick config issue but I'm tired and brain is in neutral !

Post a 15.10 upgrade a number of apps look like they have stepped back in time to the early 90's !

Eclipse, MySQL Workbench, Skype, UltraEdit to name a few look awful. I assume (probably wrongly) that this is due to GTK changes in Wily.

I vaguely remember this happening before but as I said my brain is in neutral tonight. Is there any tweak I need to make?

Hope this makes sense !

Cheers,
Tim.

---

### Post by Vladlenin5000 on 2015-11-02
Were you using some theme prior to upgrading?

---

### Post by grahammechanical on 2015-11-02
The tweak is called "re-install the apps."  The Synaptic Package Manager gives an option to re-install apps. If there are newer versions in the 15.10 repositories then you will get the newer versions.

---

### Post by lynwode on 2015-11-03
@Vladlenin5000  - the same theme
@grahammechanical  - no dice - still the same

Any ideas?

---

### Post by Bucky Ball on 2015-11-03
Try these commands, one after the other with return in between, then reboot:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Post any and all errors that these commands spit out.

---

### Post by lynwode on 2015-11-03
Well looks like Xinerama was the culprit.
I disabled that and everything looks fine now (also solved a issue with Nautilus crashing when dragging files). The only downside is that I know only have two monitors.....

Time for a new thread.....

---

