---
title: "Action &quot;Restart&quot; failing"
date: 2012-02-27
forum: Installation &amp; Upgrades
---

### Post by misterfixit on 2012-02-27
This crap is getting really old - tried everything I can think of.  Only occurred since upgrade to Ubuntu 3.0.0-16 generic.  Ideas anyone???

Thanks in advance!  :-)

-----------------------------
acton "restart" failing:

dave@The-Mighty-Wurlitzer:~$ sudo aptitude full-upgrade
The following partially installed packages will be configured:
  collectd 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up collectd (4.10.1-2.1ubuntu4) ...
Restarting statistics collection and monitoring daemon: collectd
Not restarting collectd.
invoke-rc.d: initscript collectd, action "restart" failed.
dpkg: error processing collectd (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 collectd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up collectd (4.10.1-2.1ubuntu4) ...
Restarting statistics collection and monitoring daemon: collectdNot restarting collectd.
invoke-rc.d: initscript collectd, action "restart" failed.
dpkg: error processing collectd (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 collectd
                                         
dave@The-Mighty-Wurlitzer:~$

---

### Post by collisionystm on 2012-02-28
sudo invoke-rc.d collectd stop
sudo dpkg --configure collectd


try again

---

### Post by misterfixit on 2012-02-28
> **collisionystm said:**
> sudo invoke-rc.d collectd stop
sudo dpkg --configure collectd


try again


Nope:


dave@The-Mighty-Wurlitzer:~$ sudo dpkg --configure collectd
Setting up collectd (4.10.1-2.1ubuntu4) ...
Restarting statistics collection and monitoring daemon: collectd
Not restarting collectd.
invoke-rc.d: initscript collectd, action "restart" failed.
dpkg: error processing collectd (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 collectd


Any ideas?

Regards,
Dave

---

### Post by misterfixit on 2012-03-03
> **misterfixit said:**
> nope:


Dave@the-mighty-wurlitzer:~$ sudo dpkg --configure collectd
setting up collectd (4.10.1-2.1ubuntu4) ...
Restarting statistics collection and monitoring daemon: Collectd
not restarting collectd.
Invoke-rc.d: Initscript collectd, action "restart" failed.
Dpkg: Error processing collectd (--configure):
 Subprocess installed post-installation script returned error exit status 1
errors were encountered while processing:
 Collectd


any ideas?

Regards,
dave


bump???

---

