---
title: "Install acutex without any dependencies or remove it from the update list"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by 5au1 on 2011-10-26
Hello,

I installed Texlive 2010 from a CD together with Auctex and Reftex (both compiled from source). Now the update manager tells me that there is an update available for Auctex, however when marked for installation it tries to install the whole texlive system.

I tried the command
```
sudo apt-get install --no-install-recommends auctex
```
but there are two packages that still get selected (preview-latex-style tex-common).

Is there a way to mark Auctex as a "local or absolete" in Synaptic? or install it without **any** dependencies?

Thanks in advance,

Saul

---

### Post by Toz on 2011-10-26
Try creating the file **/etc/apt/preferences.d/no_auctex** with the following content:
```

Package: auctex
 Pin: version *
 Pin-Priority: -100
```
This should pin auctex to its current version and remove it from apt updates.

---

### Post by 5au1 on 2011-10-27
Thanks for the reply,

Created the file, reloaded synaptic, but auctex remains in the update list

---

### Post by 5au1 on 2011-10-27
The solution was simpler than I thought :P. Just added:
```
> sudo aptitude install auctex=
```
The = option indicates aptitude to keep the current version (see man aptitude).
By the way this doesn't remove the package from the synaptic's list, however to do that you just have to select Package > Block version

Cheers

---

