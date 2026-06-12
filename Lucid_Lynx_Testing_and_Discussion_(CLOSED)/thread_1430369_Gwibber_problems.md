---
title: "Gwibber problems"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Matticus on 2010-03-15
I am not sure if this is an LL issue, a gwibber only issue or just me being a fool. I didn't find anything on google specifically about it, which is what leads me to believe its to do with LL, or at least this newest version of gwibber.
 
Basically I have never tried gwibber before, but I thought I would see what it is. I added and authorised my facebook account, then I used the little applet for gwibber that's already in the top panel to post a new status and it went well.

Then I thought that I will never use this as I never use facebook really, so I removed the account. But now if I click on the "Gwibber social client" from the applications menu, after clicking close on the "social accounts" window, it comes up with the "social broadcast messages" window, which still shows all the stuff from facebook that it downloaded. I can't do anything with it, or receive any new updates. If I do try and do anything with it gwibber crashes.

But it is there, I have completely removed gwibber, restarted, reinstalled. And its still there.

Any ideas, or am I just being massively stupid and not understanding how gwibber works.

Edit: After more searching, seems you just cannot remove old stream. Not sure how its still there after I reinstalled it though. Might as well delete this post as it has nothing to do with LL, or gwibber really, its just a silly lack of options.

---

### Post by VMC on 2010-03-18
I just tried Gwibber and also have errors. I just recently signed on with Facebook and have heard you need Gwibber setup for it to work.

At any rate when I push Applications>Internet>Gwibber Social Client
nothing happens.

Start Gwibber from a terminal and here is the error messages:
```
** (gwibber:1617): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:1617): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:1617): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
** Message: secret service operation failed: The name org.freedesktop.secrets was not provided by any .service files
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 50, in <module>
    from gwibber import client
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 3, in <module>
    import gtk, gobject, gwui, util, resources, actions, json, gconf
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 2, in <module>
    import os, json, urlparse, resources, util
  File "/usr/lib/python2.6/dist-packages/gwibber/util.py", line 2, in <module>
    from microblog.util.couch import RecordMonitor
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/util/couch.py", line 4, in <module>
    import desktopcouch, pycurl, oauth, threading, urllib, re, json
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 20, in <module>
    from desktopcouch.start_local_couchdb import process_is_couchdb, read_pidfile
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 38, in <module>
    from desktopcouch import local_files
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 277, in <module>
    xdg_base_dirs.save_config_path("desktop-couch"))
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 231, in __init__
    self.configuration = _Configuration(self)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 90, in __init__
    {'desktopcouch': 'basic'})
**gnomekeyring.IOError**

```

I'll have a look inside those line# errors and see if anything I can understand.

Edit: That gnomekeyring error is the key :)

---

### Post by ranch hand on 2010-03-19
For those interested, read the 3-17-10 post here;

[http://blog.qa.ubuntu.com/](http://blog.qa.ubuntu.com/)

---

