---
title: "May Ubuntu packages have higher version requirements than upstream?"
date: 2008-06-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jmillikin on 2008-06-12
Some months ago, I wrote a patch to Rhythmbox to support display of cover art embedded in music files. It's not been adopted upstream because they don't want to depend on glib 2.16. But it seems to me, that wouldn't really be a problem for the Ubuntu version because 2.14 isn't even available in the repository. Are we allowed to submit debdiffs that raise the version requirements of packages?

---

### Post by RAOF on 2008-06-12
Yes, certainly.  You'll want to attach this to a bug on launchpad and link this bug to the upstream report you originally attached the patch to.  Mention on the launchpad bug that the reason upstream doesn't want it is version concerns.

---

### Post by bruce89 on 2008-06-13
> **jmillikin said:**
> It's not been adopted upstream because they don't want to depend on glib 2.16.

Have they a reason for that?

---

### Post by jmillikin on 2008-06-13
> **bruce89 said:**
> Have they a reason for that?

Maybe they're trying to remain compatible with distributions that ship older versions of glib. Same thing happened with one my my patches to GStreamer -- they waited until they could bump their Glib dep before including it.

Getting Intrepid built in a VM now, will attach a debdiff to the launchpad bug once I have it ready.

---

### Post by bruce89 on 2008-06-13
Perhaps it should be ifdefed? I don't like distribution patches like this, it means not everyone benefits.

---

### Post by jmillikin on 2008-06-13
> **bruce89 said:**
> Perhaps it should be ifdefed? I don't like distribution patches like this, it means not everyone benefits.

The patch has been in GNOME bugzilla for 4 months, and one of the RB developers decided not to include it. I can't *force* upstream to accept patches. Maybe when it's more widely tested, they will be willing to take another look at accepting it. I don't think any of the objections to including it matter, but upstream (obviously) disagrees.

The precise objections were:
[quote="Jonathan Matthew"]There are a couple of things I don't like about this.

- saves stuff to disk without me asking it to
- doesn't work for things that aren't imported into the library (daap/upnp,
mostly)
- adds yet another field to RhythmDBEntry that is likely to be sparsely used
- the extracted image filename scheme doesn't seem right, but I can't put my
finger on what's wrong with it

rb_get_extension_for_mime_type probably works for just about all formats as it
is, but gstreamer media types (as returned by gst_structure_get_name) are not
mime types, even though they look like they are.  I'm not sure what the
alternative is.[/quote]

---

### Post by olskar on 2008-06-13
"the extracted image filename scheme doesn't seem right, but I can't put my
finger on what's wrong with it"

Great reason.

---

### Post by jmillikin on 2008-06-13
Attached debdiff at [bug #109889](https://bugs.launchpad.net/rhythmbox/+bug/109889).

---

