---
title: "unable to open '/usr/lib/systemd/system/failsafe-x.service.dpkg-new': No such file or"
date: 2024-11-04
forum: Installation &amp; Upgrades
---

### Post by mark-galeck on 2024-11-04
Hello, I have the latest Ubuntu and I always upgrade when it suggests to do so.
Recently when I use

$sudo apt upgrade

I get this error:
E: Sub-process /usr/bin/dpkg returned an error code (1)

I asked ChatGPT o1 for suggestions, none of which proved to work, except, it looked like the package xdiagnose could be the ultimate culprit. So I uninstalled it and when I attempted to reinstall, I get this: 

dpkg: error processing archive /var/cache/apt/archives/xdiagnose_3.8.10ubuntu0.1_all.deb (--unpack):
 unable to open '/usr/lib/systemd/system/failsafe-x.service.dpkg-new': No such file or directory

I asked Chat for suggestions as to what to do with this, and none of its suggestions worked.  


Can anyone tell me out of this mess? I guess I want to first be able to reinstall xdiagnose, and when that is successful, try the first problem again.

---

### Post by Bashing-om on 2024-11-04
Hello mark-galeck - Welcome to the Forums :D

Please post back the results - between code tags - of terminal commands:
```

sudo apt update
sudo apt upgrade
sudo apt install --reinstall xdiagnose

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

we see here
[INDENT]what tale gets told
[/INDENT]

---

### Post by mark-galeck on 2024-11-04
```

mark@~$ sudo apt update
[sudo] password for mark:
Hit:1 https://dl.winehq.org/wine-builds/ubuntu jammy InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu noble InRelease
Get:3 http://us.archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]
Hit:4 http://security.ubuntu.com/ubuntu noble-security InRelease
Hit:5 http://us.archive.ubuntu.com/ubuntu noble-backports InRelease
Get:6 http://us.archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages [614 kB]
Get:7 https://esm.ubuntu.com/apps/ubuntu noble-apps-updates InRelease [7,468 B]
Get:8 https://esm.ubuntu.com/apps/ubuntu noble-apps-security InRelease [7,532 B]
Get:9 http://us.archive.ubuntu.com/ubuntu noble-updates/main i386 Packages [322 kB]
Get:10 https://esm.ubuntu.com/infra/ubuntu noble-infra-updates InRelease [7,461 B]
Get:11 https://esm.ubuntu.com/infra/ubuntu noble-infra-security InRelease [7,462 B]
Fetched 1,093 kB in 1s (766 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
[COLOR=#000000]

```
```

[/COLOR]~$ apt list --upgradable
Listing... Done
lintian/noble-updates,noble-updates 2.117.0ubuntu1.2 all [upgradable from: 2.117.0ubuntu1.1]
xdiagnose/noble-updates,noble-updates 3.8.10ubuntu0.1 all [upgradable from: 3.8.10]


```
```

~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following upgrades have been deferred due to phasing:
  lintian
The following packages will be upgraded:
  xdiagnose
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/57.5 kB of archives.
After this operation, 2,048 B disk space will be freed.
Do you want to continue? [Y/n] Y
dpkg: warning: files list file for package 'xdiagnose' missing; assuming package has no files currently installed
(Reading database ... 255819 files and directories currently installed.)
Preparing to unpack .../xdiagnose_3.8.10ubuntu0.1_all.deb ...
Unpacking xdiagnose (3.8.10ubuntu0.1) over (3.8.10) ...
dpkg: error processing archive /var/cache/apt/archives/xdiagnose_3.8.10ubuntu0.1_all.deb (--unpack):
 unable to open '/usr/lib/systemd/system/failsafe-x.service.dpkg-new': No such file or directory
No apport report written because the error message indicates an issue on the local system
                                                                                         Errors were encountered while processing:
 /var/cache/apt/archives/xdiagnose_3.8.10ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
```

~$ sudo apt install --reinstall xdiagnose
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be upgraded:
  xdiagnose
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/57.5 kB of archives.
After this operation, 2,048 B disk space will be freed.
dpkg: warning: files list file for package 'xdiagnose' missing; assuming package has no files currently installed
(Reading database ... 255819 files and directories currently installed.)
Preparing to unpack .../xdiagnose_3.8.10ubuntu0.1_all.deb ...
Unpacking xdiagnose (3.8.10ubuntu0.1) over (3.8.10) ...
dpkg: error processing archive /var/cache/apt/archives/xdiagnose_3.8.10ubuntu0.1_all.deb (--unpack):
 unable to open '/usr/lib/systemd/system/failsafe-x.service.dpkg-new': No such file or directory
No apport report written because the error message indicates an issue on the local system
                                                                                         Errors were encountered while processing:
 /var/cache/apt/archives/xdiagnose_3.8.10ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


[COLOR=#000000]

[/COLOR]

---

### Post by mark-galeck on 2024-11-04
by the way, when confronted with the error:
unable to open '/usr/lib/systemd/system/failsafe-x.service.dpkg-new': No such file or directory
Chat suggested I check the /usr/lib/systemd/system directory for permissions, they were OK

then suggested specific steps to remedy the "missing" file
I did those steps and at the end I still got the same message when trying to reinstall xdiagnose

---

### Post by Bashing-om on 2024-11-04
mark-galeck - Well !

There is an open bug on this:
[https://bugs.launchpad.net/xdiagnose/+bug/2083754](https://bugs.launchpad.net/xdiagnose/+bug/2083754)

Add yourself as affected too - let's see what the big boys work out.

[INDENT]a kick upstairs
[/INDENT]

---

### Post by mark-galeck on 2024-11-04
Thank you! I will add myself to the affected.

But, my problem primarily started with 

$sudo apt upgrade

failing.  and now it seems, that it sees both lintian and xdiagnose as upgradable, and does not succeed in upgrading either of them.  xdiagnose may not be important for me, but what about other packages.  I want to be able to upgrade things, until xdiagnose is fixed.  

So how to get 
sudo apt upgrade
to work for other packages?

---

### Post by Bashing-om on 2024-11-04
mark-galeck - HUmmm -

'Tween  rock and a hard place - maybe - just maybe see if you can place xdiagnose in a "hold" state.

lintian: will be upgradeable in your turn. See: 
[https://canonical-sru-docs.readthedocs-hosted.com/en/latest/explanation/standard-processes/#phasing](https://canonical-sru-docs.readthedocs-hosted.com/en/latest/explanation/standard-processes/#phasing)

once xdiagnose is in a stable state.

[INDENT]All I can do is punt
[/INDENT]

---

### Post by vladodias on 2024-11-05
These bugs have been open for a while now, they are affecting many people but there is no priority or no one assigned... is there a way we can help to get this assigned to someone and fixed?

[https://bugs.launchpad.net/ubuntu/+source/xdiagnose/+bug/2084820](https://bugs.launchpad.net/ubuntu/+source/xdiagnose/+bug/2084820)
[https://bugs.launchpad.net/ubuntu/+source/xdiagnose/+bug/2084889](https://bugs.launchpad.net/ubuntu/+source/xdiagnose/+bug/2084889)
[https://bugs.launchpad.net/ubuntu/+source/xdiagnose/+bug/2084831](https://bugs.launchpad.net/ubuntu/+source/xdiagnose/+bug/2084831)
[https://bugs.launchpad.net/xdiagnose/+bug/2083754](https://bugs.launchpad.net/xdiagnose/+bug/2083754)

---

