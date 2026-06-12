---
title: "kde apps crashing on startup error in .xsession-errors"
date: 2009-06-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jithin1987 on 2009-06-26
In karmic korganizer deamon, update-notifier-kde are not running. 
I can see these in xsession-errors. 


Could not open library /usr/bin/knotify4: Cannot load library /usr/lib/libkdeinit4_knotify4.so: (/usr/lib/libkdeinit4_knotify4.so: cannot open shared object file: No such file or directory)


Could not open library /usr/bin/korgac: Cannot load library /usr/lib/libkdeinit4_korgac.so: (/usr/lib/libkdeinit4_korgac.so: cannot open shared object file: No such file or directory)
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kblueplugd.so
Could not open library /usr/bin/kblueplugd: Cannot load library /usr/lib/libkdeinit4_kblueplugd.so: (/usr/lib/libkdeinit4_kblueplugd.so: cannot open shared object file: No such file or directory)



<unknown program name>(5326)/: Communication problem with  "korgac" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." "

Traceback (most recent call last):
  File "/usr/bin/update-notifier-kde", line 26, in <module>
    from PyQt4.QtCore import *
ImportError: No module named QtCore


How can I get these missing libraries in karmic?

---

