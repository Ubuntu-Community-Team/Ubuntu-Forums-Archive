---
title: "Problem with apt-get [install and upgrade]"
date: 2012-03-06
forum: Installation &amp; Upgrades
---

### Post by ark2 on 2012-03-06
Hello,
   I am trying to install openvpn using apt-get, but I get an error during the process [As far as I understand the issue is with unattended-updates, which I could not upgrade due to apt-get porblem :/]. I cannot upgrade, install, autoremove or purge anything else [which I need to do since /boot is full. For upgrading I did update before trying]....

Trace [on sudo apt-get autoremove]: 

0 upgraded, 0 newly installed, 79 to remove and 421 not upgraded.
35 not fully installed or removed.
Need to get 24.1 kB of archives.
After this operation, 140 MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main unattended-upgrades all 0.73ubuntu1 [24.1 kB]
Fetched 24.1 kB in 0s (31.2 kB/s)              
Preconfiguring packages ...
(Reading database ... 287206 files and directories currently installed.)
Removing flashplugin-downloader:i386 ...
Removing libasound2-plugins:i386 ...
Removing libpulse0:i386 ...
Removing libsndfile1:i386 ...
Removing libvorbisenc2:i386 ...
Removing libvorbis0a:i386 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 287174 files and directories currently installed.)
Preparing to replace unattended-upgrades 0.73ubuntu1 (using .../unattended-upgrades_0.73ubuntu1_all.deb) ...
Checking for running unattended-upgrades: 
Traceback (most recent call last):
  File "/usr/share/unattended-upgrades/unattended-upgrade-shutdown", line 27, in <module>
    import apt_pkg
ImportError: No module named apt_pkg
invoke-rc.d: initscript unattended-upgrades, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Checking for running unattended-upgrades: 
Traceback (most recent call last):
  File "/usr/share/unattended-upgrades/unattended-upgrade-shutdown", line 27, in <module>
    import apt_pkg
ImportError: No module named apt_pkg
invoke-rc.d: initscript unattended-upgrades, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/unattended-upgrades_0.73ubuntu1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
update-rc.d: warning: unattended-upgrades start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (none)
update-rc.d: warning: unattended-upgrades stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (0 6)
Checking for running unattended-upgrades: 
Traceback (most recent call last):
  File "/usr/share/unattended-upgrades/unattended-upgrade-shutdown", line 27, in <module>
    import apt_pkg
ImportError: No module named apt_pkg
invoke-rc.d: initscript unattended-upgrades, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/unattended-upgrades_0.73ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

       Maybe I missed something basic, but I would appreciate pointers on solving the issue.
Thanks

---

### Post by Lasall on 2012-03-06
Hi ark2,

you can try to temporarily disable unattended-upgrades:

Modify file **/etc/apt/apt.conf.d/10periodic** and change value to "0":
```

APT::Periodic::Unattended-Upgrade "0";

```

Did you made some changes to your python setup? Please show:
```

locate apt_pkg.so
ls -l /usr/bin/python

```


Kind regards

Lasall

---

### Post by ark2 on 2012-03-06
Hi,
   Thanks for the reply. The value of unattended-upgrade was already 0. The contents of the file are -

```
ark:~$ cat  /etc/apt/apt.conf.d/10periodic
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "0";

```When I run:
locate apt_pkg.so 
ls -l /usr/bin/python

Output:
```
ark:~$ locate apt_pkg.so
/usr/lib/pyshared/python2.6/apt_pkg.so
/usr/lib/pyshared/python2.7/apt_pkg.so
/usr/lib/python2.6/dist-packages/apt_pkg.so
/usr/lib/python2.7/dist-packages/apt_pkg.so

ark:~$ ls -l /usr/bin/python
lrwxrwxrwx 1 root root 9 2011-10-17 20:14 /usr/bin/python -> python2.7
```We update our Python compiler [custom changes], but did not within last week.

Note: Does having both 2.6 and 2.7 apt_pkg.so cause the conflict?

---

### Post by Lasall on 2012-03-06
> **ark2 said:**
> 
Note: Does having both 2.6 and 2.7 apt_pkg.so cause the conflict?

No. At the moment I do not have any idea what causes the problem :(.

Did you make a package for your custom build? If so, try to downgrade to Ubuntu version to see if error still occurs.

---

### Post by ark2 on 2012-03-06
Yes I did make a package for a custom build, however the package is installed on not just my machine. There are no issues on another machine(s). Although I will downgrade and see if it helps. [If so will post.]

[Update: No change, get same error.]

---

