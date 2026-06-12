---
title: "Can't install Gimp"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philbo on 2008-09-26
I can't install Gimp v2.5.4-1~ppa1 in my Intrepid system.

I get an error :
Could not mark all packages for installation or upgrade.

gimp:
 Depends: libpoppler-glib2 (>=0.6) but it is not installable
 Recommends: gimp-gnomevfs but it is not going to be installed or
 	gimp-libcurl but it is not going to be installed
 Recommends: gimp-python but it is not going to be installed

Anyone got any ideas?

---

### Post by mc4100 on 2008-09-26
The version you're trying to install from Christoph's PPA is packaged for Hardy, which uses versions of libpoppler-glib2, but there's dependency problems since Intrepid has libpoppler-glib3. It will still install, using force with dpkg (see screenshot) ... but this results as it being labeled as broken, which breaks Synaptic and Update Manager (that, to be fair, just want to fix a problem); I'd say it was a bad idea. If you really want to install the newest version, then finding an Intrepid package or building it from source yourself is the way to go.

---

