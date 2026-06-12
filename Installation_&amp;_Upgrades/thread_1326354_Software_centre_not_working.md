---
title: "Software centre not working"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by sjrooney on 2009-11-14
Hi,

I upgraded a Ubuntu system from 9.04 to 9.10 using the update manager. The upgrade seems to have been largely successful, but one problem is that the software centre won't run. What happens is that it opens the window for a couple of seconds, then it closes automatically. Any ideas about what is going wrong here and how to fix it?

Regards,
Steve

---

### Post by fancypiper on 2009-11-14
Open a terminal and run it from that.  Post the error messages here. Command:

/usr/bin/software-center

---

### Post by sjrooney on 2009-11-15
$ /usr/bin/software-center
/usr/lib/python2.6/dist-packages/gst-0.10/gst/__init__.py:193: Warning: cannot register existing type `GstRTPMux'
  from _gst import *

(software-center:3040): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

(software-center:3040): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/gstreamer-0.10/libgstschro.so: undefined symbol: schro_virt_frame_new_vert_downsample
/usr/lib/python2.6/dist-packages/gst-0.10/gst/__init__.py:193: Warning: cannot register existing type `GstFLVDemux'
  from _gst import *
/usr/lib/python2.6/dist-packages/gst-0.10/gst/__init__.py:193: Warning: g_once_init_leave: assertion `initialization_value != 0' failed
  from _gst import *

(software-center:3040): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed
/usr/lib/python2.6/dist-packages/gst-0.10/gst/__init__.py:193: Warning: cannot register existing type `GstValve'
  from _gst import *

(software-center:3040): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed
/usr/lib/python2.6/dist-packages/gst-0.10/gst/__init__.py:193: Warning: cannot register existing type `GstRTPSirenPay'
  from _gst import *

(software-center:3040): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstx264.so

Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.

(software-center:3034): GStreamer-WARNING **: adding type GstFourcc multiple times

(software-center:3034): GStreamer-WARNING **: adding type GstIntRange multiple times

(software-center:3034): GStreamer-WARNING **: adding type GstDoubleRange multiple times

(software-center:3034): GStreamer-WARNING **: adding type GstFractionRange multiple times

(software-center:3034): GStreamer-WARNING **: adding type GstValueList multiple times

(software-center:3034): GStreamer-WARNING **: adding type GstValueArray multiple times

(software-center:3034): GStreamer-WARNING **: adding type GstFraction multiple times

(software-center:3034): GStreamer-WARNING **: adding type gdouble multiple times

(software-center:3034): GStreamer-WARNING **: adding type gfloat multiple times

(software-center:3034): GStreamer-WARNING **: adding type gchararray multiple times

(software-center:3034): GStreamer-WARNING **: adding type gboolean multiple times

(software-center:3034): GStreamer-WARNING **: adding type GEnum multiple times

(software-center:3034): GStreamer-WARNING **: adding type GFlags multiple times

(software-center:3034): GStreamer-WARNING **: adding type gint multiple times

(software-center:3034): GStreamer-WARNING **: adding type gint64 multiple times

(software-center:3034): GStreamer-WARNING **: adding type glong multiple times

(software-center:3034): GStreamer-WARNING **: adding type guint multiple times

(software-center:3034): GStreamer-WARNING **: adding type guint64 multiple times

(software-center:3034): GStreamer-WARNING **: adding type gulong multiple times
/usr/share/software-center/softwarecenter/apt/aptcache.py:38: Warning: cannot register existing type `GstRTPMux'
  gtk.main_iteration()

(software-center:3064): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

(software-center:3064): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/gstreamer-0.10/libgstschro.so: undefined symbol: schro_virt_frame_new_vert_downsample
/usr/share/software-center/softwarecenter/apt/aptcache.py:38: Warning: cannot register existing type `GstFLVDemux'
  gtk.main_iteration()
/usr/share/software-center/softwarecenter/apt/aptcache.py:38: Warning: g_once_init_leave: assertion `initialization_value != 0' failed
  gtk.main_iteration()

(software-center:3064): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed
/usr/share/software-center/softwarecenter/apt/aptcache.py:38: Warning: cannot register existing type `GstValve'
  gtk.main_iteration()

(software-center:3064): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed
/usr/share/software-center/softwarecenter/apt/aptcache.py:38: Warning: cannot register existing type `GstRTPSirenPay'
  gtk.main_iteration()

(software-center:3064): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstx264.so

Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

---

### Post by fancypiper on 2009-11-15
First, I would try removing /usr/lib/gstreamer-0.10/libgstx264.so as the error message suggests:

In a terminal command:
sudo rm /usr/lib/gstreamer-0.10/libgstx264.so

If that doesn't fix it, then I would try removing and re-installing the software center.

Open a terminal and command:

sudo apt-get purge software-center
sudo apt-get install software-center

---

### Post by sjrooney on 2009-11-15
Thanks, that seemed to do the trick. wine got in the way to begin with so I removed wine, then removed software centre, re-installed software centre and finally re-installed wine and it all looks well.

Regards,
Steve

---

### Post by phoenixskywalker on 2009-11-25
Hi all. I also have a similar problem but my own displays this error:

Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 140, in __init__
    self.icons, datadir)
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 58, in __init__
    SoftwarePane.__init__(self, cache, db, icons, datadir)
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 92, in __init__
    self.datadir)
  File "/usr/share/software-center/softwarecenter/view/appdetailsview.py", line 102, in __init__
    self.aptd_client = client.AptClient()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/client.py", line 382, in __init__
    self._locale = "%s.%s" % locale.getdefaultlocale()
  File "/usr/lib/python2.6/locale.py", line 478, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.6/locale.py", line 410, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: en_NG


I am guessin it has something to do with my locale not been recognised or something. Thanks for your help.

---

