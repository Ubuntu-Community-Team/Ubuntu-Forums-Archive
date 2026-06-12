---
title: "Installing KDE on UBUNTU?"
date: 2005-07-07
forum: Installation &amp; Upgrades
---

### Post by mhbengal on 2005-07-07
I installed Ubuntu on my laptop but needed KDE hence I used the FAQ steps to do the following:

"sudo apt-get remove ubuntu-desktop" (This works and is removed)
"sudo apt-get remove kubuntu-desktop" using the UNIVERSE repos, but an error message turns up saying no such package found.

How do I now install KDE (Convert to Kubuntu) on this existing Ubuntu Hoary installation. Is there a way at the tiem of installating Ubuntu to get KDE installed.

Mustapha

---

### Post by mhbengal on 2005-07-07
Correction to the Above:

"sudo apt-get remove ubuntu-desktop" (This works and is removed)

"sudo apt-get install kubuntu-desktop" using the UNIVERSE repos, but an error message turns up saying no such package found.

Mustapha

---

### Post by t2kburl on 2005-07-07
I think kubuntu desktop package is only on the CD  ... which I used to install my system, and after I read this I found that that particular package was not installed on my system.

Try just using apt-get install kde or use synaptic to choose the specific kde packages you want. Just be sure to include kdebase, kdm and kdelibs.  (I doubt you'll be able to miss them since I'm sure most KDE packages depend on them.)

you may want to add this line to your /etc/apt/sources.list

deb [http://kubuntu.org/hoary-kde341/](http://kubuntu.org/hoary-kde341/) hoary-updates main

so you can get KDE 3.4.1 update right away

once the download completes in synaptic it will ask you to choose your default display manager, simply choose kdm and you are set. (I did this when I installed with a Ubuntu CD on another system)

---

### Post by aragorn2909 on 2005-07-07
the kubuntu-desktop package is not required to run kubuntu.  t2kburl is right, all you should need to get going  is sudo apt-get install kde.

---

