---
title: "How do I go about getting a app added to the repo?"
date: 2008-11-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by denzilla on 2008-11-05
I want to get Nestopia and the current version of SDLMAME added to the repos for JJ. Where do I start?

---

### Post by smartboyathome on 2008-11-05
Read up on these:

[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)
[https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

---

### Post by ShirishAg75 on 2008-11-05
Although the above is of course the most desirable, although if you are not upto packaging, even then all is not lost.

You can file a needs-packaging request for ubuntu but in order to do that you will have to do open an account at launchpad (which is not free software atm :( )

[http://launchpad.net](http://launchpad.net) 

b. The first thing is to check if the package is in debian.org [http://packages.debian.org](http://packages.debian.org) Its always nicer if the package is in debian so one just needs to give syncing and merging requests from time to time (sometimes even that is not necessary)

c. There is also a package called reportbug, install it either through synaptic or through apt-get 

```
 $ sudo apt-get install reportbug
```d. Then file a bug using reportbug against wnpp. The howto to do the same is given at [http://www.debian.org/devel/wnpp/](http://www.debian.org/devel/wnpp/)

You can look up few requests which people have made at [http://www.debian.org/devel/wnpp/requested](http://www.debian.org/devel/wnpp/requested) to understand the information you need to post. 

e. Wait for a couple of minutes and then once you get the confirmation from debian confirming the bug you can copy and paste the contents of the wnpp you had given at debian to ubuntu . 

Some examples of packaging request in ubuntu 

[https://bugs.launchpad.net/ubuntu/+bugs?field.tag=needs-packaging](https://bugs.launchpad.net/ubuntu/+bugs?field.tag=needs-packaging)

f. Also make sure that you also add the upstream debian request. This makes it easier for people. 

There are instances however, specifically with licensing, if it has not a pure copyleft license like GNU GPL that it **may** not get packaged in Debian but in Ubuntu the possibility is higher. 

You could also put up a bug-request in just launchpad itself but I like to cover as much as ground as possible. 

Just my 0.02 cents/dollar :)

---

### Post by denzilla on 2008-11-06
I'm not into the compiling/packaging stuff, all I want is to get someone to add them to the repos for the next release. Nestopia and MAME are OSS, so it shouldn't be an issue, right?

---

### Post by amano on 2008-11-06
All emulation related programs in the repositories are just unmaintained, ancient cruft, while there are wonderful shiny versions out there in the wild...

NES --> Nestopia: [http://rbelmont.mameworld.info/?page_id=200](http://rbelmont.mameworld.info/?page_id=200)
Megadrive --> Gens/GS: [http://info.sonicretro.org/Gens/GS#Other_Information](http://info.sonicretro.org/Gens/GS#Other_Information)
Super Nintendo --> SNES9x: [http://www.snes9x.com/phpbb2/viewtopic.php?t=3703](http://www.snes9x.com/phpbb2/viewtopic.php?t=3703)
Amiga --> E-UAE: [http://www.rcdrummond.net/uae/](http://www.rcdrummond.net/uae/)
MS-DOS --> DBGL (DosBox Frontend in java): [http://home.quicknet.nl/qn/prive/blankendaalr/dbgl/](http://home.quicknet.nl/qn/prive/blankendaalr/dbgl/)

And the very hyped Open-Sourcing of SimCity 1 as Microlpolis wasn't dealt with either:
[http://alanbshepard70.googlepages.com/micropolis.html](http://alanbshepard70.googlepages.com/micropolis.html) and [http://ppa.launchpad.net/martin-espinoza/ubuntu/pool/main/m/micropolis/](http://ppa.launchpad.net/martin-espinoza/ubuntu/pool/main/m/micropolis/)
Micropolis thread: [http://ubuntuforums.org/showthread.php?t=932721&highlight=Sim+City](http://ubuntuforums.org/showthread.php?t=932721&highlight=Sim+City)


Someone should file bugs for that.

---

### Post by smartboyathome on 2008-11-06
> **denzilla said:**
> I'm not into the compiling/packaging stuff, all I want is to get someone to add them to the repos for the next release. Nestopia and MAME are OSS, so it shouldn't be an issue, right?

File a needs-packaging bug then, but it might not get packaged if no one wants to package it. Creating debs aren't simple, so it can take a little while to create one.

---

