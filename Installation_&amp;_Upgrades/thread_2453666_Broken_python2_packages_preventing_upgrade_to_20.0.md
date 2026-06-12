---
title: "Broken python2 packages preventing upgrade to 20.04"
date: 2020-11-14
forum: Installation &amp; Upgrades
---

### Post by hypercoffeedude on 2020-11-14
Hello all, I am trying to upgrade from Ubuntu 19.10 to 20.04 using "do-release-upgrade" in the terminal. I receive the following error. I am not sure what to do next. I know linux pretty well, and I am comfortable in the terminal if anyone has any ideas. I've provided a few logs, if there is another I should be looking at I can post those as well.

```
Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

Calculating the changes
Calculating the changes
Could not calculate the upgrade
 
An unresolvable problem occurred while calculating the upgrade. 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. If 
you want to investigate this yourself the log files in 
'/var/log/dist-upgrade' will contain details about the upgrade. 
Specifically, look at 'main.log' and 'apt.log'. 

Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
```

main.log
```
2020-11-14 23:52:16,345 INFO Using config files '['./DistUpgrade.cfg']'
2020-11-14 23:52:16,345 INFO uname information: 'Linux CF-31-Ubuntu 5.3.0-64-generic #58-Ubuntu SMP Fri Jul 10 19:33:51 UTC 2020 x86_64'
2020-11-14 23:52:16,757 INFO apt version: '1.9.4ubuntu0.1'
2020-11-14 23:52:16,757 INFO python version: '3.7.5 (default, Apr 19 2020, 20:18:17) 
[GCC 9.2.1 20191008]'
2020-11-14 23:52:16,761 INFO release-upgrader version '20.04.28' started
2020-11-14 23:52:16,770 INFO locale: 'en_US' 'UTF-8'
2020-11-14 23:52:16,825 DEBUG screen returned: 'No Sockets found in /run/screen/S-root.

'
2020-11-14 23:52:16,825 INFO re-exec inside screen: '['screen', '-e', '\\0\\0', '-c', 'screenrc', '-S', 'ubuntu-release-upgrade-screen-window', '/tmp/ubuntu-release-upgrader-5ufub9do/focal', '--mode=server', '--frontend=DistUpgradeViewText']'
```

apt.log
```
Log time: 2020-11-14 23:13:14.051867
Log time: 2020-11-14 23:13:17.260095
Log time: 2020-11-14 23:14:28.600601
  MarkInstall python2-dbg:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU Ib > FU=1
  Installing python2 as Depends of python2-dbg
    MarkInstall python2:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU Ib > FU=0
    Installing python2-minimal as PreDepends of python2
      MarkInstall python2-minimal:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > FU=0
    Installing libpython2-stdlib as Depends of python2
      MarkInstall libpython2-stdlib:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > FU=0
  Installing libpython2-dbg as Depends of python2-dbg
    MarkInstall libpython2-dbg:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > FU=0
Starting pkgProblemResolver with broken count: 7
Starting 2 pkgProblemResolver with broken count: 7
Investigating (0) python:amd64 < 2.7.17-1 @ii mK Ib >
Broken python:amd64 Depends on python2:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > (= 2.7.17-1)
  Considering python2:amd64 184 as a solution to python:amd64 343
  Added python2:amd64 to the remove list
  Fixing python:amd64 via keep of python2:amd64
  MarkKeep python2:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > FU=0
 Try to Re-Instate (0) python2:amd64
Re-Instated python2:amd64 (8 vs 7)
Investigating (0) python-minimal:amd64 < 2.7.17-1 @ii mK Ib >
Broken python-minimal:amd64 Depends on python2-minimal:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > (= 2.7.17-1)
  Considering python2-minimal:amd64 4 as a solution to python-minimal:amd64 179
  Added python2-minimal:amd64 to the remove list
  Fixing python-minimal:amd64 via keep of python2-minimal:amd64
  MarkKeep python2-minimal:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > FU=0
Investigating (0) libpython-stdlib:amd64 < 2.7.17-1 @ii mK Ib >
Broken libpython-stdlib:amd64 Depends on libpython2-stdlib:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > (= 2.7.17-1)
  Considering libpython2-stdlib:amd64 4 as a solution to libpython-stdlib:amd64 179
  Added libpython2-stdlib:amd64 to the remove list
  Fixing libpython-stdlib:amd64 via keep of libpython2-stdlib:amd64
  MarkKeep libpython2-stdlib:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > FU=0
 Try to Re-Instate (0) python2-minimal:amd64
  MarkKeep python2-minimal:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > FU=0
 Try to Re-Instate (0) libpython2-stdlib:amd64
  MarkKeep libpython2-stdlib:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > FU=0
Investigating (0) python-dev:amd64 < 2.7.17-1 @ii mK Ib >
Broken python-dev:amd64 Depends on python2-dev:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU Ib > (= 2.7.17-1)
  Considering python2-dev:amd64 2 as a solution to python-dev:amd64 3
  Added python2-dev:amd64 to the remove list
  Fixing python-dev:amd64 via keep of python2-dev:amd64
  MarkKeep python2-dev:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU Ib > FU=0
 Try to Re-Instate (0) python2-dev:amd64
  MarkKeep python2-dev:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU Ib > FU=0
Investigating (0) python2-dev:amd64 < 2.7.17-1 | 2.7.17-2ubuntu4 @ii umH Ib >
Broken python2-dev:amd64 Depends on python2:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU Ib > (= 2.7.17-1)
  Considering python2:amd64 184 as a solution to python2-dev:amd64 2
  Removing python2-dev:amd64 rather than change python2:amd64
  MarkDelete python2-dev:amd64 < 2.7.17-1 | 2.7.17-2ubuntu4 @ii umH Ib > FU=0
Investigating (0) libpython-dbg:amd64 < 2.7.17-1 @ii mK Ib >
Broken libpython-dbg:amd64 Depends on libpython2-dbg:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > (= 2.7.17-1)
  Considering libpython2-dbg:amd64 1 as a solution to libpython-dbg:amd64 0
  Removing libpython-dbg:amd64 rather than change libpython2-dbg:amd64
  MarkDelete libpython-dbg:amd64 < 2.7.17-1 @ii mK Ib > FU=0
Investigating (0) libpython-all-dbg:amd64 < 2.7.17-1 | 2.7.17-2ubuntu4 @ii umH Ib >
Broken libpython-all-dbg:amd64 Depends on libpython-dbg:amd64 < 2.7.17-1 @ii mR > (= 2.7.17-1)
  Considering libpython-dbg:amd64 0 as a solution to libpython-all-dbg:amd64 0
  Re-Instated libpython-all-dbg:amd64
Investigating (0) python-dbg:amd64 < 2.7.17-1 @ii mK Ib >
Broken python-dbg:amd64 Depends on libpython-dbg:amd64 < 2.7.17-1 @ii mR > (= 2.7.17-1)
  Considering libpython-dbg:amd64 0 as a solution to python-dbg:amd64 -1
  Removing python-dbg:amd64 rather than change libpython-dbg:amd64
  MarkDelete python-dbg:amd64 < 2.7.17-1 @ii mK Ib > FU=0
Investigating (0) python-all-dbg:amd64 < 2.7.17-1 | 2.7.17-2ubuntu4 @ii umH Ib >
Broken python-all-dbg:amd64 Depends on libpython-all-dbg:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > (= 2.7.17-1)
  Considering libpython-all-dbg:amd64 0 as a solution to python-all-dbg:amd64 -1
  Re-Instated python-all:amd64
  Re-Instated python-all-dbg:amd64
Investigating (1) python:amd64 < 2.7.17-1 @ii mK Ib >
Broken python:amd64 Depends on python2:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU Ib > (= 2.7.17-1)
  Considering python2:amd64 184 as a solution to python:amd64 343
  Added python2:amd64 to the remove list
  Fixing python:amd64 via keep of python2:amd64
  MarkKeep python2:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU Ib > FU=0
Investigating (1) python-dev:amd64 < 2.7.17-1 @ii mK Ib >
Broken python-dev:amd64 Depends on python2-dev:amd64 < 2.7.17-1 | 2.7.17-2ubuntu4 @ii umR > (= 2.7.17-1)
  Considering python2-dev:amd64 2 as a solution to python-dev:amd64 3
  Added python2-dev:amd64 to the remove list
  Fixing python-dev:amd64 via keep of python2-dev:amd64
  MarkKeep python2-dev:amd64 < 2.7.17-1 | 2.7.17-2ubuntu4 @ii umR > FU=0
Investigating (1) python-all:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU Ib >
Broken python-all:amd64 Depends on python2:amd64 < 2.7.17-1 | 2.7.17-2ubuntu4 @ii umH > (= 2.7.17-2ubuntu4)
  Considering python2:amd64 184 as a solution to python-all:amd64 2
  MarkKeep python-all:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU Ib > FU=0
  Holding Back python-all:amd64 rather than change python2:amd64
Investigating (1) python-all-dbg:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU Ib >
Broken python-all-dbg:amd64 Depends on python2:amd64 < 2.7.17-1 | 2.7.17-2ubuntu4 @ii umH > (= 2.7.17-2ubuntu4)
  Considering python2:amd64 184 as a solution to python-all-dbg:amd64 -1
  MarkKeep python-all-dbg:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU Ib > FU=0
  Removing python-all-dbg:amd64 rather than change python2:amd64
  MarkDelete python-all-dbg:amd64 < 2.7.17-1 | 2.7.17-2ubuntu4 @ii umH Ib > FU=0
Investigating (2) python2-dbg:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii pumU Ib >
Broken python2-dbg:amd64 Depends on python2:amd64 < 2.7.17-1 | 2.7.17-2ubuntu4 @ii umH > (= 2.7.17-2ubuntu4)
  Considering python2:amd64 184 as a solution to python2-dbg:amd64 10000
Done
Log time: 2020-11-14 23:14:31.859002
```

grep Broken /var/log/dist-upgrade/apt.log
```

Broken python:amd64 Depends on python2:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > (= 2.7.17-1)
Broken python-minimal:amd64 Depends on python2-minimal:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > (= 2.7.17-1)
Broken libpython-stdlib:amd64 Depends on libpython2-stdlib:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > (= 2.7.17-1)
Broken python-dev:amd64 Depends on python2-dev:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU Ib > (= 2.7.17-1)
Broken python2-dev:amd64 Depends on python2:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU Ib > (= 2.7.17-1)
Broken libpython-dbg:amd64 Depends on libpython2-dbg:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > (= 2.7.17-1)
Broken libpython-all-dbg:amd64 Depends on libpython-dbg:amd64 < 2.7.17-1 @ii mR > (= 2.7.17-1)
Broken python-dbg:amd64 Depends on libpython-dbg:amd64 < 2.7.17-1 @ii mR > (= 2.7.17-1)
Broken python-all-dbg:amd64 Depends on libpython-all-dbg:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU > (= 2.7.17-1)
Broken python:amd64 Depends on python2:amd64 < 2.7.17-1 -> 2.7.17-2ubuntu4 @ii umU Ib > (= 2.7.17-1)
Broken python-dev:amd64 Depends on python2-dev:amd64 < 2.7.17-1 | 2.7.17-2ubuntu4 @ii umR > (= 2.7.17-1)
Broken python-all:amd64 Depends on python2:amd64 < 2.7.17-1 | 2.7.17-2ubuntu4 @ii umH > (= 2.7.17-2ubuntu4)
Broken python-all-dbg:amd64 Depends on python2:amd64 < 2.7.17-1 | 2.7.17-2ubuntu4 @ii umH > (= 2.7.17-2ubuntu4)
Broken python2-dbg:amd64 Depends on python2:amd64 < 2.7.17-1 | 2.7.17-2ubuntu4 @ii umH > (= 2.7.17-2ubuntu4)

```

---

### Post by Impavidus on 2020-11-15
Release upgrades from a supported release to the next release work quite well. Release upgrades from an LTS release to the next LTS release work quite well too. But you're trying to upgrade from a dead release. What's more, your system is broken and when Python is broken that's a real problem, as core components of the OS depend on Python.

I don't think (but am not entirely sure) that any components of Ubuntu 19.10 relied on Python 2, so you could try to remove Python 2 completely. But I wouldn't attempt an upgrade. Just fresh install Ubuntu 20.04. It will come without Python 2.

---

### Post by hypercoffeedude on 2020-11-16
I wouldn't think 19.10 would be a dead release so soon... Attempting to remove python2 would result in losing about 1.3Gb of software in my case. I noticed in the new release it uses a package called "python-is-python3" to keep compatibility with anything that requires python2. Is there anyway to trick my system to install this package (and have it remove python2?). I have quite a few programs installed and many more things I'd rather not have to deal with after a fresh install. I love a fresh install, but getting it back the way this one is would be time consuming.

---

### Post by The Cog on 2020-11-16
I think  the easiest way out of this is to do a fresh install of 20.04 and then restore your home and user data from your backup.
If you don't have a backup then now (before an upgrade or re-install) is a very good time to make one.

Fresh install and then restore backup is the way I always upgrade. It generally means having to install a few packages that I use and that don't come as default, but if you keep a list of those as you install them, installing them again next time is a breeze. These days I just use an ansible playbook to reinstall the optional packages, configure the firewall and ssh server etc, but that's just something you might want to think about in the future.

---

### Post by Impavidus on 2020-11-16
19.10 had 9 months of support, like all interim releases.

Python 2 is no longer supported from upstream. It's still available on Ubuntu 20.04, but no longer installed by default. Some time in the future there will be an Ubuntu release that no longer has Python 2 in the repos.

When a Python script says it's for /usr/bin/python, it will be interpreted by Python 2 and will give an error if that's not available. If it says /usr/bin/python3, it will be interpreted by Python 3. The purpose of python-is-python3 is to eliminate the error for scripts that don't say explicitly they are for Python 3, but are compatible with it.

---

