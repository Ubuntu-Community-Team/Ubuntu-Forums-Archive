---
title: "Synaptic autoremove shows no packages to autoremove"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by thnld on 2010-01-12
Hi everybody!

My synaptic shows more packages in the section "manually installed" than it should. It shows packages there, which were installed *as dependencies*. Therefore, when I try to do

sudo apt-get autoremove

no packages are removed.

This error occurred in this context:
I have a gnome-desktop and tried KDE by installing "kubuntu-desktop". Then I decided not to use KDE and removed it by

sudo apt-get remove kubuntu-desktop

Then I wanted to clean up my system by doing

sudo apt-get autoremove

Nothing was removed in this step. I still have "kmail" etc. showing under "manually installed".

How can I remove all packages that were installed as dependecies to "kubuntu-desktop"?

---

### Post by Elfy on 2010-01-12
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

might be of some help

---

### Post by thnld on 2010-01-12
thanks, forestpiskie.

actually, i don't want to clean up my system manually, but want to repair the synaptic database, so that i can use "autoremove" again. i'm sure there are a lot of other unused dependencies on my system which synaptic fails to detect...

is there any switch or something for synaptic or apt-get to only show those packages under "manually installed" which i actually manually installed?


> **forestpiskie said:**
> [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

might be of some help

---

### Post by Elfy on 2010-01-12
I don't think that it will - I have in the paste been able to, fro instance install kubuntu-desktop and all that brings and then remove them all with remove kubuntu-desktop, now though remove kubuntu-desktop does just that and leaves the other packages.

---

### Post by thnld on 2010-01-12
exactly!
in my opinion, that is a bug. synaptic now just keeps every installed package forever. that is not how a package management system should work. i want to switch apt back to the old behaviour where the list "manually installed" contains no automatically installed packages.

> **forestpiskie said:**
> I don't think that it will - I have in the paste been able to, fro instance install kubuntu-desktop and all that brings and then remove them all with remove kubuntu-desktop, now though remove kubuntu-desktop does just that and leaves the other packages.

---

