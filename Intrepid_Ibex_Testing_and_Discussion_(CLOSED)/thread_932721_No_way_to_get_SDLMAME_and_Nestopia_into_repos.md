---
title: "No way to get SDLMAME and Nestopia into repos?"
date: 2008-09-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by denzilla on 2008-09-28
Repos still have SDLMAME .123 and MAMEDEV is closing in on version .128. Also, how did the finest NES emualator Nestopia miss an inclusion?

---

### Post by amano on 2008-09-28
You can add the finest (GNOME) SNES emulator Snes9x (you can get some debs here: [https://launchpad.net/~bearoso/+archive](https://launchpad.net/~bearoso/+archive)) and the by far finest Amiga emulator E-UAE (some debs can be found in this ppa: [http://morgoth.free.fr/ubports/](http://morgoth.free.fr/ubports/) ) to this list (forget the ancient cruft that can be found in the repos).

I guess that Debian is rather reluctant with including gaming and emulation software or even updating it. And without having these things in Debian, they cannot get synchronnized with Ubuntu.

The freshly open-sourced Sim City (now called Micropolis) is still missing as well from Debian and thus from Ubuntu as well.

The correct way would to file a bug, but at least for some of those bugs already exist. It could be a better idea to complain to the Debian people to update their stuff and remove the cruft.

Rather barebone and ancient versions of snes9x, MAME and the original UAE can be found in the repos and some ancient and partly broken NES emulators as well.

---

### Post by denzilla on 2008-09-28
Shame no one has set up an emu dedicated repo for Ubuntu that maintains latest builds for all the popular emulators. Personally, I don't like DL'ing debs from unknown sources. Might be a nice side project for someone with the no-how :)

---

### Post by jlacroix on 2008-09-28
> **denzilla said:**
> Shame no one has set up an emu dedicated repo for Ubuntu that maintains latest builds for all the popular emulators. Personally, I don't like DL'ing debs from unknown sources. Might be a nice side project for someone with the no-how :)

I agree, someone should do it. Unfortunately my packaging is rusty or else I would do it.

---

### Post by wgrant on 2008-09-29
Rather than making another useless third-party repository, people could instead focus their efforts on getting the newer versions into Ubuntu - before feature freeze.

---

### Post by denzilla on 2008-09-29
> **fujitsu said:**
> Rather than making another useless third-party repository, people could instead focus their efforts on getting the newer versions into Ubuntu - before feature freeze.

I'm not sure I understand why feature freeze even applies to third party applications like MAME or Nestopia. They're not "features", just applications one could DL from the repos. The whole argument about compatibility is pretty much out the window, cause its not like anyone is going to do extensive testing/bugfixing to something like an arcade/console emulator other than the authors themselves. Does anyone check whether the current repo versions work from distro release to distro release anyway?

---

### Post by wgrant on 2008-09-29
> **denzilla said:**
> I'm not sure I understand why feature freeze even applies to third party applications like MAME or Nestopia. They're not "features", just applications one could DL from the repos. The whole argument about compatibility is pretty much out the window, cause its not like anyone is going to do extensive testing/bugfixing to something like an arcade/console emulator other than the authors themselves. Does anyone check whether the current repo versions work from distro release to distro release anyway?

FeatureFreeze had UpstreamVersionFreeze merged into it a couple of release cycles ago. UpstreamVersionFreeze existed because experience shows that it's not a good idea to get a new, buggy upstream release into the development distroseries a week before release, as it's not unlikely that it'd be more buggy than the old one. There may be upstream bugs, there may be integration issues, they might need newer libraries which will then need a rebuild of the archive only to introduce new bugs... Freezing like we do is the best way to avoid such horrors.

As for testing, that's why we have testers... if people don't test things, then no, people don't test things. But the sort of people who want to upgrade applications to their latest crackful versions should be the sort of people who run the latest development distroseries, so should be the sort of people doing the testing.

---

