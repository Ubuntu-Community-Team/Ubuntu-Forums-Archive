---
title: "&quot;fatal python error: pyeval_acquirethread null new thread state&quot; in logs of mod_wsgi"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by Voland on 2012-10-19
I've successfully upgraded to 12.10 release, but after reboot this line appeared in logs of Apache and Django:
```
Fri Oct 19 13:38:43 2012] [info] mod_wsgi (pid=6911): Shutdown requested 'fantomas'.
[Fri Oct 19 13:38:43 2012] [info] mod_wsgi (pid=6911): Stopping process 'fantomas'.
Fatal Python error: PyEval_AcquireThread: NULL new thread state
[Fri Oct 19 13:38:44 2012] [info] mod_wsgi (pid=7136): Attach interpreter ''.
[Fri Oct 19 13:38:44 2012] [info] mod_wsgi (pid=7137): Attach interpreter ''.
[Fri Oct 19 13:38:44 2012] [info] mod_wsgi (pid=7134): Attach interpreter ''.
[Fri Oct 19 13:38:44 2012] [info] mod_wsgi (pid=7135): Attach interpreter ''.
[Fri Oct 19 13:38:44 2012] [info] mod_wsgi (pid=7138): Attach interpreter ''.
[Fri Oct 19 13:39:18 2012] [info] mod_wsgi (pid=7135): Create interpreter 'fantomas|'.
```
So I have 200 error of Apache:
> The server encountered an internal error or misconfiguration and was unable to complete your request.
```
python manage.py runserver
``` works fine:
```
voland@django-dev:~/sandbox/fantomas$ python manage.py runserver
Validating models...

0 errors found
Django version 1.4.1, using settings 'fantomas.settings'
Development server is running at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

django.wsgi:
```
import os, sys

sys.path.append('/home/voland/sandbox')
sys.path.append('/home/voland/sandbox/fantomas')
os.environ['DJANGO_SETTINGS_MODULE'] = 'fantomas.settings'

import django.core.handlers.wsgi
application = django.core.handlers.wsgi.WSGIHandler()
```

Settings:
```
WSGIScriptAlias / /home/voland/sandbox/fantomas/deploy/django.wsgi
    
WSGIDaemonProcess fantomas maximum-requests=200 stack-size=524288
WSGIProcessGroup fantomas
```

What should I do to get my django back to work?

---

### Post by dino99 on 2012-10-19
have you some packages from ppa(s) ? maybe some conflicts

---

### Post by Voland on 2012-10-19
No, there are no packages from ppa.
I've solved problem with server misconfiguration, Django started to work, but I still have this errors in logs

---

### Post by KevinCole on 2012-12-20
> **Voland said:**
> I've solved problem with server misconfiguration, Django started to work, but I still have this errors in logs

What was the misconfiguration? I've just started to see the

```
PyEval_AcquireThread: NULL new thread state
```

error, but only occasionally.

---

