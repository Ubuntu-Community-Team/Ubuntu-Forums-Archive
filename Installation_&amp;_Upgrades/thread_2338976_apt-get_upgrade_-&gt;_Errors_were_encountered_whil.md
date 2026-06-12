---
title: "apt-get upgrade -&gt; Errors were encountered while processing"
date: 2016-10-03
forum: Installation &amp; Upgrades
---

### Post by bmorgenthaler on 2016-10-03
Running 16.04LTS and logged into my server and saw a system reboot needed to happen and updates needed to be applied.  Rebooted the system then tried to apply the updates
```
sudo apt-get update
sudo apt-get upgrade
```
Now I'm stuck with the following:```
Errors were encountered while processing:
 udev
 initscripts
 ifupdown
 dbus
 rpcbind
 nfs-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

It all seems to start with the udev upgrade to 229-4ubuntu10:```
Setting up udev (229-4ubuntu10) ...
addgroup: The group `input' already exists as a system group. Exiting.
update-initramfs: deferring update (trigger activated)
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
insserv: warning: script 'screen-cleanup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `screen-cleanup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `screen-cleanup'
insserv: warning: script 'dsmc' missing LSB tags and overrides
insserv: warning: script 'vmware-tools' missing LSB tags and overrides
insserv: There is a loop between service monit and dsmc if stopped
insserv:  loop involving service dsmc at depth 2
insserv:  loop involving service monit at depth 1
insserv: Stopping dsmc depends on monit and therefore on system facility `$all' which can not be true!
insserv: Stopping vmware-tools depends on monit and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package udev (--configure):
 subprocess installed post-installation script returned error exit status 1
```

Any ideas?

---

### Post by bmorgenthaler on 2016-10-03
Okay figured it out.  There is some conflict with monit on my system.  I removed monit, all packages updated succesfully AND crashplan started working again.

---

### Post by ian-weisser on 2016-10-03
Glad to see you figured it out.

---

