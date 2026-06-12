---
title: "Package problem"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by sryth on 2011-02-23
Hey folks,

I recently came back to Ubuntu after a long hiatus.  In the last week I've installed and re-installed 10.10 several times getting things the way I want them.  Although I've installed on 3 different machines and updated them all almost completely, I'm having a problem downloading the package "openoffice.org-core"  On every install on all 3 machines it stops at exactly 20.5 MB out of 27.3   Is anyone else having this problem? 

I'm thinking it is an issue with the repo, unless someone can think of something I'm possibly missing.

EDIT: This problem has been continuous over the last week, isn't a temporary connection issue.

---

### Post by tommcd on 2011-02-23
> **sryth said:**
> 
I'm thinking it is an issue with the repo, unless someone can think of something I'm possibly missing.

Are you using any third party repos in your sources.list? This includes those all too problematic and totally unsupported PPA repos.
What happens if you run:
```
sudo apt-get install openoffice.org-core
```
The openoffice.org-core package is present in the default 10.10 repos:[http://packages.ubuntu.com/maverick/openoffice.org-core](http://packages.ubuntu.com/maverick/openoffice.org-core)

---

### Post by sryth on 2011-02-24
> **tommcd said:**
> Are you using any third party repos in your sources.list? This includes those all too problematic and totally unsupported PPA repos.
What happens if you run:
```
sudo apt-get install openoffice.org-core
```
The openoffice.org-core package is present in the default 10.10 repos:[http://packages.ubuntu.com/maverick/openoffice.org-core](http://packages.ubuntu.com/maverick/openoffice.org-core)


Not using any third party repos.  Default only, and that is where it is failing.  Stops at 20.5 MB every time on every machine, tried both resuming the apply changes in synaptic, tried apt-get on the command line, tried deleting the partially downloaded package from the apt cache and re-downloading.  Even tried downloading the package directly from the ubuntu website with firefox and halted at the same point.  Tried each of these solutions a few times a day for the last 5 days.

---

### Post by tommcd on 2011-02-24
From the: settings > repositories, section in synaptic, see if you can change to a different mirror. Then click the link to reload the repos when prompted. Then see if you can install the openoffice.org-core package. Perhaps the openoffice.org-core package on the mirror you are using is corrupted or something.

---

