---
title: "I can't upgrade"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by JGT on 2007-10-18
I use 7.04. I had a look on Update Manager but the PC insists it's up to date. 

Another thread said 

[PHP]gksu "update-manager -c"[/PHP]

so I tried that. Output below.

Please help!

Thanks

John

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
NameError: global name 'os' is not defined
[/PHP]

---

### Post by linuxwizard on 2007-10-18
Look over this and the release notes

[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by JGT on 2007-10-18
Thanks, though that was the first place I looked. I'll keep checking [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) too.

---

### Post by PartisanEntity on 2007-10-21
> **JGT said:**
> I use 7.04. I had a look on Update Manager but the PC insists it's up to date. 

Another thread said 

[PHP]gksu "update-manager -c"[/PHP]

so I tried that. Output below.

Please help!

Thanks

John

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
NameError: global name 'os' is not defined
[/PHP]

I get a similar error:

> warning: could not initiate dbus
extracting '/tmp/tmp1HKXkN/gutsy.tar.gz'
authenticate '/tmp/tmp1HKXkN/gutsy.tar.gz' against '/tmp/tmp1HKXkN/gutsy.tar.gz.gpg'
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by pierric on 2008-01-01
Hi !

I have the exact same issue ...

I launch the update manager with the -c option to be able to click on upgrade, I agree to the terms, it downloads 2 small files, and then, when I would expect to see the dialog with the different steps of the upgrade, it comes back to the main dialog, still with 'an upgrade is available'. In the console , I see:

extracting '/tmp/tmpBsNx_e/gutsy.tar.gz'
authenticate '/tmp/tmpBsNx_e/gutsy.tar.gz' against '/tmp/tmpBsNx_e/gutsy.tar.gz.gpg' 
could not send the dbus Inhibit signal: global name 'dbus' is not defined
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 914, in on_button_dist_upgrade_clicked
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 178, in run
    self.runDistUpgrader()
  File "/usr/lib/python2.5/site-packages/UpdateManager/DistUpgradeFetcher.py", line 53, in runDistUpgrader
    if os.getuid() != 0:
NameError: global name 'os' is not defined



Would be glad if someone could help...
Thanks,
Pierric.

---

### Post by pierric on 2008-01-01
Okay, just solved.... I promise I'd been googling for a while...

The answer is there:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/118862](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/118862)

You just have to add

import os
import dbus


at the beginning of the file /usr/lib/python2.5/site-packages/UpdateManager/DistUpgradeFetcher.py

It gets me to the next step, as soon as a I have a good bandwith I'll be able to check wether it goes to the end... but I suppose it will.

---

