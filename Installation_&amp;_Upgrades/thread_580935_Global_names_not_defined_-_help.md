---
title: "Global names not defined - help"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by JGT on 2007-10-19
I'm a beginning Linux user. I tried to update using Update Mamager, but my set-up insisted I was up to date. Another thread advised gksu "update-manager -c" . This produced the following output.

Can anyone please kindly explain how to proceed from here?


[PHP]john@john-desktop:~$ gksu "update-manager -c" 
warning: could not initiate dbus 
Loading simple Config module ... 
Creating backend ... 
Loading socket FrontEnd module ... 
Starting SCIM as daemon ... 
GTK Panel of SCIM 1.4.4 

extracting '/tmp/tmpEzFX41/gutsy.tar.gz' 
authenticate '/tmp/tmpEzFX41/gutsy.tar.gz' against '/tmp/tmpEzFX41/gutsy.tar.gz.gpg'  
could not send the dbus Inhibit signal: global name 'dbus' is not defined 
Traceback (most recent call last): 
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 914, in on_button_dist_upgrade_clicked 
    fetcher.run() 
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 178, in run 
    self.runDistUpgrader() 
  File "/usr/lib/python2.5/site-packages/UpdateManager/DistUpgradeFetcher.py", line 53, in runDistUpgrader 
    if os.getuid() != 0: 
NameError: global name 'os' is not defined  [/PHP]

---

### Post by anodari on 2007-10-19
I had the same problem, try to verify the software channels in the system/admin menu.

---

### Post by ekravche on 2007-10-20
> **anodari said:**
> I had the same problem, try to verify the software channels in the system/admin menu.

what do you mean? I get the same error...

---

### Post by ekravche on 2007-10-20
Found the solution. You'll need to modify DistUpgradeFetcher.py	by adding the following 2 lines to the top of this file

import os
import dbus

see [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/118862](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/118862) for more info

---

### Post by Palmyra on 2008-04-05
> **ekravche said:**
> Found the solution. You'll need to modify DistUpgradeFetcher.py	by adding the following 2 lines to the top of this file

import os
import dbus

see [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/118862](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/118862) for more info

Thanks; that worked for me.  Here's what you should do:

```


As the second error suggests, file "/usr/lib/python2.5/site-packages/UpdateManager/DistUpgradeFetcher.py" doesn't import the "os" object/package/whatever it's called. (Sorry, I only learned python by ear...)

I added "import os" at the top of that file and the update started.

(I still got the dbus problem, so I also added "import dbus" at the same file. Now I don't get either error.)

I'm trying to do the update now and hoping this will work...

```

If that's not plain English, do the following:

1.  gksudo gedit usr/lib/python2.5/site-packages/UpdateManager/DistUpgradeFetcher.py
2.  Enter password.
3.  Below the # symbols, but above everything else, add the following:

import os
import dbus

4.  Close out of gEdit.
5.  Try upgrading the distro again: gksu "update-manager -c" (you need the quote marks - usually, quote marks aren't added, but you need them here).

You don't have to know what the # symbols are used for (if you're curious, they are comment symbols in the programming world).

---

