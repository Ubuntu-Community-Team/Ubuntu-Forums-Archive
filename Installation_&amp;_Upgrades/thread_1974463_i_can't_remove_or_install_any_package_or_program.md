---
title: "i can't remove or install any package or program"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by woxuxow on 2012-05-06
i have installed gimp form packages and that caused some problems
i copied gimp packages and some its lib (not all) form 11.10 apt-cash to 12.04 apt-cache

and i have installed them by dpkg -i *.deb on 12.04 
now i have some problems that drive me crazy and i can't correct them
when i try to upgrade or install - remove any package or lib i have get an error that says use apt-get install -f to correct the problems 
when i try that i get an error

```

dpkg: dependency problems prevent configuration of libgegl-0.0-0:
 libgegl-0.0-0 depends on libjpeg62; however:
  Package libjpeg62 is not installed.
dpkg: error processing libgegl-0.0-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of gimp:
 gimp depends on libgegl-0.0-0 (>= 0.0.22); however:
  Package libgegl-0.0-0 is not configured yet.
dpkg: error processing gimp (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 libgegl-0.0-0
 gimp
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i tried to install libgegl-0.0-0_0.0.22-2ubuntu3_i386.deb but it did not work
and i can not remove gimp and its dependencies 

what should i do to get ride of this error

---

### Post by 23dornot23d on 2012-05-06
Is the 12.04 a new installation ..... or a upgrade ?

Quick way to get rid of problems .... re-install 12.04 fresh.

If you cannot remove or install packages .... then the programs that you need cannot be installed to fix said problem easily ..... but maybe someone else can talk you through
a way of correcting the problem you have.

Best of luck ...... I usually use aptitude to sort dependency issues out but it is not installed by default now ......

---

### Post by mips on 2012-05-06
> **MustafaJF said:**
> i have installed gimp form packages and that caused some problems
**i copied gimp packages and some its lib (not all) form 11.10 apt-cash to 12.04 apt-cache**

I would not do that. Rather install gimmp 2.6 from the repos, **sudo apt-get install gimp**

or install gimp 2.8 from the ppa,
```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update && sudo apt-get install gimp
```

---

### Post by woxuxow on 2012-05-06
> **23dornot23d said:**
> Is the 12.04 a new installation ..... or a upgrade ?

Quick way to get rid of problems .... re-install 12.04 fresh.

If you cannot remove or install packages .... then the programs that you need cannot be installed to fix said problem easily ..... but maybe someone else can talk you through
a way of correcting the problem you have.

Best of luck ...... I usually use aptitude to sort dependency issues out but it is not installed by default now ......

I've installed Fresh 12.04
i don't want to re-install it,it is not possible at all
i installed libjpeg62 and now i can install and remove packages but still i can't install any package from apt-cache in other words i can not use --no-download

---

### Post by woxuxow on 2012-05-06
> **mips said:**
> I would not do that. Rather install gimmp 2.6 from the repos, **sudo apt-get install gimp**

or install gimp 2.8 from the ppa,
```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update && sudo apt-get install gimp
```

i didn't know that it might cause bad problems
but now i'm very very careful

---

