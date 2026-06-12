---
title: "procps and udev errors when upgrading"
date: 2016-10-29
forum: Installation &amp; Upgrades
---

### Post by Lukas_Beran on 2016-10-29
Hi.
I am running Ubuntu Server 16.04.1 LTS and two days ago I met an outage of my webpages running on this server. So I rebooted the server and everything was fine. But when I tried to do an upgrade, I got error
```

root@vps:~# apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]
Setting up procps (2:3.3.10-4ubuntu2.1) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: script udev-orig: service udev already provided!
Job for systemd-sysctl.service failed because the control process exited with error code. See "systemctl status systemd-sysctl.service" and "journalctl -xe" for details.
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing package procps (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing package udev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 procps
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```



What can I do now?

I tried
```

root@vps:~# dpkg-reconfigure procps
/usr/sbin/dpkg-reconfigure: procps is broken or not fully installed

```

```

root@vps:~# apt install procps
Reading package lists... Done
Building dependency tree
Reading state information... Done
procps is already the newest version (2:3.3.10-4ubuntu2.1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]
Setting up procps (2:3.3.10-4ubuntu2.1) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: script udev-orig: service udev already provided!
Job for systemd-sysctl.service failed because the control process exited with error code. See "systemctl status systemd-sysctl.service" and "journalctl -xe" for details.
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing package procps (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing package udev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 procps
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

root@vps:~# apt --purge -f remove
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up procps (2:3.3.10-4ubuntu2.1) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: script udev-orig: service udev already provided!
Job for systemd-sysctl.service failed because the control process exited with error code. See "systemctl status systemd-sysctl.service" and "journalctl -xe" for details.
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing package procps (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing package udev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 procps
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

