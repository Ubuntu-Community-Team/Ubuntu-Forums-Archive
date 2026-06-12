---
title: "Unable to update to Gutsy"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by waltn on 2007-10-21
I have tried the System>Administration>Update Manager route and it does not find the update. From another thread in these forums, I tried ":sudo update-manager --check-dist-upgrades" from the command line and got the following before the GUI started:

```
walt@walt-ubuntu:[~]$ sudo update-manager --check-dist-upgrades
Password:
warning: could not initiate dbus
```

When the GUI runs, it does find the Gutsy update. When I click the Update button, the following occurs:

```
extracting '/tmp/tmpezTQU2/gutsy.tar.gz'
authenticate '/tmp/tmpezTQU2/gutsy.tar.gz' against '/tmp/tmpezTQU2/gutsy.tar.gz.gpg' 
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

At this point, the update hangs. Does anyone have any suggestions?

Thanks,
Walt

---

### Post by Pumalite on 2007-10-21
Have you tried the official method?:
[http://ubuntuforums.org/showthread.php?t=286599](http://ubuntuforums.org/showthread.php?t=286599)

---

### Post by waltn on 2007-10-21
Yes...with exactly the same results.

Thanks,
Walt

---

### Post by Pumalite on 2007-10-21
Consider this:

[http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)

---

### Post by waltn on 2007-10-22
Pumalite,

Other than trying a clean install (which I'd rather not do at this point), nothing suggested in the link works.

I an concerned by the references to **dbus**...does anyone know what this means?

Walt

---

### Post by Pumalite on 2007-10-22
I did a clean install in three machines without any problems. A clean install is always better. You can save /home and your data. Why don't you post your specs, so I can give you more precise instructions. Sorry, I don't have an answer for 'dbus'.

---

