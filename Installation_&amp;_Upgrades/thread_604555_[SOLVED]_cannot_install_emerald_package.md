---
title: "[SOLVED] cannot install emerald package"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by morgengenuss on 2007-11-06
i know the problem i am about to describe is somewhat weird. i've never experienced this until now (i'm with ubuntu since breezy) and i don't seem to be able to find a solution.

my problem sounds like easy to solve at a first glance: i simply cannot install emerald from the repositories. i get the error message:
```
Package emerald is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emerald has no installation candidate
```
something about the state of my system: i upgraded from feisty to gutsy via update-manager, everything went fine. i used xgl and beryl/emerald in feisty before and the upgrade didn't brake beryl, but emerald didn't work anymore. i removed all beryl-related packages and reconfigured my xgl-session to use compiz-fusion, which works just fine. then i removed and in a second step completely removed emerald via synaptic, since it was broken (still the old feisty version). then i assumed that the gutsy version of the package should be found in the repositories and synaptic even displays the two essential packages for emerald to work (emerald, libemeraldengine0), but without version numbers and description. the only package that seems ok is libemeraldengine-dev (which was not installed previously, meaning in feisty), but of course it's not installable because dependent on libemeraldengine0.

_stuff i have done:_
1. i have the universe repositories enabled.
2. i tried at least 5 different mirrors. i even manually checked whether the emerald package was on the mirrors.
3. i tried apt-get, aptitude, synaptic and add/remove, of course all of them giving me the same output.
4. i ran apt-get update a few times, tried different sources.list.
5. i looked for the package and version number with apt-cache search and found the correct version for gutsy.
6. checked /var/lib/dpkg/info/*emerald* - there were no such files found (possible explanation for missing informations in synaptic). also /var/lib/dpkg/status still contains old software from gutsy (incl. beryl and the older emerald).

_workarounds i tried:_
1. manually downloaded emerald_0.3~git20070717-0ubuntu1_i386.deb from the gutsy universe repositories of the main server, but of course i cannot install it because the dependencies are not satisfiable (libemeraldengine0).
2. used dpkg -i --force-depend on the emerald package which produced a (of course) broken install of emerald, then tried to repair it but without luck.
3. tried to manually compile libemeraldengine0, but there were quite a few dependencies unmet and up to now i would still prefer to solve the issue to manually resolving the dependencies. (also at the moment i'm using gtk-window-decorator to have some decorations, which is as a workaround quite ok.)

so although i do have some workaround i would like to know wtf is going on with my packages. also this problem could affect other packages that i haven't stumbled upon up to now.

any help/comment greatly appreciated.

---

### Post by morgengenuss on 2007-11-06
well seems that downloading and installing first libemeraldengine0.deb and then emerald.deb resolves the issue...

---

### Post by gators38 on 2008-04-14
ignore this, sorry.

---

