---
title: "Picard - Error"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by faction918 on 2008-08-13
I have installed Picard form the Ubuntu repositories (apt-get). When I run Picard I get the following:

> 
faction918@FACTIONPCUBUNTU:~$ picard
Traceback (most recent call last):
  File "/usr/bin/picard", line 2, in <module>
    from picard.tagger import main; main('/usr/share/locale', True)
  File "/usr/lib/python2.5/site-packages/picard/tagger.py", line 56, in <module>
    from picard.browser.browser import BrowserIntegration
  File "/usr/lib/python2.5/site-packages/picard/browser/browser.py", line 20, in <module>
    from PyQt4 import QtCore, QtNetwork
ImportError: /usr/lib/libQtNetwork.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv


I get the same error when I compile it from scratch from their website.

I am presuming it is a dependency problem but does anyone know what package I need to install?

Thanks!

---

### Post by faction918 on 2008-08-17
Still Nothing... I am presuming this is not a common problem?

---

### Post by faction918 on 2008-08-21
Humm, Anyone :(? Any suggestions in any direction...

---

### Post by saanchi on 2008-11-10
i got the similar problem ...
it gives the following error...........

Traceback (most recent call last):
  File "/usr/bin/picard", line 2, in <module>
    from picard.tagger import main; main('/usr/share/locale', True)
  File "/var/lib/python-support/python2.5/picard/tagger.py", line 21, in <module>
    from PyQt4 import QtGui, QtCore
ImportError: /usr/lib/libQtGui.so.4: undefined symbol: _ZN23QCoreApplicationPrivate19checkReceiverThreadEP7QObject
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_picard.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/picard", line 2, in <module>
    from picard.tagger import main; main('/usr/share/locale', True)
  File "/var/lib/python-support/python2.5/picard/tagger.py", line 21, in <module>
    from PyQt4 import QtGui, QtCore
ImportError: /usr/lib/libQtGui.so.4: undefined symbol: _ZN23QCoreApplicationPrivate19checkReceiverThreadEP7QObject

---

### Post by euxneks on 2008-11-10
This is just a guess as when I install picard it works flawlessly, but make sure that you have **python-qt4** installed as well as **python-qt4-dev**..

```
sudo apt-get install python-qt4 python-qt4-dev
```

Hope that helps!

---

