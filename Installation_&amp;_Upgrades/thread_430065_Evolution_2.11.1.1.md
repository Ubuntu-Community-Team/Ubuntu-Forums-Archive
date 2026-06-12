---
title: "Evolution 2.11.1.1"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by rbmorse on 2007-05-01
There is a new version of Evolution (2.11.1.1) in the wild that promises to address some of the problems with the current version (2.10.X).  I downloaded the tarball and tried to install Evolution from source....the package configured successfully (after a long but very straightforward dependency chase), but would not build, citing numerous syntax errors before failing completely. 

I notice this morning that 2.11.1.1 is in the Gutsy repositories (and in fact installs quite nicely on the Gutsy VM I'm testing). 

I tried to bring the .deb files in the Gutsy Apt cache over to my Feisty installation, but of course they won't install because of about 30 other dependencies. 

This is probably well into stupid territory, but rather than chase down every stinkin file and library Evolution 2.11 wants, is it a bad thing to temporarily change my Feisty sources over to the Gutsy repositories, update, install the new version of Evolution, then restore the fiesty sources and continue with life? Or, is this asking too much from the package management system?

TIA

Ron Morse

---

