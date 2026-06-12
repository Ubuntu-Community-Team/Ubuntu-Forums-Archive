---
title: "banshee and dependency"
date: 2009-01-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by biasquez on 2009-01-30
sudo apt-get install banshee
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  monodoc-base gvfs-bin monodoc-manual
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libart2.24-cil libavahi1.0-cil libboo2.0-cil libgconf2.24-cil libgnome-vfs2.24-cil libgnome2.24-cil libmono-zeroconf1.0-cil libtaglib2.0-cil podsleuth
Suggested packages:
  monodoc-gtk2.0-manual
The following packages will be REMOVED:
  f-spot libart2.0-cil libgconf2.0-cil libgnome-vfs2.0-cil libgnome2.0-cil libgtksourceview2.0-cil monodevelop tomboy
The following NEW packages will be installed:
  banshee libart2.24-cil libavahi1.0-cil libboo2.0-cil libgconf2.24-cil libgnome-vfs2.24-cil libgnome2.24-cil libmono-zeroconf1.0-cil libtaglib2.0-cil
  podsleuth
0 upgraded, 10 newly installed, 8 to remove and 0 not upgraded.
Need to get 3695kB of archives.
After this operation, 23.4MB disk space will be freed.



is it normal that banshee removes packages like f-spot?

---

### Post by nystire on 2009-01-31
I don't think it is normal, but you may find that you are removing some of it's dependencies and not installing any alternatives.

---

### Post by RAOF on 2009-01-31
Until the unexpected **gnome-sharp2** transition is finished, these sort of co-installability problems are to be expected.  It sucks, but it's being worked on.

---

### Post by biasquez on 2009-01-31
ok thanks

---

### Post by hugmenot on 2009-02-04
I'm tired of reading my tomboy notes&#8217; xml files with a text editor. Can you please push an updated tomboy soon?

---

### Post by castrojo on 2009-02-04
> **hugmenot said:**
> I'm tired of reading my tomboy notes’ xml files with a text editor. Can you please push an updated tomboy soon?

Either help out or don't use a development release if your notes are that important. :p

---

### Post by gspat on 2009-02-04
Tomboy works just fine for me??? 8)

---

### Post by hugmenot on 2009-02-05
> **whiprush said:**
> Either help out or don't use a development release if your notes are that important. :p

Well, recently I had looked into why gmime-cil wouldn&#8217;t install its assemblies properly. I wasted more than an hour with no results. Coming from that experience I'd rather defer to the experts, because it's their stuff.

---

