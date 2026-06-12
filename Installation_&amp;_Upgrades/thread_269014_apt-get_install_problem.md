---
title: "apt-get install problem"
date: 2006-10-01
forum: Installation &amp; Upgrades
---

### Post by dmsn on 2006-10-01
Hey 
Im trying to install gtk and gtk+.
But i get problem, why i get this and how can i fix it?

Thanks


sudo apt-get install gtk+*
..............
Note, selecting gtk2-engines-lighthouseblue for regex 'gtk+*'
Note, selecting gtk-engines-thingeramik-data for regex 'gtk+*'
Note, selecting libgtk1.3-common for regex 'gtk+*'
Note, selecting r-cran-gtools for regex 'gtk+*'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ardour-gtk-i686: Conflicts: ardour-gtk
  gtkpod-aac: Conflicts: gtkpod
  libgtk2-ex-podviewer-perl: Conflicts: libgtk2-podviewer-perl but 0.09-2 is to be installed
  libgtkextra-dev: Conflicts: libgtkextra17-dev but 0.99.17-2.2 is to be installed
  libgtkextra17-dev: Conflicts: libgtkextra-dev
  monodoc-gtk2.0-manual: Conflicts: monodoc-gtk-manual but 1:1.0.10-3ubuntu1 is to be installed
  monodoc-gtksourceview2.0-manual: Conflicts: monodoc-gtksourceview-manual but 0.5-7 is to be installed
  snd-gtk: Conflicts: snd-gtk-alsa but 7.8-1.1 is to be installed
  snd-gtk-alsa: Conflicts: snd-gtk but 7.8-1.1 is to be installed
  xara-gtk: Conflicts: xara-gtk-byte but 1.0.11build1 is to be installed
  xara-gtk-byte: Conflicts: xara-gtk
E: Broken packages
dmsn@lapp:~/programs/$

---

### Post by croak77 on 2006-10-01
Try installing just libgtk1.2 and libgtk2.0-0.

---

