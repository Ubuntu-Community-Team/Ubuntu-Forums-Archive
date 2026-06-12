---
title: "aptitude errors"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by dimkal on 2007-07-19
Hello, I'm trying to remove few packages and I'm getting the bellow error. Running Ubuntu Feisty Fawn on amd64.

I've tried to look for information on similar errors, but had no luck finding anything.

Thanks,
-d

ubuntu:~>sudo aptitude
Password:
(Reading database ... 145524 files and directories currently installed.)
Removing python-crypto ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
File "/usr/bin/pycentral", line 3, in <module>
import fnmatch, glob, os, re, sys, time
ImportError: No module named fnmatch
dpkg: error processing python-crypto (--purge):
subprocess pre-removal script returned error exit status 1
'import site' failed; use -v for traceback
Traceback (most recent call last):
File "/usr/bin/pycentral", line 3, in <module>
import fnmatch, glob, os, re, sys, time
ImportError: No module named fnmatch
dpkg: error while cleaning up:
subprocess post-installation script returned error exit status 1
Removing python-imaging-tk ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
File "/usr/bin/pycentral", line 3, in <module>
import fnmatch, glob, os, re, sys, time
ImportError: No module named fnmatch
dpkg: error processing python-imaging-tk (--purge):
subprocess pre-removal script returned error exit status 1
Removing python-imaging ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
File "/usr/bin/pycentral", line 3, in <module>
import fnmatch, glob, os, re, sys, time
ImportError: No module named fnmatch
dpkg: error processing python-imaging (--purge):
subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
python-crypto
python-imaging-tk
python-imaging
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Press return to continue.

---

### Post by overdrank on 2007-07-19
> **dimkal said:**
> Hello, I'm trying to remove few packages and I'm getting the bellow error. Running Ubuntu Feisty Fawn on amd64.

I've tried to look for information on similar errors, but had no luck finding anything.

Thanks,
-d

ubuntu:~>sudo aptitude
Password:
(Reading database ... 145524 files and directories currently installed.)
Removing python-crypto ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
File "/usr/bin/pycentral", line 3, in <module>
import fnmatch, glob, os, re, sys, time
ImportError: No module named fnmatch
dpkg: error processing python-crypto (--purge):
subprocess pre-removal script returned error exit status 1
'import site' failed; use -v for traceback
Traceback (most recent call last):
File "/usr/bin/pycentral", line 3, in <module>
import fnmatch, glob, os, re, sys, time
ImportError: No module named fnmatch
dpkg: error while cleaning up:
subprocess post-installation script returned error exit status 1
Removing python-imaging-tk ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
File "/usr/bin/pycentral", line 3, in <module>
import fnmatch, glob, os, re, sys, time
ImportError: No module named fnmatch
dpkg: error processing python-imaging-tk (--purge):
subprocess pre-removal script returned error exit status 1
Removing python-imaging ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
File "/usr/bin/pycentral", line 3, in <module>
import fnmatch, glob, os, re, sys, time
ImportError: No module named fnmatch
dpkg: error processing python-imaging (--purge):
subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
python-crypto
python-imaging-tk
python-imaging
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Press return to continue.

Hi I am not well versed on aptitude but you can try this command 
```
sudo aptitude clean --purge-unused
```
I tried this on my system and it cleared all in aptitude. You can find more info on aptitude here
[https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide)
I hope this helps and please remember not to make the same post in different fourms ;-)

---

### Post by dimkal on 2007-07-19
thank you for your response,
 i've tried your suggestion without much luck,

ubuntu:~>sudo aptitude clean --purge-unused
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done

---

