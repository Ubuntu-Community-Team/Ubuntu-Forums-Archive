---
title: "help installing sonata"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by vertigo1980 on 2007-04-26
hi all,

i am trying to install a music player, [sonata](http://sonata.berlios.de/index.html) on feisty. in the download section it has links to ubuntu debs for the latest version, but when i try installing it, it won't let me since the dependency "python" is unsatisfiable. the funny thing is that i DO have python, as well as 2.4 and 2.5. i would usually compile from source but i'm not that good at it and i don't want to have to download so much dev files on my dialup connection.

the feisty repos have 1.0 available (which installs perfectly on synaptic), but the latest version has some good bugfixes i need. i am sure the dependency problem is because the package is not built for feisty, probably edgy. can anyone please upload a package for feisty? or tell me how to get around this without compiling?

thanks! :)

---

### Post by vertigo1980 on 2007-04-27
ok i tried installing it via the terminal, dpkg -i, it said:

```
Unpacking sonata (from .../Desktop/sonata_1.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of sonata:
 sonata depends on python (<< 2.5); however:
  Version of python on system is 2.5.1~rc1-0ubuntu3.
dpkg: error processing sonata (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:

```

but i have the python, phython2.4 and python2.5 packages already installed via synaptic

---

### Post by vertigo1980 on 2007-04-27
ok so i tried compiling it myself, still nothing. i tried installing the gtk/python depenencies, turns out i can't install them because some of their dependencies are broken or something. :(

i really hate to ask, and i've learned the basics of compiling, but any chance someone could compile it for me?

---

### Post by aidanr on 2007-04-27
here's a feisty deb of the latest svn, i haven't a lot of experience with checkinstall so i'm not sure if it'll work for you

---

### Post by vertigo1980 on 2007-04-27
ah thanks aidanr, it works! ;)

much appreciated

i've really gotta get broadband :P

---

