---
title: "Software Center Crashes"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bodycoach2 on 2009-10-28
When I open Ubuntu software center, once it fully loads, it immediately disappears. Not even in system manager anymore. I'm on a Acer TravelMate 260, 768MBram, 5400rpm 80GB HD, intel graphics. Rhythmbox doesn't even open, but that for another thread (unless someone has a fix for that too)

apt-get update/upgrade does not fix the problem. I've been doing that everday as new updates come in. I'm hoping the issue is fixed soon, but not sure as it seems the repos are ready to go to court.

---

### Post by andrewabc on 2009-10-28
Open it via terminal (type in software-center) or whatever it is named, and see what it says after it stops. Should give an error.

[http://packages.ubuntu.com/karmic/software-center](http://packages.ubuntu.com/karmic/software-center)

Search the bugs to see if anything else similar.
[https://launchpad.net/ubuntu/+source/software-center/+bugs](https://launchpad.net/ubuntu/+source/software-center/+bugs)

---

### Post by bodycoach2 on 2009-10-28
Here's the result:
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml

(software-center:2212): GStreamer-WARNING **: adding type GstFourcc multiple times

(software-center:2212): GStreamer-WARNING **: adding type GstIntRange multiple times

(software-center:2212): GStreamer-WARNING **: adding type GstDoubleRange multiple times

(software-center:2212): GStreamer-WARNING **: adding type GstFractionRange multiple times

(software-center:2212): GStreamer-WARNING **: adding type GstValueList multiple times

(software-center:2212): GStreamer-WARNING **: adding type GstValueArray multiple times

(software-center:2212): GStreamer-WARNING **: adding type GstFraction multiple times

(software-center:2212): GStreamer-WARNING **: adding type gdouble multiple times

(software-center:2212): GStreamer-WARNING **: adding type gfloat multiple times

(software-center:2212): GStreamer-WARNING **: adding type gchararray multiple times

(software-center:2212): GStreamer-WARNING **: adding type gboolean multiple times

(software-center:2212): GStreamer-WARNING **: adding type GEnum multiple times

(software-center:2212): GStreamer-WARNING **: adding type GFlags multiple times

(software-center:2212): GStreamer-WARNING **: adding type gint multiple times

(software-center:2212): GStreamer-WARNING **: adding type gint64 multiple times

(software-center:2212): GStreamer-WARNING **: adding type glong multiple times

(software-center:2212): GStreamer-WARNING **: adding type guint multiple times

(software-center:2212): GStreamer-WARNING **: adding type guint64 multiple times

(software-center:2212): GStreamer-WARNING **: adding type gulong multiple times
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

---

### Post by bodycoach2 on 2009-10-28
Here's the result:
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml

(software-center:2212): GStreamer-WARNING **: adding type GstFourcc multiple times

(software-center:2212): GStreamer-WARNING **: adding type GstIntRange multiple times

(software-center:2212): GStreamer-WARNING **: adding type GstDoubleRange multiple times

(software-center:2212): GStreamer-WARNING **: adding type GstFractionRange multiple times

(software-center:2212): GStreamer-WARNING **: adding type GstValueList multiple times

(software-center:2212): GStreamer-WARNING **: adding type GstValueArray multiple times

(software-center:2212): GStreamer-WARNING **: adding type GstFraction multiple times

(software-center:2212): GStreamer-WARNING **: adding type gdouble multiple times

(software-center:2212): GStreamer-WARNING **: adding type gfloat multiple times

(software-center:2212): GStreamer-WARNING **: adding type gchararray multiple times

(software-center:2212): GStreamer-WARNING **: adding type gboolean multiple times

(software-center:2212): GStreamer-WARNING **: adding type GEnum multiple times

(software-center:2212): GStreamer-WARNING **: adding type GFlags multiple times

(software-center:2212): GStreamer-WARNING **: adding type gint multiple times

(software-center:2212): GStreamer-WARNING **: adding type gint64 multiple times

(software-center:2212): GStreamer-WARNING **: adding type glong multiple times

(software-center:2212): GStreamer-WARNING **: adding type guint multiple times

(software-center:2212): GStreamer-WARNING **: adding type guint64 multiple times

(software-center:2212): GStreamer-WARNING **: adding type gulong multiple times
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

---

### Post by andrewabc on 2009-10-28
I'm not sure if you can uninstall and reinstall the program. Might help.

I'd create a bug if it doesn't.

---

