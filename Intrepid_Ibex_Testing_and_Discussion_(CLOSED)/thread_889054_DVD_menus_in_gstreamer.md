---
title: "DVD menus in gstreamer?"
date: 2008-08-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by pferraro on 2008-08-13
gstreamer0.10-plugins-bad 0.10.8-1 just hit the repos.
[http://gstreamer.freedesktop.org/releases/gst-plugins-bad/0.10.8.html](http://gstreamer.freedesktop.org/releases/gst-plugins-bad/0.10.8.html)
Item #3 in the release notes:
 * Experimental DVD navigation support

Anyone tried this yet?

---

### Post by razmakati on 2008-08-13
Tried and failed

It is asking for a DVD subpicture decoder plugin of which I can not find with the research I've done. Something about "No decoder to handle media type 'video/x-dvd-subpicture'"

Worse still this update botched the ability to play DVD's by letting Totem open them as one continuous file.

Oh Well the joys of development.

Once this feature smooths itself out though G Streamer has sealed the deal

DVD menus is the only thing that has prevented my better half from accepting Linux totally.

---

### Post by Nullack on 2008-08-13
Have a look at my post in this section of the forum on the Intrepid Video thread. DVDNAV and DVDREAD are hard coded into the bad plugin set which makes an easy install problematic cos then without forcing it, the bad plugin set will also be removed. DVDNAV and DVDREAD will be used first so it has to go.

The menus also require compile time switches to be enabled.

The developer on his blog said recently it wont be feature complete for 2.5 months.

---

