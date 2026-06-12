---
title: "Installing gutsy packages from dvd on hardy installation?"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by ninotsmindelivar on 2008-07-26
Hi there, I'm trying to install hardy on a series of school computers in a developing country (internet to speak of for heavy downloads). Hardy is needed as its kernel seems to resolve a bug with the school computers' burners, keeping them from writing discs on gutsy and gutsy alone.

However, I have the full dvd version of kubuntu 7.10, from which I need to install krita, its dependencies, and russian language support in the menus and their dependencies, as well as restricted codec support (I have an aptoncd disc with those, for 7.10). 

Basically, I'd like to install these older versions of the software from gutsy on a hardy install.

If I disable the internet repos for hardy, and only enable my aptoncd and gutsy dvd in the sourcelist, will these older versions install without hardy complaining at us?

Thanks a ton in advance!

---

### Post by kuja on 2008-07-28
Well, that depends, if these packages are already installed, including their dependencies, it won't complain, otherwise it might complain at you, in which case you'd have to figure out what to remove, remove it, and then proceed with the install of the older packages. Downgrading of things might also be possible, but it is a bit difficult to do.

---

