---
title: "Whom to inform about broken dependencies?"
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by jdw on 2005-05-03
Where should I go or whom should I inform about broken package dependencies on the "Marillat" repo?  Gstreamer0.8-lame wants a version of libc that Ubuntu apparently doesn't have yet.

There's actually a slightly older version of gstreamer0.8-lame on there that works, but currently you have to manually download it and dpkg to install it.

I also thought that you could do a force version with Synaptic/apt-get to get an older version of a .deb?  I couldn't get that feature to work for this particular .deb, though.

Thanks!

---

### Post by Leif on 2005-05-04
I'm not sure this counts as a broken dependency as marillat isn't really an official ubuntu repository. Updates to the necessary libraries will probably not be available until breezy is released.

---

### Post by jdw on 2005-05-04
In that case, the RestrictedFormats page should probably be updated so that people do a wget and dpkg for that specific gstreamer plugin, instead of apt-get'ing it.

---

