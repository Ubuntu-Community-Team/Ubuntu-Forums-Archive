---
title: "Compiz Stops Working at Random"
date: 2008-11-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by PRGUY85 on 2008-11-23
Hey:

First, I know this is alpha testing and I know bugs are expected.  Right now my current Jaunty testing OS has been working fine, however, 1-2 days ago several instances when Compiz stopped working began to happen.  I notice this because the maximize/minimize animations are gone, the amount of desktop workspaces switch from 4 to 2 and the screen flickers.  When I go to System Monitor, the process compiz.real is not there anymore.  This happens at random and is not caused by any particular event that I know of.

It must be said that before I updated to Jaunty repos, I used Ubuntu Tweak to activate the Compiz Devel repos.  Right now my version of Compiz is:

1:0.7.8-0ubuntu4.2~ppa1 from ppa.launchpad.net
The repo is:

deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main #Compiz Fusion

Should I delete this repo and any other third party repos during testing or it shouldn't matter?

Thanks

---

### Post by go7Ul1ai on 2008-11-24
This happens to me except I use a fully updated Intrepid Ibex on both of my machines, and I happen to use Ubuntu Tweak (0.4.3) also.

Lee

---

### Post by PRGUY85 on 2008-11-24
I believe it has to do with selecting the Compiz Development repos on Ubuntu Tweak.  I reinstalled Intrepid and did not use those repos and it has been fine.

---

### Post by Eclipse. on 2008-11-24
Remove the entry ubuntu-tweak made in your sources.list, remove compiz and then reinstall it.

Jaunty has 0.78 in the repos anyway.

---

