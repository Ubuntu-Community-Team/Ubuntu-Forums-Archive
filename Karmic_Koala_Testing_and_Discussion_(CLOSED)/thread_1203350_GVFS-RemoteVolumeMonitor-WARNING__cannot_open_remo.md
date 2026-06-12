---
title: "GVFS-RemoteVolumeMonitor-WARNING **: cannot open remote-volume-monitors"
date: 2009-07-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dinxter on 2009-07-03
getting,

(nautilus:5768): GVFS-RemoteVolumeMonitor-WARNING **: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory

with a number of different apps

is this a gvfs bug or are the apps looking for something that isnt meant to be there anymore?

gvfs/karmic uptodate 1.3.1-0ubuntu3
libgvfscommon0/karmic uptodate 1.3.1-0ubuntu3

---

### Post by dinxter on 2009-07-03
seems remote-volume-monitors is in gvfs-backends, i'm taking it its not a problem as gvfs doesnt depend on gvfs-backends, is it supposed to though?

---

### Post by chrisccoulson on 2009-07-03
gvfs **recommends** gvfs-backends, which means that you can run it without, but the maintainer doesn't recommend that and most people will want to install gvfs-backends. The recommends are also installed by default. 

You will miss lots of features without gvfs-backends backends though.

---

### Post by dinxter on 2009-07-03
yep, recommends are installed on mine by default, no idea why backends wasnt installed, not quite sure what the critreria is for bumping something up to depends from recommends is, i'm sure there are reasons..

---

