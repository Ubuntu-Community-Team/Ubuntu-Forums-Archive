---
title: "Can't uninstall vmware"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by tylerjroach on 2007-07-05
I couldn't get vmware to work and i deleted the /etc/vmware folder while i was trying to fix it. Now i can't uninstall vmware and it comes up with this error: 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 128209 files and directories currently installed.)
Removing vmware-player ...
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Could someone tell me how i could uninstall it a different way other than apt-get remove or if possible could someone send me their /etc/vmware folder over so it might recognize and be able to uninstall. Thank you.

---

### Post by destructchaos on 2007-07-05
try the '-f' parameter with aptitude

---

### Post by tylerjroach on 2007-07-05
Thank you for the response and i kept searching on google and found this link: [http://ubuntuforums.org/showthread.php?t=426198](http://ubuntuforums.org/showthread.php?t=426198) and now everything is fixed. thank you for your help though

---

