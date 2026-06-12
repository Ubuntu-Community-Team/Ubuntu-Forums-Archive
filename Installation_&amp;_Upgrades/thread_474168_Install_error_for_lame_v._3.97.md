---
title: "Install error for lame v. 3.97"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by Blue Toes on 2007-06-14
when trying to install lame, to try and get gnormalizer (idealy a cd ripper) working, i was using the generic instalation instructuins, and when i got to the "make install' part somthing went wrong, im not sure but i think it was somewhere around here in what the terminal shows:

test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libmp3lame.la' '/usr/local/lib/libmp3lame.la'
/usr/bin/install -c .libs/libmp3lame.so.0.0.0 /usr/local/lib/libmp3lame.so.0.0.0
/usr/bin/install: cannot create regular file `/usr/local/lib/libmp3lame.so.0.0.0': Permission denied
make[3]: *** [install-libLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/kevin/Desktop/lame-3.97/libmp3lame'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/kevin/Desktop/lame-3.97/libmp3lame'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/kevin/Desktop/lame-3.97/libmp3lame'
make: *** [install-recursive] Error 1

i think ive had similar problems when installing things before, does anyone know whats going on?

---

### Post by merlinus on 2007-06-14
version 3.96.1 is available via Synaptic, and everything you need will be installed.

-merlin

---

