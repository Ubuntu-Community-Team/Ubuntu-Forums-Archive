---
title: "Trouble with udev and rsyslog after upgrade"
date: 2013-03-27
forum: Installation &amp; Upgrades
---

### Post by TomB19 on 2013-03-27
Ubuntu 12.04

udev went south first and then, while upgrading some other stuff to try to fix udev, rsyslog has also gone south.

```
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
start: Job is already running: rsyslog
invoke-rc.d: initscript rsyslog, action "restart" failed.
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up udev (175-0ubuntu9.3) ...
start: Job is already running: udev
invoke-rc.d: initscript udev, action "restart" failed.
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 rsyslog
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Does this mean I have to tweak apparmor in order to upgrade udev?


This is from dpkg.log, showing the status of rsyslog.  rsyslog also has some apparmor controls so this could be a similar problem.

```
2013-03-25 21:18:46 upgrade rsyslog 5.8.6-1ubuntu8 5.8.6-1ubuntu8.1
2013-03-25 21:18:46 status half-configured rsyslog 5.8.6-1ubuntu8
2013-03-25 21:18:46 status unpacked rsyslog 5.8.6-1ubuntu8
2013-03-25 21:18:46 status half-installed rsyslog 5.8.6-1ubuntu8
2013-03-25 21:18:46 status triggers-pending ureadahead 0.100.0-12
2013-03-25 21:18:46 status half-installed rsyslog 5.8.6-1ubuntu8
2013-03-25 21:18:46 status triggers-pending ureadahead 0.100.0-12
2013-03-25 21:18:46 status triggers-pending man-db 2.6.1-2ubuntu1
2013-03-25 21:18:46 status half-installed rsyslog 5.8.6-1ubuntu8
2013-03-25 21:18:46 status half-installed rsyslog 5.8.6-1ubuntu8
2013-03-25 21:18:46 status unpacked rsyslog 5.8.6-1ubuntu8.1
2013-03-25 21:18:46 status unpacked rsyslog 5.8.6-1ubuntu8.1

```


Any hint as to which direction to look would be appreciated.  I mostly opened this thread because I could not find anything relevant when searching for these issues.  If I can manage to sort this out, I hope it will be of help to someone else.

---

### Post by TomB19 on 2013-03-27
I did a '/etc/init.d/apparmor teardown' and then remove/install of rsyslog.  It was not effective.  I'm not sure if this rules out apparmor now, or not, but I suspect it does.

---

### Post by TomB19 on 2013-03-30
I tried "apt-get upgrade -f", "dpkg --configure -a", and a few other things.

From there, I gave up and installed 12.10 yesterday.  After all, it's been a few months since I've been forced to reinstall.  Once installed, I did an update/upgrade and now cups is hooped.

```
Processing triggers for cups ...
start: Job is already running: cups
invoke-rc.d: initscript cups, action "start" failed.
dpkg: error processing cups (--unpack):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 cups
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I can live without cups.  I'll just boot into Windows 7 to do any printing I might need.  In the mean time, I will refrain from updating anything at all so I can limp this along for another few months before the next forced re-install install.  I'm glad Windows is stable.

---

### Post by TomB19 on 2013-03-30
One more post on this....

I was unable to install anything, because of the cups error.  In the past, I've been able to live with the udev/rsyslog error but I had all the software I needed, already installed by the time those errors showed up.  This time, I still had software that needed installing.

I've done one more re-install and went back to ubuntu 12.04.  So far, it is still working.

I've been told it's my hardware countless times.  It isn't.  This system works fine with Windows 7 but, far more telling of where it's at is the fact that my other machines go sour at about the same time.

The kiss of death is clearly KDE.  I used KDE for years and loved it, still do, but I have yet to find a distribution that will remain stable with KDE installed.  For what it's worth, I've found ubuntu with kde-standard far more stable than kubuntu.  Neither is good enough, though.  Ubuntu, without KDE, seems to be pretty stable.  Adding KDE into the mix has always been a system killer for me.

---

