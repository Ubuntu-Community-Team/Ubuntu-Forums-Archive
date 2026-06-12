---
title: "Please help me compile Totem from source - i'm stuck on last error"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by tzily on 2010-07-27
Hello, I can't compile the last version of Totem - 2.90.5 from source even if i've installed all the packages it needs. Here's the final error:

> checking for GST... configure: error: Package requirements (gstreamer-0.10 >= 0.10.28.1 gstreamer-base-0.10 >= 0.10.28.1 gstreamer-plugins-base-0.10 >= 0.10.26 gstreamer-tag-0.10 >= 0.10.26 gconf-2.0) were not met:

Requested 'gstreamer-0.10 >= 0.10.28.1' but version of GStreamer is 0.10.28
Requested 'gstreamer-base-0.10 >= 0.10.28.1' but version of GStreamer base classes is 0.10.28

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GST_CFLAGS
and GST_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
The thing is i'm already on gconf 2 + libgconf2-dev and gstreamer 0.10.28.1 + dev files and everything :( what's wrong with this error?

It would of been more easy if there was a way to update the Totem repos in synaptic, but last version there is 2.30.2-0ubuntu1.

---

