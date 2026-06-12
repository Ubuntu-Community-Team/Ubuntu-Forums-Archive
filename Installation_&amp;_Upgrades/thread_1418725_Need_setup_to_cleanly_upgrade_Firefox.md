---
title: "Need setup to cleanly upgrade Firefox"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2010-02-28
I ran the ubuntuzilla.py script which went fine until I got the following.

I can only launch FF now in safe-mode from the commandline. Would really like to get these issues sorted out.

```
Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg-divert: rename involves overwriting `/usr/bin/firefox.ubuntu' with
  different file `/usr/bin/firefox', not allowed
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Traceback (most recent call last):
  File "/home/rj/bin/ubuntuzilla.py", line 1331, in <module>
    bs.start()
  File "/home/rj/bin/ubuntuzilla.py", line 311, in start
    fi.start()
  File "/home/rj/bin/ubuntuzilla.py", line 354, in start
    self.install()
  File "/home/rj/bin/ubuntuzilla.py", line 781, in install
    self.linkLauncher()
  File "/home/rj/bin/ubuntuzilla.py", line 984, in linkLauncher
    self.util.execSystemCommand(executionstring="sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox")
  File "/home/rj/bin/ubuntuzilla.py", line 154, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, http://ubuntuzilla.sourceforge.net/
ubuntuzilla.py  1.68s user 0.44s system 2% cpu 1:32.39 total
```

---

### Post by watchpocket on 2010-03-01
I solved this problem with:

```
ubuntuzilla.py -a remove -p firefox 
``` Reason I posted question is, I'd run the above command once, but when it asked:

"Are you sure you want to disable automatic update checking for the official Mozilla build of Firefox?" 

 I got worried the new install wouldn't check for the updates, so I answered "No".

Wrong thing to do.  It won't fully un-install unless you answer yes to that question.
So I ran the remove command again, answering yes, & only then did it do a full un-install so that I could successfully re-install.

---

### Post by nanotube on 2010-03-01
Hi,

you must have looked at some outdated tutorial on the internet. ubuntuzilla is now a ppa with actual firefox/thunderbird/seamonkey packages in it, so there's no need to deal with an installer script.

the latest info is always on [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

