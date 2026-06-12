---
title: "Gnome settings daemon"
date: 2008-07-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by chrismine on 2008-07-04
For a while now I get an error box that Gnome settings daemon cannot be started.  Does it happen with on your PC's too or is it a bug?  Thanks.

---

### Post by MastroPino on 2008-10-22
I have the same issue after an apt-get upgrade today

Help us xD

---

### Post by MastroPino on 2008-10-22
> **MastroPino said:**
> I have the same issue after an apt-get upgrade today

Help us xD

Remove libvisual-0.4-plugins solves this.

---

### Post by psyphen on 2008-10-22
Same exact issue here

Removed libvisual-0.4-plugins and it works now.
Hope that's not a permanent solution, though :P. Also I don't know about you guys, but my volume control still doesn't show up in the top right now so it's not totally fixed.

---

### Post by plun on 2008-10-22
You must add a new volume control to the panel > just right click and "add to panel".

-----------------

This bug was introduced during RC freeze and its ongoing work for the moment, maybe we must wait for an update ???

[https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448](https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448)

Nevertheless, easy to remove this package.

---

### Post by plun on 2008-10-22
Update accepted    :)

> libvisual-plugins (0.4.0.dfsg.1-2ubuntu4) intrepid; urgency=low

  * New patch, 60_no-const-vispluginfo-in-nastyfft, the static VisPluginInfo
    in nastyfft was declared as const, but libvisual write to its refcount
    when it visual_object_unref()s it (nasty!).  This is broken at various
    levels: libvisual shouldn't be writing to this static plugin which is
    allocated by a dlopen()ed plugin, and it should also honor the "const
    VisPluginInfo" API...  Anyway, nastyfft was the only occurrence and this
    fixes the crash for now; LP: #287448.

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/009206.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/009206.html)




Also new walk around see bug.... I don't see any reasons for enabling the ppa

---

