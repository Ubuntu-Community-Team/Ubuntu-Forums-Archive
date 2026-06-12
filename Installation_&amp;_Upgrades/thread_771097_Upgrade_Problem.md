---
title: "Upgrade Problem"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Shadius on 2008-04-27
Tried to upgrade to 8.04 (Hardy) but it says that "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." It says that in the terminal window after I type "sudo apt-get install - f" because it told me to do this. Keep in mind that I'm new to Linux, so I don't know much. My question is how do I manually run "dpkg"?

---

### Post by ayampanggang on 2008-04-27
to manually install packages *.deb you do sudo dpkg -i <package_name.deb>
i suggest you look at the manual since i never use dpkg that much

---

### Post by Shadius on 2008-04-27
I was trying to upgrade to Hardy from the Update Manager but now it's telling me I have to use the Terminal. So I'm at a loss.

---

### Post by pnti on 2008-04-27
Just follow advice of your Ubuntu:

$sudo dpkg --configure -a

.

---

### Post by Shadius on 2008-04-27
Okay, it seems to be finished but it says the following:

Errors were encountered while processing:
 libpango1.0-dev
 compiz-core
 compiz-gnome
 compiz-plugins

So what do I do now?

---

