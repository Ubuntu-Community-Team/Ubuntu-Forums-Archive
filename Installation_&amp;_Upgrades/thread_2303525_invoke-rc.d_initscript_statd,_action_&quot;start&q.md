---
title: "invoke-rc.d: initscript statd, action &quot;start&quot; failed."
date: 2015-11-19
forum: Installation &amp; Upgrades
---

### Post by tluyet on 2015-11-19
I upgraded last night and got an error I haven't been able to resolve. I am new to ubuntu so I don't really know where to start:
```
apt-get install -f
```
returns:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-66 linux-headers-3.13.0-66-generic
  linux-image-3.13.0-66-generic linux-image-extra-3.13.0-66-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up nfs-common (1:1.2.8-6ubuntu1.2) ...
start: Job failed to start
invoke-rc.d: initscript statd, action "start" failed.
dpkg: error processing package nfs-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nfs-kernel-server:
 nfs-kernel-server depends on nfs-common (= 1:1.2.8-6ubuntu1.2); however:
  Package nfs-common is not configured yet.

dpkg: error processing package nfs-kernel-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 nfs-common
 nfs-kernel-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

syslog contains this:

```
Nov 19 09:36:46 COG kernel: [2430297.390704] init: statd pre-start process (3808) terminated with status 127
```

/var/log/upstart/statd.log contains this:

```
UPSTART_EVENTS =
sm-notify: error while loading shared libraries: libtirpc.so.1: cannot open shared object file: No such file or directory
```

can someone please tell me where I should be looking to resolve this?

---

### Post by ian-weisser on 2015-11-19
Reinstall the libtirpc1 package, and try again.

---

### Post by tluyet on 2015-11-19
```
apt-get install --reinstall libtirpc1
```

returns:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-66 linux-headers-3.13.0-66-generic
  linux-image-3.13.0-66-generic linux-image-extra-3.13.0-66-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 71.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu/ trusty/main libtirpc1 amd64 0.2.2-5ubuntu2 [71.3 kB]
Fetched 71.3 kB in 0s (115 kB/s)
(Reading database ... 220670 files and directories currently installed.)
Preparing to unpack .../libtirpc1_0.2.2-5ubuntu2_amd64.deb ...
Unpacking libtirpc1:amd64 (0.2.2-5ubuntu2) over (0.2.2-5ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libtirpc1:amd64 (0.2.2-5ubuntu2) ...
Setting up nfs-common (1:1.2.8-6ubuntu1.2) ...
start: Job failed to start
invoke-rc.d: initscript statd, action "start" failed.
dpkg: error processing package nfs-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Errors were encountered while processing:
 nfs-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

statd.log:

```
UPSTART_EVENTS =
sm-notify: error while loading shared libraries: libgssglue.so.1: cannot open shared object file: No such file or directory
```

syslog unchanged

---

### Post by ian-weisser on 2015-11-19
Okay, now reinstall libgssglue1, and try again.
Reinstall each mising library as you discover them.

---

### Post by tluyet on 2015-11-19
[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1841707_1.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1841707") 				 				 					 						 	[**[COLOR=#DD4814][B]ian-weisser**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1841707") thank you so much you put me on the right track after reinstalling 
libtirpc1 I needed to reinstall libgssglue1 and it worked.

---

