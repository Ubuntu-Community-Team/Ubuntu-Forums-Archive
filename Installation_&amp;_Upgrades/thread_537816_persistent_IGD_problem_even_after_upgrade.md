---
title: "persistent IGD problem even after upgrade"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by steel_lady on 2007-08-29
I have this persistent problem and after reading similar posts, I still did not resolve it. I need it for various programs. It was makong problems for me for months with almost every installation and now after upgrading to feisty it is still a problem. Update manager is offering constantly to upgrade it but it is refused at the end. His is how my upgrade ended: 

Could not install 'linux-igd'
The upgrade has aborted. Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.package linux-igd is already installed and configured
E: /var/cache/apt/archives/linux-igd_0.cvs20060201-2ubuntu1_i386.deb: subprocess new pre-removal script returned error exit status 1

How can I reinstall it?

---

### Post by steel_lady on 2007-08-29
The complete error message:

Preparing to replace linux-igd 0.cvs20060201-1 (using .../linux-igd_0.cvs20060201-2ubuntu1_i386.deb) ...
External interface not specified in /etc/default/upnpd
invoke-rc.d: initscript upnpd, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
External interface not specified in /etc/default/upnpd
invoke-rc.d: initscript upnpd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/linux-igd_0.cvs20060201-2ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
External interface not specified in /etc/default/upnpd
invoke-rc.d: initscript upnpd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/linux-igd_0.cvs20060201-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing linux-igd (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.

---

### Post by steel_lady on 2007-08-29
when I edit the file


/etc/default/upnpd

removing comments to configure it, than it returns to the old message of 

dpkg: error processing /var/cache/apt/archives/linux-igd_0.cvs20060201-2ubuntu1_i386.deb (--unpack):
subprocess new pre-removal script returned error exit status 1


only

---

### Post by steel_lady on 2007-08-29
can somebody tell me how to remove this package on force since it can not be removed by synaptic?

---

### Post by steel_lady on 2007-08-29
I found this topic: 

[http://www.ubuntugeek.com/package-installation-error-and-solution.html](http://www.ubuntugeek.com/package-installation-error-and-solution.html)

but I still can not remove it because it complains:

sudo dpkg --remove --force-remove-reinstreq linux-igd
(Reading database ... 198333 files and directories currently installed.)
Removing linux-igd ...
Stopping Linux IGD Daemon: invoke-rc.d: initscript upnpd, action "stop" failed.
dpkg: error processing linux-igd (--remove):
 subprocess pre-removal script returned error exit status 1
Starting Linux IGD Daemon: upnpd.
Errors were encountered while processing:
 linux-igd

---

### Post by steel_lady on 2007-08-29
Thanx to user sipior, the problem is solved. He rewrote /etc/init.d/upnpd  and after that I was able to remove the package and reinstall.

---

### Post by uteck on 2007-12-24
I would be interested in what was changed in the init.d/upnp file as I am also having this problem.  I may play with it a bit more to see if I can find out what is causing the error, but ideally this info should be posted encase others are looking for it.

---

