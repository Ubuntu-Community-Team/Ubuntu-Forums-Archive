---
title: "Beta seems to be missing  gst/interfaces/tuner.h"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by wkulecz on 2010-04-13
I've installed all the gstreamer stuff I can find in synaptic but can't compile my program because gst/interfaces/tuner.h is missing.

pkg-config --cflags --libs gstreamer-0.10 gstreamer-interfaces-0.10 worked on 8.04 but gstreamer-interfaces-0.10 seem missing as well.

The sample gstreamer "hello world" program compiles and run correctly, but my code needs to use the gst interfaces to select the proper video capture card input.

Any ideas of where to find what is missing?
Does this merit a bug report on Launchpad?

--wally.

---

### Post by wkulecz on 2010-04-13
Seems libgstreamer-plugins-base0.10-dev was not installed.  Also was hard to find it in synaptic, but its there now in the Libraries - Development section.

---

