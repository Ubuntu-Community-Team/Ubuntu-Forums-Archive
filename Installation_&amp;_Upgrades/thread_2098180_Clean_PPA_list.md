---
title: "Clean PPA list"
date: 2012-12-25
forum: Installation &amp; Upgrades
---

### Post by Tclarkie on 2012-12-25
Can somebody please post a clean, out of the box repository list for ubuntu 12:10, i've broken mine?

Thanks

---

### Post by Kirk Schnable on 2012-12-25
> **Tclarkie said:**
> Can somebody please post a clean, out of the box repository list for ubuntu 12:10, i've broken mine?

Thanks

Take a look at this file on your Ubuntu machine.
/usr/share/doc/apt/examples/sources.list

That file will work in the location:
/etc/apt/sources.list

You'll also want to clean out any contents in:
/etc/apt/sources.list.d/

---

### Post by Tclarkie on 2012-12-25
Many thanks

---

### Post by Kirk Schnable on 2012-12-25
> **Tclarkie said:**
> Many thanks

No problem!  If everything is taken care of, please mark this thread as Solved using the Thread Tools menu.

Kirk

---

### Post by arpanaut on 2012-12-25
This may help you:
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

As for the PPA's  the only default are for the "partner" and "extras"

Edit: actually those are not PPA's per se but do appear in the "Other Software" in the GUI for Software Sources.
There are no PPA's enabled by default, sorry for the misleading information.

---

