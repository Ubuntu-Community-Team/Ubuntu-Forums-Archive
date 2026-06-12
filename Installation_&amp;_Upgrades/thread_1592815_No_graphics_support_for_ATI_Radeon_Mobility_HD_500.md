---
title: "No graphics support for ATI Radeon Mobility HD 5000 series"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by castironpants on 2010-10-10
So Ubuntu had been working great in Lucid, and when I upgraded to Maverick the support for my graphics card stopped. It has the proper driver ("ATI/AMD Proprietary FGLRX graphics driver") active and fglrx, fglrx-amdccle and fglrx-modaliases are all at 2:8.780-0ubuntu2. I also have the xorg radeon package installed. Yet, whenever I try to enable desktop effects (to get compiz to work) it says that Desktop effects could not be enabled.

---

### Post by Mark Phelps on 2010-10-11
Did you unistall the fglrx driver BEFORE you did the upgrade?  If not, that's probably the source of your problems.  In that case, remove the fglrx driver stuff and reinstall.  Should then be OK.

However, did see some traffic regarding fglrx problems with 10.10 indicating that the one from the repos is bad and you need to get one from the ppa's.  Sorry, don't have the ppa specification.

---

### Post by castironpants on 2010-10-11
This was from a fresh install.

I think you're referring to the x-swat ppa, and that only made it worse. Couldn't load, had to upgrade to the standard ones from the command line because it couldn't detect any screens.

That is unless there's another ppa I don't know about.

---

### Post by castironpants on 2010-10-11
Even after purging everything, installing the 8.73 "TESTING USE ONLY" (from packages) and doing a "sudo aticonfig --initial" and reboot, I STILL can't enable desktop effects! What gives?

---

### Post by anilbpai on 2011-01-09
Every am suffering from the same problem... Waiting to see Compiz Effects on laptop :(

---

