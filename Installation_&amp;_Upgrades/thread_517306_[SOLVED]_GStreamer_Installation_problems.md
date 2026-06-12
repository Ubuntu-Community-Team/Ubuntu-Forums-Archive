---
title: "[SOLVED] GStreamer Installation problems"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by JudasReanimated on 2007-08-04
[B]ude/glib-2.0 -I/usr/lib/glib-2.0/include -I../.. -Wall -DGST_DISABLE_DEPRECATED -g -I../../libs -I../../include -D_COTHREADS_OMEGA -g -O2 -MT libgstbasicomegascheduler_la-gstbasicscheduler.lo -MD -MP -MF .deps/libgstbasicomegascheduler_la-gstbasicscheduler.Tpo -c gstbasicscheduler.c  -fPIC -DPIC -o .libs/libgstbasicomegascheduler_la-gstbasicscheduler.o
gstbasicscheduler.c: In function 'gst_basic_scheduler_chainhandler_proxy':
gstbasicscheduler.c:473: error: invalid lvalue in assignment
gstbasicscheduler.c: In function 'gst_basic_scheduler_select_proxy':
gstbasicscheduler.c:494: error: invalid lvalue in assignment
gstbasicscheduler.c: In function 'gst_basic_scheduler_gethandler_proxy':
gstbasicscheduler.c:543: error: invalid lvalue in assignment
gstbasicscheduler.c: In function 'gst_basic_scheduler_eventhandler_proxy':
gstbasicscheduler.c:581: error: invalid lvalue in assignment
gstbasicscheduler.c: In function 'gst_basic_scheduler_cothreaded_chain':
gstbasicscheduler.c:729: error: invalid lvalue in assignment
gstbasicscheduler.c: In function 'gst_basic_scheduler_chain_remove_element':
gstbasicscheduler.c:883: error: invalid lvalue in assignment
gstbasicscheduler.c: In function 'gst_basic_scheduler_reset':
gstbasicscheduler.c:1060: error: invalid lvalue in assignment
make[3]: *** [libgstbasicomegascheduler_la-gstbasicscheduler.lo] Error 1
make[3]: Leaving directory `/home/user/Desktop/gstreamer-0.7.3/gst/schedulers'
make[2]: *** [check-recursive] Error 1
make[2]: Leaving directory `/home/user/Desktop/gstreamer-0.7.3/gst'
make[1]: *** [check] Error 2
make[1]: Leaving directory `/home/user/Desktop/gstreamer-0.7.3/gst'
make: *** [check-recursive] Error 1[/B]

For some reason every question I've asked on here has gone unanwsered. I really would like to solve this on my own, but google is giving me nothing to go on, and it would make a little girl sad if I couldn't get her this CD which I can't make into audio format without GStreamer for some reason. So come on if you have a heart please help me with this. Now granted if I don't get any help, I'm just going to go and put this on Windows and burn it which will be much easier even though Windows Sucks ***, but still it's getting annoying that I can't get any help at all.

---

### Post by davidjmayo on 2007-08-04
Looks like you are doing things the hard way - trying to build apps from source code

Try Synaptic from system==>administration==>synaptic package manager

type gstreamer in the search bar then check in the box to select and install the package(s)
this will also advise you later of any updates

(another way to do it from Applications==>add/remove --- and again search and look in multimedia)

Maybe the apps in your other threads are there too but I didn't check them

---

### Post by JudasReanimated on 2007-08-04
I tried apt-get, but no luck. The other two were QDVD and DVD Styler. Neither of which I can get to install.

---

### Post by bren on 2007-08-04
can you post the contents of your /etc/apt/sources.list file here....

---

### Post by JudasReanimated on 2007-08-04
Well I'll be darned, Synaptics actually had it, but QDVD and DVD Styler however were not found. Well I take that back. DVD Styler was found, but not installable.

---

