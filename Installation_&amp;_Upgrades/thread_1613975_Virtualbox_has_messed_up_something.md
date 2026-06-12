---
title: "Virtualbox has messed up something"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by taavi on 2010-11-05
Hi, I installed Virtualbox back in 10.04 and now have upgraded to 10.10. I used vbox repo for that:
```

taavi@hyperion:~$ cat /etc/apt/sources.list.d/virtualbox.list
deb http://download.virtualbox.org/virtualbox/debian maverick non-free
```

But now something has messed up poor old dpkg brains cause when I try to run apt-get upgrade manually, outcome is very messy. I want to get rid of those warnings and errors. If their packages or metainfo is messed up, I can live with it, but leave dpkg alone!

```

taavi@hyperion:~/apps$ sudo aptitude upgrade
The following partially installed packages will be configured:
  virtualbox-3.2 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
warning, in file '/var/lib/dpkg/status' near line 49781 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 49782 package 'virtualbox-3.1':
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 49806 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 49807 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
Setting up virtualbox-3.2 (3.2.10-66523~Ubuntu~maverick) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
warning, in file '/var/lib/dpkg/status' near line 49781 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 49782 package 'virtualbox-3.1':
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 49806 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 49807 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
 * Stopping VirtualBox kernel modules                                                                                                                   *  done.
 * Starting VirtualBox kernel modules                                                                                                                   *  done.
.: 132: Can't open /etc/rc.status
invoke-rc.d: initscript vboxweb-service, action "start" failed.
dpkg: error processing virtualbox-3.2 (--configure):
 subprocess installed post-installation script returned error exit status 127
Processing triggers for python-central ...
Errors were encountered while processing:
 virtualbox-3.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
warning, in file '/var/lib/dpkg/status' near line 49781 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 49782 package 'virtualbox-3.1':
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 49806 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 49807 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
Setting up virtualbox-3.2 (3.2.10-66523~Ubuntu~maverick) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
warning, in file '/var/lib/dpkg/status' near line 49781 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 49782 package 'virtualbox-3.1':
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 49806 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 49807 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
 * Stopping VirtualBox kernel modules                                                                                                                   *  done.
 * Starting VirtualBox kernel modules                                                                                                                   *  done.
.: 132: Can't open /etc/rc.status
invoke-rc.d: initscript vboxweb-service, action "start" failed.
dpkg: error processing virtualbox-3.2 (--configure):
 subprocess installed post-installation script returned error exit status 127
Processing triggers for python-central ...
Errors were encountered while processing:
 virtualbox-3.2
                                         

```

---

### Post by taavi on 2010-11-05
Ooh it's a dupe: [http://art.ubuntuforums.org/showthread.php?t=1591201](http://art.ubuntuforums.org/showthread.php?t=1591201)

---

