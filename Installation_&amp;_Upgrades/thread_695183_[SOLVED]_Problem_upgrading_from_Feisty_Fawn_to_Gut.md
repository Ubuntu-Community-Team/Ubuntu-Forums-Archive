---
title: "[SOLVED] Problem upgrading from Feisty Fawn to Gutsy Gibbon &amp;quot;could not initialize dbu"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by RyGuy on 2008-02-12
I usually can find the solutions to my problems online, so this is my first post.  I'm trying to upgrade to Gutsy Gibbon, but the upgrade tool keeps failing.  Here is the output from my terminal.
```

% sudo update-manager -c -d
warning: could not initiate dbus
extracting '/tmp/tmpi3KpkE/gutsy.tar.gz'
authenticate '/tmp/tmpi3KpkE/gutsy.tar.gz' against '/tmp/tmpi3KpkE/gutsy.tar.gz.gpg' 
could not send the dbus Inhibit signal: global name 'dbus' is not defined
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 914, in on_button_dist_upgrade_clicked
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 178, in run
    self.runDistUpgrader()
  File "/usr/lib/python2.5/site-packages/UpdateManager/DistUpgradeFetcher.py", line 53, in runDistUpgrader
    if os.getuid() != 0:
NameError: global name 'os' is not defined

```
in between where it says that it could not initiate dbus and when it starts extracting I have to click to upgrade in the GUI (I'm sure everyone is familiar with this).

I have seen many people with similar problems, but I haven't found any solutions.  Thanks in advance for your help.

 - Ryan

---

### Post by Partyboi2 on 2008-02-12
There seems to be a solution [here]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/118862")
Hopefully it will work for you :)

---

### Post by RyGuy on 2008-02-13
Awesome!  For those interested, I added the line

import os

to the file

/usr/lib/python2.5/site-packages/UpdateManager/DistUpgradeFetcher.py

and then I was able to upgrade successfully.  Thanks Partyboi2.  I'll try to figure out how to thank you in the system as well. =-)

 - Ryan

---

