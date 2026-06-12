---
title: "An unhandlable error occured"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by Tyler09 on 2012-01-11
I was attempting to install openoffice on my Ubuntu 11.10 OS and i followed the process on this site:
[http://www.fossapps.com/2011/06/26/how-to-install-open-office-for-ubuntu-11-04/](http://www.fossapps.com/2011/06/26/how-to-install-open-office-for-ubuntu-11-04/)
And afterwards things became a mess, now when i try to install other upgrades or other programs i get errors. A specific error from trying to install python is:
 An unhandlable error occured
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.
Details:

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the libreoffice-common package. This might mean you need to manually fix this package.

Not sure what to do thanks for your help.

---

### Post by Buntumatic on 2012-01-11
I do not agree with reasoning Libreoffice being inferior. In actuality, Libreoffice is being developed actively and last time I checked Openoffice development was stalled.
As of today, Jan 2012 I'd recommend using Libreoffice.

---

### Post by arubislander on 2012-01-11
+1

If you are at all able to uninstall OpenOffice I would try to do so. As you've seen, installing it is not worth the hassle, and I would stick to LibreOffice unless you are looking for specific functionality that is only available in OpenOffice (I wouldn't know what that would be, but I guess it is possible that such exists)

---

### Post by Buntumatic on 2012-01-11
I stand yo be corrected, but didn't LibreOffice fork when OpenOffice stalled and since then LibreOffice has been moving forward. Latest OpenOffice seems still be 3.3.0, while LibreOffice is at 3.5 and live. Considering this it's unlikely OpenOffice has a feature LibreOffice has not.

---

### Post by Tyler09 on 2012-01-11
Ok well i cant uninstall or install anything because  i get that same error.

---

### Post by Tyler09 on 2012-01-14
Soo does anyone have any other suggestions?

---

### Post by Hagar Delest on 2012-01-14
You can try to install Synaptic and use it to remove the packages. But if nothing works anymore, you should check the apt-get help to fix such situation.

---

### Post by Buntumatic on 2012-01-14
When you tried to install OpenOffice, did it pull in something with it?
Right now it looks like your Python install may be borked.
What is the current active version of python in your system?

---

### Post by Tyler09 on 2012-01-16
I just followed the steps on that site, and i guess i'm not sure where to go to look up what version of python.

---

### Post by Tyler09 on 2012-01-16
I typed in sudo apt-get -f install, and it works now with libreoffice removed and open office seems to work fine

---

