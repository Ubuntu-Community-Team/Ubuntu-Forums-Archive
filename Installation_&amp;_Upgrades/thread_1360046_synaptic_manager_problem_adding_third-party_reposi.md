---
title: "synaptic manager problem :adding third-party repositories"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by anthonyleamy on 2009-12-20
I have been personalizing the ubuntu mini install on my netbook and am trying to add the crunchbang repository.
However, after adding the relevant http:// address in the APT line box, the +add source button remains greyed out and inactive; thus I cannot save the new source.

Tips for GUI or command line would be appreciated.

---

### Post by oldos2er on 2009-12-20
Lines in sources.list must begin with either deb or deb-src.

---

### Post by anthonyleamy on 2009-12-20
Thanks. 
I just discovered that fact using the sudo cat /etc/apt/sources.list command

The'deb' doesn't appear in synaptic api line, hence the greyed out box.

Thank you for your help.

---

