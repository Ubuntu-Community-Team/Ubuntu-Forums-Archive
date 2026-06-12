---
title: "Permission denied when upgrading update-manager"
date: 2014-03-31
forum: Installation &amp; Upgrades
---

### Post by weiser on 2014-03-31
Hey I have some mythbuntu 12.04 installation and most did go well with the upgrade, but my frontend did not succes in the upgrade. It stopped with this error:

ion-moo dpkg $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up update-notifier-common (0.119ubuntu8.6) ...
/var/lib/dpkg/info/update-notifier-common.postinst: 25: /var/lib/dpkg/info/update-notifier-common.postinst: /usr/lib/update-notifier/package-data-downloader: Permission denied
dpkg: error processing update-notifier-common (--configure):
 subprocess installed post-installation script returned error exit status 126
Setting up update-manager-core (1:0.156.14.12) ...
/var/lib/dpkg/info/update-manager-core.postinst: 45: /var/lib/dpkg/info/update-manager-core.postinst: pycompile: Permission denied
dpkg: error processing update-manager-core (--configure):
 subprocess installed post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on update-notifier-common (>= 0.119ubuntu2); however:
  Package update-notifier-common is not configured yet.
dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.156.14.12); however:
  Package update-manager-core is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                                   Errors were encountered while processing:
 update-notifier-common
 update-manager-core
 flashplugin-installer
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)
ion-moo dpkg $ 


I'm not sure this is an error in the packages, but I don't know what else it could be.

Any help would be apriciated

thanks,

Kim

---

### Post by ian-weisser on 2014-04-03
> **weiser said:**
> 
Setting up update-notifier-common (0.119ubuntu8.6) ...
/var/lib/dpkg/info/update-notifier-common.postinst: 25: /var/lib/dpkg/info/update-notifier-common.postinst: /usr/lib/update-notifier/package-data-downloader: Permission denied
...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                                   

To me, it doesn't look like a *package* problem.
It looks like a *permission* problem.
And it looks like you have had it for quite a while.

1) Look at the permissions: ```
ls -l /usr/lib/update-notifier/
```

For reference, here's what mine look like:
```
$ ls -l /usr/lib/update-notifier/
total 80
-rwxr-xr-x 1 root root  2444 Nov 13 14:05 apt-cdrom-check
lrwxrwxrwx 1 root root    12 Nov 13 14:05 apt-check -> apt_check.py
-rwxr-xr-x 1 root root  7058 Nov 13 14:05 apt_check.py
-rwxr-xr-x 1 root root  4861 Nov 13 14:05 backend_helper.py
-rwxr-xr-x 1 root root   619 Nov 13 14:05 cddistupgrader
-rwxr-xr-x 1 root root  9688 Nov 13 14:05 distro-cd-updater
-rwxr-xr-x 1 root root  5568 Nov 13 14:05 local-avahi-notification
-rwxr-xr-x 1 root root 10168 Nov 13 14:05 package-data-downloader
-rwxr-xr-x 1 root root   358 Nov 13 14:05 package-system-locked
-rwxr-xr-x 1 root root  5580 Nov 13 14:05 system-crash-notification
-rwxr-xr-x 1 root root  2468 Nov 13 14:05 update-motd-fsck-at-reboot
-rwxr-xr-x 1 root root   115 Nov 13 14:05 update-motd-reboot-required
-rwxr-xr-x 1 root root  1186 Nov 13 14:05 update-motd-updates-available

```

If yours look different, you should be able to *sudo chmod* it back to the correct values.

2) If your permissions are correct, then let's try the package route. Delete the new version of the package, and force the package manager to re-download a fresh copy:
```
sudo apt-get clean update-notifier-common
sudo apt-get update
```

---

