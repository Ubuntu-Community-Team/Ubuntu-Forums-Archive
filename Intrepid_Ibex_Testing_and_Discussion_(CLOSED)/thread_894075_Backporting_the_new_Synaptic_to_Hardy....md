---
title: "Backporting the new Synaptic to Hardy..."
date: 2008-08-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by picpak on 2008-08-18
I just finished building it. However, when I go to use "Quick Search", the entry box is blanked out. :confused: Any ideas? What else do I need to build?

---

### Post by aamukahvi on 2008-08-19
It doesn't even work in Intrepid at the moment...

---

### Post by RAOF on 2008-08-19
You need apt-xapian-index for that box to work.

---

### Post by aamukahvi on 2008-08-19
> **RAOF said:**
> You need apt-xapian-index for that box to work.
Why isn't it automatically installed?

---

### Post by RAOF on 2008-08-19
Because it's in Universe, presumably.

---

### Post by aamukahvi on 2008-08-19
Ah. But it's very weird and counter-intuitive having an inactive searchbox with no documented (afaik) way of activating it. Maybe it'll be promoted to main in time for release?

I think the search box should be hidden if it cannot be used at all.

---

### Post by picpak on 2008-08-19
> **RAOF said:**
> You need apt-xapian-index for that box to work.

Thank you! :KS

Here's the .deb for Hardy:

[http://www.mediafire.com/?0fz0j4awhxl](http://www.mediafire.com/?0fz0j4awhxl)

Enjoy!

---

### Post by olskar on 2008-08-19
> **aamukahvi said:**
> Ah. But it's very weird and counter-intuitive having an inactive searchbox with no documented (afaik) way of activating it. Maybe it'll be promoted to main in time for release?

I think the search box should be hidden if it cannot be used at all.


[https://wiki.ubuntu.com/MainInclusionProcess](https://wiki.ubuntu.com/MainInclusionProcess)

[https://wiki.ubuntu.com/MainInclusionReportTemplate](https://wiki.ubuntu.com/MainInclusionReportTemplate)

:)

---

### Post by philinux on 2008-08-19
I mus admit to not noticing a big difference. Why's the intrepid version better?

---

### Post by Nullack on 2008-08-19
You can read a packages changelog if you search for it:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by cariboo on 2008-08-19
See this bug:

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/250524](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/250524)

---

