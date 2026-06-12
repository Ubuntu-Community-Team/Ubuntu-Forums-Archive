---
title: "adobe-flashplugin problems with firefox after upgrade from 10.04 to 12.04"
date: 2013-09-18
forum: Installation &amp; Upgrades
---

### Post by lindend on 2013-09-18
Trying to install any package on my system after the upgrade results in this error:



```
The following packages have unmet dependencies:
 firefox : Breaks: adobe-flashplugin (<= 11.1.102.63-0precise1) but 10.0.32.18-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Trying a 

```
sudo apt-get -f install
```

results in this error

```
The following packages will be REMOVED:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 10.4 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 329266 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin




```



sudo apt-get remove adobe-flashplugin

results in this error

```
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 10.4 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 329266 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)&#65279;
```

Finally tried this

```
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
(Reading database ... 329266 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin

```

Any ideas of how to fix this?

---

### Post by lindend on 2013-09-19
Solved the problem.  Had to manually edit /var/lib/dpkg/status and remove the offending package.  More details can be found at this link


[http://www.iasptk.com/ubuntu-debian/15825-ubuntu-fix-broken-package-best-solution](http://www.iasptk.com/ubuntu-debian/15825-ubuntu-fix-broken-package-best-solution)

---

