---
title: "Fluendo Media Center"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by canadianwriterman on 2010-04-08
Anyone else try to install the new Fluendo Media Centre on Lucid? I get python errors and it won't open.

---

### Post by thatguruguy on 2010-04-08
I use moovida, the free alternative.  I've had no problems with it.  What problems are you having, exactly?

---

### Post by canadianwriterman on 2010-04-08
When I try to open the Media Center, it won't open. I get some sort of a Python script error. Here's the terminal output:

```
stephen@stephen-laptop:~$ fluoh
Launcher core version: 1.0.9
Current core version: 1.0.9

(moovida:2616): GStreamer-WARNING **: External plugin loader failed. This most likely means that the plugin loader helper binary was not found or could not be run. If you are running an uninstalled GStreamer setup, you might need to update your gst-uninstalled script so that the GST_PLUGIN_SCANNER environment variable gets set.

(moovida:2616): GStreamer-WARNING **: Failed to load plugin '/opt/fluoh/lib/gstreamer-0.10/libgstpango.so': /usr/lib/libpangoft2-1.0.so.0: undefined symbol: g_realloc_n

(moovida:2616): GStreamer-WARNING **: Failed to load plugin '/opt/fluoh/lib/gstreamer-0.10/libgstgconfelements.so': /usr/lib/libgconf-2.so.4: undefined symbol: g_malloc0_n

(moovida:2616): GStreamer-WARNING **: Failed to load plugin '/opt/fluoh/lib/gstreamer-0.10/libgstpango.so': /usr/lib/libpangoft2-1.0.so.0: undefined symbol: g_realloc_n

(moovida:2616): GStreamer-WARNING **: Failed to load plugin '/opt/fluoh/lib/gstreamer-0.10/libgstgconfelements.so': /usr/lib/libgconf-2.so.4: undefined symbol: g_malloc0_n
Initializing fluendo modules
Initializing fluendo modules
WARN  MainThread      application                 Apr 08 17:50:04  An Traceback occurred and got saved to /tmp/elisa_ipz6Lh.txt (elisa/core/application.py:342)
<type 'exceptions.ImportError'>
Python 2.5.5: /opt/fluoh/bin/python
Thu Apr  8 17:50:04 2010

A problem occurred in a Python script.  Here is the sequence of
function calls leading up to the error, in the order they occurred.
<type 'exceptions.ImportError'>: could not import gtk.gdk
    __class__ = <type 'exceptions.ImportError'>
    __delattr__ = <method-wrapper '__delattr__' of exceptions.ImportError object at 0x92bc50c>
    __dict__ = {}
    __doc__ = "Import can't find module, or can't find name in module."
    __getattribute__ = <method-wrapper '__getattribute__' of exceptions.ImportError object at 0x92bc50c>
    __getitem__ = <method-wrapper '__getitem__' of exceptions.ImportError object at 0x92bc50c>
    __getslice__ = <method-wrapper '__getslice__' of exceptions.ImportError object at 0x92bc50c>
    __hash__ = <method-wrapper '__hash__' of exceptions.ImportError object at 0x92bc50c>
    __init__ = <method-wrapper '__init__' of exceptions.ImportError object at 0x92bc50c>
    __new__ = <built-in method __new__ of type object at 0xc10400>
    __reduce__ = <built-in method __reduce__ of exceptions.ImportError object at 0x92bc50c>
    __reduce_ex__ = <built-in method __reduce_ex__ of exceptions.ImportError object at 0x92bc50c>
    __repr__ = <method-wrapper '__repr__' of exceptions.ImportError object at 0x92bc50c>
    __setattr__ = <method-wrapper '__setattr__' of exceptions.ImportError object at 0x92bc50c>
    __setstate__ = <built-in method __setstate__ of exceptions.ImportError object at 0x92bc50c>
    __str__ = <method-wrapper '__str__' of exceptions.ImportError object at 0x92bc50c>
    args = ('could not import gtk.gdk',)
    message = 'could not import gtk.gdk'

The above is a description of an error in a Python program.  Here is
the original traceback:

ImportError: could not import gtk.gdk


Fatal Python error: Can't initialize module pgm.imaging.
Aborted (core dumped)
```

---

