---
title: "Flash install problem"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by Trower on 2009-12-09
The newest flash .deb wont install for me I get "error: Dependency not satisfiable: libpango1.0-0"

I dont have Gnash installed and sudo apt-get install flashplugin-nonfree wont work ither, says the adress for the file is not found. 

I have 8.04 HH

-Thanks for any help

---

### Post by fancypiper on 2009-12-09
Have you added the medibuntu sources?  If not, follow directions in the link below, then try sudo apt-get install flashplugin-nonfree

[Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by mikewhatever on 2009-12-09
Hmm, I really don't think flash is in Medibuntu. It's in multiverse, and the package version is ... something rather obscure. libpango1.0-0 is also a dependency for flash in Jaunty, so not sure what's wrong.

---

