---
title: "reinstalling gnome desktop"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by bennettpr on 2008-03-19
I was removing evolution from my machine (I don't use it) and it took out the entire gnome desktop!

I don't want to do a full reinstall, so I've logged in using a terminal and run synaptic.
I've added my install cd as a repository and then run:

sudo apt-get install ubuntu-desktop

but aptitude doesn't install the packages, as it looks for extra packages which require an internet connection to work, which I don't have at the moment.

Any way to get gnome reinstalled off the cd without doing a full reinstall.

Thanks in advance,
Captain Stupid

---

### Post by fedex1993 on 2008-03-19
well the best would possibly reinstall ubuntu but try sudo apt-get remove ubuntu-desktop then reinstall ubuntu desktop that might work

---

### Post by bennettpr on 2008-03-19
I've tried this but apt-get still fails as it can't get all the packages from servers, even though they should all be on the cd.....

I'd hate to do a full reinstall as I've spent a while getting stuff running (dvd, cd, mp3, beryl, apache, mysql, php...) and I'm on a dialup connection which means I'll have to d/l everything again :(

---

### Post by zvacet on 2008-03-19
@ **bennettpr**

If you use live Cd to install ubuntu-desktop that will not work,because you can do it only with alternate CD.You can go to the **synaptic>file tab>history** and see which packages you uninstalled.Try to install them with synaptic.If you didn´t run **apt-get clean** or **apt-get autoclean** packages should be in var/cache/apt/archivea and in that case you don´t need internet.

---

