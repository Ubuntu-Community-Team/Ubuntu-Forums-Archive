---
title: "safer apt-get??"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by orrorin on 2007-05-12
The last time I installed Feisty on my x86, towards the end when it was updating some packages, apt-get ran into some problems (most probably a network bandwidth issue, since we were also watching some video streams on our other PC). It happened while updating the gnome-panel package and subsequently, the packages got and stayed broken. i.e. every time I tried to install any package apt-get/aptitude/synaptics would complain that gnome-panel needed to be installed but some files are missing. It would then bail out and there was seemingly no way to recover other than a fresh install.

So, is there a safer version of apt-get that can download complete package(s), do some sanity checks and only then try to install, in the right order of the dependencies? Or are there any commands to "repair" broken package database?

I'm new to Ubuntu and have some minimal experience with FC6.

---

### Post by evolutionx on 2007-05-12
Hi,

You might like to try the following command in terminal.

sudo dselect

When the menu comes up select Update and afterwards select Install.

This should update the apt sources and then install any packages not previously installed from last time.

Hope this helps.

---

### Post by orrorin on 2007-05-13
thanks evolutionx; i'll check it out...

---

