---
title: "Compiz Plugins"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by Big_J on 2006-09-23
i was trying to install compiz but I can't install compiz-plugins because it seems an older version is in the repository. Why would a new component be placed with an outdated/incompatible versoin?

```
sudo apt-get install compiz xserver-xgl libgl1-mesa xserve r-xorg libglitz-glx1 compiz-gnome
Reading package lists... Done
Building dependency tree... Done
xserver-xgl is already the newest version.
libgl1-mesa is already the newest version.
xserver-xorg is already the newest version.
libglitz-glx1 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-plugins (>= 0.2) but it is not going to be installed
E: Broken packages

```

```
sudo apt-get install compiz-plugins Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-plugins: Depends: compiz-core (>= 0.0.13.54) but it is not going to be installed
                  Depends: csm (>= 0.5) but it is not installable
E: Broken packages

```

it seems that 0.0.13.38 is the newest version on the repos but compiz-plugins need 0.0.13.54? Where do I get that?

I'm using:
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

---

### Post by K.Mandla on 2006-09-23
I think those repositories are in a state of change right now. Compiz is [forking]("http://www.compiz.net/topic-4591-beryl-informations-announcement") and I was under the impression those repositories were broken.

Would that account for what you're seeing?

---

### Post by Big_J on 2006-09-23
That would explain alot, like why updates to compiz came in on a daily bases and suddenly stopped about five days ago...

But I used those same repositories about three days ago, and they worked fine back then. But if they are broken, is there a working one for now?
Because I'd really hate to wait until all the mess is cleaned up, compiz is not just eye candy for me, it's been really usefull!

---

### Post by K.Mandla on 2006-09-23
None that I'm aware of. You might poke around the compiz.net forums, to see if anyone is backing up the old repositories. Personally, I was waiting for the "beryl-is-ready" announcement before trying them out. :)

---

### Post by crazedgremlin on 2006-10-28
I have the same problem... I really wanted compiz or beryl...whatever I could get working.  Hope the repos are up soon :D

---

