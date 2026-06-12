---
title: "Automated Ubuntu update script."
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by serial# on 2011-09-01
Run in terminal:
```


wget http://updateubuntu.webs.com/Update.py && chmod a+x Update.py && ./Update.py
```

---

### Post by philinux on 2011-09-01
I'm not sure anyone should just run this script blindly. They may not want to do a distribution upgrade without backing up first etc etc.

```
#!/usr/bin/env python

import subprocess
import time
import sys
def banner():
    print '\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n'
    print '                       -+-+-+-+-+-+-+-+-+-+-+-'
    print '                       -+-  Ubuntu Update  -+-'
    print '                       -+-+-+-+-+-+-+-+-+-+-+-'
    print '                              :Serial:'
    print '                               ver 1.0'
    print '\n'
def CLS():
    print '\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n'
if __name__ == "__main__":
    banner()
    time.sleep(2)
    print '1 - Update'
    print '2 - Update Script'
    print '3 - Exit'
    print '\n'
    option = input("> ")
    if option == 1:
        CLS()
        print '> Checking internet connection....'
        if subprocess.Popen("ping -q -c 1 -w 2 www.google.com > /dev/null",shell=True).wait() == 0:
            CLS()
            print '> Updating....'
            if subprocess.Popen("sudo apt-get update && sudo **[COLOR="Red"]apt-get -y dist-upgrade[/COLOR]** && sudo apt-get autoremove -y && sudo apt-get -y autoclean",shell=True).wait() == 0:
               print '> Update successful'
            else:
               print'> Update failed'
        else:
            print '> No internet connection'
            print'> Goodbye'
            sys.exit()
    if option == 3:
           print'> Goodbye'
           sys.exit()
    if option == 2:
           if subprocess.Popen("rm -f -r Update.py && wget http://updateubuntu.webs.com/Update.py && chmod a+x Update.py && ./Update.py",shell=True).wait() == 0:
               print '> Update successful'
```

---

### Post by serial# on 2011-09-01
Well put.....
Updated:
```
#!/usr/bin/env python

import subprocess
import time
import sys
def banner():
    print '\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n'
    print '                       -+-+-+-+-+-+-+-+-+-+-+-'
    print '                       -+-  Ubuntu Update  -+-'
    print '                       -+-+-+-+-+-+-+-+-+-+-+-'
    print '                              :Serial:'
    print '                               ver 1.0'
    print '\n'
def CLS():
    print '\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n'
if __name__ == "__main__":
    banner()
    time.sleep(2)
    print '1 - Update'
    print '2 - Dist-Upgrade'
    print '3 - Update Script'
    print '4 - Exit'
    print '\n'
    option = input("> ")
    if option == 1:
        CLS()
        print '> Checking internet connection....'
        if subprocess.Popen("ping -q -c 1 -w 2 www.google.com > /dev/null",shell=True).wait() == 0:
            CLS()
            print '> Updating....'
            if subprocess.Popen("sudo apt-get update && sudo apt-get autoremove -y && sudo apt-get -y autoclean",shell=True).wait() == 0:
               print '> Update successful'
            else:
               print'> Update failed'
        else:
            print '> No internet connection'
            print'> Goodbye'
            sys.exit()
    if option == 4:
           print'> Goodbye'
           sys.exit()
    if option == 3:
           if subprocess.Popen("rm -f -r Update.py && wget http://updateubuntu.webs.com/Update.py && chmod a+x Update.py && ./Update.py",shell=True).wait() == 0:
               print '> Update successful'
    if option == 2:
        CLS()
        if subprocess.Popen("sudo apt-get -y dist-upgrade",shell=True).wait() == 0:
            print '> Update successful'
        else:
               print '> Dist-upgrade failed'

```Added the option for dist-upgrade. And updated it as well on the site.

---

