---
title: "What happens w/ PPAs set to another release?"
date: 2018-10-15
forum: Installation &amp; Upgrades
---

### Post by Pseudonomous on 2018-10-15
Hello Folks,

Let me lead with the question I actually want answered.  If you enable the KXStudio PPAs the way they suggest, you enup with a whole bunch of PPAs enabled, many which will not match your current release of Ubuntu, like:

deb [http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu](http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu) lucid main
deb [http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu](http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu) trusty main
deb [http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu](http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu) xenial main
deb [http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu](http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu) wily main

...

There's a whole bunch of these for most of the kxstudio PPAs. Does anybody know if the package management tools on ubuntu implicitly ignore PPAs with the wrong release set?  My experiences using apt to install suggests not to me, but I figure I might as well check.

If anybody wants some background on why I'm asking this, keep reading:

After upgrading (by a fresh install, migrating data and configs from a different disk) to 18.04 I've been having issues applications crashing due to memory allocation errors.  I think this may have something to do with library conflicts with the KXstudio PPAs.

Critically I've been having trouble with Armour (which I acquire directly from the upstream binaries) and KDEnlive (which I acquire from the ubuntu repos) crashing.  Both give errors like:

free(): invalid pointer
Aborted (core dumped)

I very strongly suspect that my problems are related to LV2/LADSPA plugins.  I ended up doing a fresh install and had Ardour and KDEnlive working, albeit missing some plugins.  The problems I started noticing occurred after installing a number of LV2 and LADSPA plugin collection packages to try and recover my missing plugins.  I've tried rolling back installed packages and then disabling the kxstudio PPA, but I've got no luck.  Well, KDEnlive started at least starting up again, but Ardour still crashes whenever I try to load a project.

I'm suspecting that I'm just going to have to do another clean install, this time on BTRFS so I can snapshot my root file-system to save my project toward rebuilding a functional desktop software environment.   Annoyingly, this is going to be my 3rd time installing 18.04 on my desktop computer since the first install (an upgrade from 16.04 -> 18.04) was so hopelessly broken on upgrade (I couldn't even get a GNOME session to start, though I was, after spending about an hour getting X11 to work outside of fallback mode) able to load a MATE session) that I already gave up once and did a new clean install.

Luckily, as circumstances would have it, I've got my old installation of 16.04 completely saved to another disk so I will suffer no appreciable data loss and have an emergency fallback option of just going back to using 16.04 (though, long-term, I'm going to have to upgrade eventually).  But I'm really frustrating that I've already burned about a full workday's worth of time trying to get 18.04 mostly functional, only to have messed things up again and put myself back at square one.

FWIW I wouldn't be complaining about KXStudio here, if was able to register at their own forums without running into issues with the registration form.  Unfortunately, using their applications, is the only way I was every to make the pulseaudio to jack bridge work, so I'm compelled to install their software.

---

### Post by dino99 on 2018-10-15
The install script usually does settings itself, choosing your install version by default.
******************************
Adding Launchpad PPA Repositories
Adding Launchpad PPA (Personal Package Archive) is possible conveniently via the command: add-apt-repository. This command is similar to "addrepo" on Debian.

The command updates your sources.list file or adds/edits files under sources.list.d/. Type man add-apt-repository for detailed help.

If a public key is required and available it is automatically downloaded and registered.
Should be installed by default. On older or minimal Ubuntu releases, you may have to install software-properties-common and/or python-software-properties first (sudo apt-get install python-software-properties)

sudo add-apt-repository ppa:<repository-name>
*********************************

If you choose a ppa missing your installed version, then that means it is too old/no more maintained/abandonned....   So forget about it to avoid conflicts/troubles/....

---

### Post by Frogs Hair on 2018-10-16
Looks like no updates for 188 weeks if this is the [PPA]("https://launchpad.net/~kxstudio-team/+archive/ubuntu/ppa") in question. It's up to the maintainer/s of the PPA to update and test for each new Ubuntu release.

---

