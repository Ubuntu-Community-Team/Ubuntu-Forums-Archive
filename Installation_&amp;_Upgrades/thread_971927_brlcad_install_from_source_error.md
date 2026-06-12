---
title: "brlcad install from source error"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by pbox on 2008-11-05
i just migrated to ubuntu recently. and was looking for cad softwares, i can't find brlcad in apt-get and synaptic so i was forced to build from the source.  i tried the older version with the .deb file but still can't make it to work. i installed build-essential and xorg-dev already. i know building from source is not recommended on newbie like me but it seems i don't had a choice. i was following all procedures regarding brlcad on this site and ended up on this error.  that's why i joined the forum since i don't understand whats wrong or lacking =p. i installed most files related to tk and x11 which fix some previous error but not this one.

Making all in openNURBS
make[3]: Entering directory `/usr/local/src/brlcad-7.10.0/src/other/openNURBS'
/bin/bash ../../../libtool --silent --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../../../include   -I/usr/local/include -DBRLCADBUILD=1 -I../../../include  -pipe -fno-strict-aliasing -fno-common -fexceptions -g -c -o opennurbs_3dm_attributes.lo `test -f 'opennurbs_3dm_attributes.cpp' || echo './'`opennurbs_3dm_attributes.cpp
In file included from /usr/include/c++/4.2/new:44,
                 from opennurbs_system.h:170,
                 from opennurbs.h:27,
                 from opennurbs_3dm_attributes.cpp:17:
/usr/include/c++/4.2/cstddef:55: error: '::ptrdiff_t' has not been declared
make[3]: *** [opennurbs_3dm_attributes.lo] Error 1
make[3]: Leaving directory `/usr/local/src/brlcad-7.10.0/src/other/openNURBS'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/brlcad-7.10.0/src/other'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/brlcad-7.10.0/src'
make: *** [all-recursive] Error 1

i think i need someone who can explain to me what's going on.

offtopic question: why does blender in get-apt not updated? i run sudo apt-get update but still the version of blender it provides is not updated and so was in gimp.

---

### Post by brlcad on 2008-12-24
That error looks like a problem with your compilation environment setup.  There's something wrong with your standard C++ header files.  

Make sure you have installed the build-essential package.  If you have it installed and still get the error, try upgrading to gcc 4.3

Cheers!
Sean

---

