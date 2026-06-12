---
title: "Recent libxine 1.1.8 update on Kubuntu"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by aln on 2007-11-21
I've been notified about libxine1 update today. Great! But why does it want to install all the GNOME-related packages like gconf2, libxine1-gnome, libgnomevfs2-0 etc. :confused: I'm on Kubuntu Gutsy and don't need this stuff. What's the reason for creating all those dependencies?

---

### Post by birdflesh10 on 2007-11-21
Right. Xine engine shouldn't need any gnome stuff to upgrade. I have 2 packages for upgrade (libxine1 libxine1-ffmpeg) and 18 new to install (gamin gconf2 gconf2-common gnome-mime-data libavahi-glib1 libgamin0 libgconf2-4 libgnomevfs2-0 libgnomevfs2-common libidl0 liborbit2 libwavpack1 libxine1-console libxine1-gnome libxine1-misc-plugins libxine1-plugins libxine1-x shared-mime-info). :(

---

### Post by aln on 2007-11-27
I'v got the massage from the maintainer of libxine1 package:

"Is it possible that you have enabled backports? The packages from
  hardy do indeed have an alternative dependency on 
  'libxine1-plugins | libxine1-misc-plugins'. This means that you can
  avoid installing libxine1-gnome by selecting libxine1-misc-plugins
  instead of libxine1-plugins.

The dependency has to be in this order in order to support upgrades from
dapper. It will be lessened after hardy release for hardy+1."



On the other hand I've managed to get through this update simply by deselecting all packages except libxine1 and libxine1-ffmpeg. It' didn't prevent lbixine1from being upgraded.

---

