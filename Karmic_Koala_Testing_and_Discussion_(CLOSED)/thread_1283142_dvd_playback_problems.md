---
title: "dvd playback problems"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2009-10-05
i have been having a dvd playback problem for awhile now. 
in which ever software that i use vlc or totem.

some dvd's will play ok. some dont play at all giving errors. some stop with error after about 10-15 mins into the movie.

when it stops part way through get error unable to read from resource (totem).
when i cant play dvd's at all get errors: 
VLC - VLC is unable to open the MRL 'dvd:///dev/sr0'.
totem - either says you dont have permission to read from the resource or just says cant read resource. 

i have been using ubuntu 9.10 since alpha 2 and i haven't tried reinstalling. 
i have the packages ubuntu-restricted-extras, libdvdcss2 and w32codecs installed.  

any suggestions to fix this, as it very annoying that some dvd's work and some dont. i didn't any problems with dvd playback in jaunty.

---

### Post by phenest on 2009-10-05
Any chance you could list the DVD's that don't play?

---

### Post by moviemaniac on 2009-10-05
It's a known bug: [https://bugs.launchpad.net/bugs/438065](https://bugs.launchpad.net/bugs/438065)

A workaround is to either uninstall libbrasero-media0 or install the brasero and libbrasero-media0 packages version 2.27.92 from your /var/cache/apt directory (unless you're on a fresh install that's younger than 10 days or so in that case the old files won't be there).

---

### Post by terry_gardener on 2009-10-05
i have uninstalled libbrasero-media0 and the dvd's play all the way through. 
i have just tried 5 dvd's and they play all the way through and fast forwarded them to find out. 

sadly uninstalling the above package removes brasero (which i am not bothered about because i use k3b to burn discs anyway) and rhythmbox which i use all the time.

---

### Post by moviemaniac on 2009-10-05
there you go: [http://www.doblmann.de/brasero2.27.92.tar.gz](http://www.doblmann.de/brasero2.27.92.tar.gz)

the archive contains the last (official, signed by ubuntu, taken from my apt-cache) brasero-versions before the problematic update. Extract them to a new directory and install them with "sudo dpkg -i *.*" (gdebi is broken right now). After that you can reinstall rhythmbox. It would also be a good idea to lock the two brasero-packages in Synaptic so they don't get updated with the broken versions. You can remove the version-lock once a solution to the bug is found.

PS: My webspace-plan doesn't include unlimited traffic so please don't link to the file above anywhere else than here.

---

### Post by terry_gardener on 2009-10-05
thanks moviemaniac 

but i found the package somewhere else and installed it and it now works.

here is the link to the i386 package. 

[http://launchpadlibrarian.net/31473036/libbrasero-media0_2.27.92-0ubuntu1_i386.deb]("http://launchpadlibrarian.net/31473036/libbrasero-media0_2.27.92-0ubuntu1_i386.deb")

---

