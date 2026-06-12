---
title: "do-relase-upgrade fails to run."
date: 2019-04-13
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2019-04-13
I am attempting to upgrade a system running 16.04 LTS to 18.04 LTS

I tried to run do-releae-upgrade and it appears to start normally. 
```
$ do-release-upgrade
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [819 B]                                           
Get:2 Upgrade tool [1,246 kB]                                                  
Fetched 1,247 kB in 0s (0 B/s)                                                 
authenticate 'bionic.tar.gz' against 'bionic.tar.gz.gpg' 
extracting 'bionic.tar.gz'
[sudo] password for romulus: 
```

However as soon as I give it the users password I get the following output, 
If I run the command as sudo I get the same result, which i can't make heads or tails of:

```
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-zowqztrk/bionic", line 8, in <module>
    sys.exit(main())
  File "/tmp/ubuntu-release-upgrader-zowqztrk/DistUpgrade/DistUpgradeMain.py", line 224, in main
    from .DistUpgradeController import DistUpgradeController
  File "/tmp/ubuntu-release-upgrader-zowqztrk/DistUpgrade/DistUpgradeController.py", line 52, in <module>
    from .DistUpgradeQuirks import DistUpgradeQuirks
  File "/tmp/ubuntu-release-upgrader-zowqztrk/DistUpgrade/DistUpgradeQuirks.py", line 36, in <module>
    from janitor.plugincore.manager import PluginManager
  File "/tmp/ubuntu-release-upgrader-zowqztrk/janitor/__init__.py", line 20, in <module>
    import pkg_resources
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 69, in <module>
    __import__('pkg_resources.extern.packaging.version')
  File "/usr/lib/python3/dist-packages/pkg_resources/_vendor/packaging/version.py", line 10, in <module>
    from ._structures import Infinity
  File "<frozen importlib._bootstrap>", line 969, in _find_and_load
  File "<frozen importlib._bootstrap>", line 958, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 673, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 661, in exec_module
  File "<frozen importlib._bootstrap_external>", line 765, in get_code
  File "<frozen importlib._bootstrap_external>", line 476, in _compile_bytecode
ValueError: bad marshal data (invalid reference)
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/problem_report.py", line 497, in add_to_existing
    self.write(f)
  File "/usr/lib/python3/dist-packages/problem_report.py", line 450, in write
    block = f.read(1048576)
  File "/usr/lib/python3.5/codecs.py", line 321, in decode
    (result, consumed) = self._buffer_decode(data, self.errors, final)
UnicodeDecodeError: 'utf-8' codec can't decode byte 0x8b in position 1: invalid start byte
```

It is followed by this output 

```
Original exception was:
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-zowqztrk/bionic", line 8, in <module>
    sys.exit(main())
  File "/tmp/ubuntu-release-upgrader-zowqztrk/DistUpgrade/DistUpgradeMain.py", line 224, in main
    from .DistUpgradeController import DistUpgradeController
  File "/tmp/ubuntu-release-upgrader-zowqztrk/DistUpgrade/DistUpgradeController.py", line 52, in <module>
    from .DistUpgradeQuirks import DistUpgradeQuirks
  File "/tmp/ubuntu-release-upgrader-zowqztrk/DistUpgrade/DistUpgradeQuirks.py", line 36, in <module>
    from janitor.plugincore.manager import PluginManager
  File "/tmp/ubuntu-release-upgrader-zowqztrk/janitor/__init__.py", line 20, in <module>
    import pkg_resources
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 69, in <module>
    __import__('pkg_resources.extern.packaging.version')
  File "/usr/lib/python3/dist-packages/pkg_resources/_vendor/packaging/version.py", line 10, in <module>
    from ._structures import Infinity
  File "<frozen importlib._bootstrap>", line 969, in _find_and_load
  File "<frozen importlib._bootstrap>", line 958, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 673, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 661, in exec_module
  File "<frozen importlib._bootstrap_external>", line 765, in get_code
  File "<frozen importlib._bootstrap_external>", line 476, in _compile_bytecode
ValueError: bad marshal data (invalid reference)
=== Command terminated with exit status 1 (Sat Apr 13 12:26:47 2019) ===
```

After that I am asked:

```
press x to destroy pot r to resurrect window
```

Then there is a system problem report which fails.
```

This problem report is damaged and cannot be processed.
Error('Incorrect padding',):

```


I already ran:
```

apt update
apt full-upgrade
dpkg --configure -a
apt install -f
```

None of them produce any error or output.

The download creates a folder in /tmp that has this in it:
```

# /tmp/ubuntu-release-upgrader-zowqztrk# ls -ld *
-rw-r--r--   1 root root    7327 May 18  2017 AcquireProgress.ui
-rw-r--r--   1 root root      26 May 18  2017 additional_pkgs.cfg
-rw-r--r--   1 root root    9873 Nov 12 15:09 apt_btrfs_snapshot.py
-rw-r--r--   1 root root   33593 Nov 13  2015 apt_clone.py
-rwxr-xr-x   2 root root     126 May 18  2017 bionic
-rw-r--r--   1 root root 1246272 Jan 31 03:28 bionic.tar.gz
-rw-r--r--   1 root root     819 Jan 31 03:28 bionic.tar.gz.gpg
-rwxr-xr-x   1 root root    1591 May 18  2017 build-dist.sh
-rwxr-xr-x   1 root root    1116 Jan 22 11:47 cdromupgrade
-rw-r--r--   1 root root    6867 May 18  2017 Changelog
-rw-r--r--   1 root root    4237 May 18  2017 crashdialog.ui
-rw-r--r--   1 root root   13834 Nov 12 15:09 demoted.cfg
-rw-r--r--   1 root root    8097 May 18  2017 demoted.cfg.hardy
-rw-r--r--   1 root root       0 May 18  2017 demoted.cfg.lucid
-rw-r--r--   1 root root   30482 May 18  2017 demoted.cfg.trusty
-rw-r--r--   1 root root   22427 Nov 12 15:09 demoted.cfg.xenial
-rw-r--r--   1 root root    1667 Nov  6  2017 DevelReleaseAnnouncement
-rw-r--r--   1 root root    2434 Nov 12 15:09 DevelReleaseAnnouncement.html
-rw-r--r--   1 root root    4855 May 18  2017 dialog_changes.ui
-rw-r--r--   1 root root    3514 May 18  2017 dialog_conffile.ui
-rw-r--r--   1 root root    2502 May 18  2017 dialog_error.ui
-rw-r--r--   1 root root    1682 May 18  2017 dialog_release_notes.ui
-rw-r--r--   1 root root   11572 Oct  1  2018 distinfo.py
-rw-r--r--   1 root root   23717 Oct  1  2018 distro.py
lrwxrwxrwx   1 root root       1 Apr 13 12:26 DistUpgrade -> .
-rw-r--r--   1 root root    5064 May 18  2017 DistUpgradeApport.py
-rw-r--r--   1 root root   12690 May 18  2017 DistUpgradeAptCdrom.py
-rw-r--r--   1 root root   53808 Jan 16 17:53 DistUpgradeCache.py
-rw-r--r--   1 root root    4847 Jul  9  2018 DistUpgrade.cfg
-rw-r--r--   1 root root    1623 May 18  2017 DistUpgrade.cfg.dapper
-rw-r--r--   1 root root    3821 May 18  2017 DistUpgrade.cfg.hardy
-rw-r--r--   1 root root    4058 May 18  2017 DistUpgrade.cfg.lucid
-rw-r--r--   1 root root    4069 May 18  2017 DistUpgrade.cfg.precise
-rw-r--r--   1 root root    4970 May 18  2017 DistUpgrade.cfg.trusty
-rw-r--r--   1 root root    4772 Jul  9  2018 DistUpgrade.cfg.xenial
-rw-r--r--   1 root root    3837 May 18  2017 DistUpgradeConfigParser.py
-rw-r--r--   1 root root  102412 Jan 16 17:53 DistUpgradeController.py
-rw-r--r--   1 root root   11472 Jan 16 17:53 DistUpgradeFetcherCore.py
-rw-r--r--   1 root root    9950 Mar 20  2018 DistUpgradeFetcherKDE.py
-rw-r--r--   1 root root    5966 Feb  5  2018 DistUpgradeFetcher.py
-rw-r--r--   1 root root    2064 May 18  2017 DistUpgradeFetcherSelf.py
-rw-r--r--   1 root root    3043 May 18  2017 DistUpgradeGettext.py
-rw-r--r--   1 root root    9317 May 18  2017 DistUpgradeMain.py
-rw-r--r--   1 root root    4018 May 18  2017 DistUpgradePatcher.py
-rwxr-xr-x   2 root root     126 May 18  2017 dist-upgrade.py
-rw-r--r--   1 root root   36765 Aug 28  2018 DistUpgradeQuirks.py
-rw-r--r--   1 root root   77613 Nov 12 15:09 DistUpgrade.ui
-rw-r--r--   1 root root      21 Nov 12 15:09 DistUpgradeVersion.py
-rw-r--r--   1 root root   33484 Jan 16 17:53 DistUpgradeViewGtk3.py
-rw-r--r--   1 root root   40826 Jan 16 17:53 DistUpgradeViewKDE.py
-rw-r--r--   1 root root   13637 Jan 16 17:53 DistUpgradeViewNonInteractive.py
-rw-r--r--   1 root root   16586 Jan 16 17:53 DistUpgradeView.py
-rw-r--r--   1 root root   12630 Jan 16 17:53 DistUpgradeViewText.py
-rw-r--r--   1 root root    2016 Nov  6  2017 EOLReleaseAnnouncement
-rw-r--r--   1 root root    2992 Nov 12 15:09 EOLReleaseAnnouncement.html
-rw-r--r--   1 root root     243 May 18  2017 etc-default-apport
-rw-r--r--   1 root root    1607 May 18  2017 fetch-progress.ui
drwxr-xr-x   2 root root    4096 Apr 13 12:26 gtkbuilder
-rw-r--r--   1 root root    4020 May 18  2017 GtkProgress.py
drwxr-xr-x   2 root root    4096 Apr 13 12:26 imported
-rw-r--r--   1 root root       0 May 18  2017 __init__.py
drwxr-xr-x   4 root root    4096 Apr 13 12:26 janitor
-rw-r--r--   1 root root   16878 Oct 31 06:29 MetaRelease.py
-rw-r--r--   1 root root   17855 Nov 12 15:09 mirrors.cfg
drwxrwxr-x 125 root root    4096 Apr 13 12:26 mo
drwxr-xr-x   3 root root    4096 Apr 13 12:26 NvidiaDetector
drwxr-xr-x   2 root root    4096 Apr 13 12:26 patches
-rw-r--r--   1 root root     208 May 18  2017 prerequists-sources.dapper.list
-rw-r--r--   1 root root     247 May 18  2017 prerequists-sources.dapper-ports.list
-rw-r--r--   1 root root     294 May 18  2017 prerequists-sources.list
drwxr-xr-x   2 root root    4096 Apr 13 12:26 __pycache__
-rw-r--r--   1 root root    3321 Feb  5  2018 QUrlOpener.py
-rw-r--r--   1 root root    2897 Jan 16 17:53 README
-rw-r--r--   1 root root    1730 Nov  6  2017 ReleaseAnnouncement
-rw-r--r--   1 root root    2644 Nov 12 15:09 ReleaseAnnouncement.html
-rw-r--r--   1 root root    3955 Nov 12 15:09 ReleaseNotes.ui
-rw-r--r--   1 root root    7658 Apr 12  2018 ReleaseNotesViewer.py
-rw-r--r--   1 root root    2928 May 18  2017 ReleaseNotesViewerWebkit.py
-rw-r--r--   1 root root     448 May  2  2018 removal_blacklist.cfg
-rw-r--r--   1 root root      82 May 18  2017 screenrc
-rw-r--r--   1 root root    2056 May 18  2017 SimpleGtk3builderApp.py
-rw-r--r--   1 root root    2037 May 18  2017 SimpleGtkbuilderApp.py
-rw-r--r--   1 root root   18354 Oct  1  2018 sourceslist.py
-rw-r--r--   1 root root    3478 May  3  2018 telemetry.py
-rw-r--r--   1 root root    2617 May 18  2017 TODO
-rw-------   1 root root    1200 Apr 13 12:26 trustdb.gpg
-rw-r--r--   1 root root   79002 Oct  1  2018 Ubuntu.info
-rw-r--r--   1 root root   17325 Oct  1  2018 Ubuntu.mirrors
-rw-r--r--   1 root root   14182 Nov 12 15:09 UpgradePromptDialog.ui
-rw-r--r--   1 root root   18365 Oct 31 06:29 utils.py
-rw-r--r--   1 root root    7646 Nov  6  2017 window_main.ui
-rwxr-xr-x   1 root root    4027 Jan 16 17:53 xorg_fix_proprietary.py
-rw-r--r--   1 root root     496 May 18  2017 zz-update-grub
```

---

### Post by rsteinmetz70112 on 2019-04-15
Upon further checking it appears that there is a problem with python on this machine.
I'm going to start a new thread to try to solve that one.

---

### Post by rsteinmetz70112 on 2019-04-18
I think I'm making some progress. I've been reinstall dependancies and checking configuration b now whne I run do-release-upgrade I get less output, but it still failes:
```
# do-release-upgrade
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [819 B]
Get:2 Upgrade tool [1,239 kB]
Fetched 1,240 kB in 6s (60.7 kB/s)
authenticate 'bionic.tar.gz' against 'bionic.tar.gz.gpg'
extracting 'bionic.tar.gz'
xisting
    self.write(f)
  File "/usr/lib/python3/dist-packages/problem_report.py", line 452, in write
    crc = zlib.crc32(block, crc)
TypeError: a bytes-like object is required, not 'str'

Original exception was:
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-cysvr13f/bionic", line 8, in <module>
    sys.exit(main())
  File "/tmp/ubuntu-release-upgrader-cysvr13f/DistUpgrade/DistUpgradeMain.py", line 224, in main
    from .DistUpgradeController import DistUpgradeController
  File "/tmp/ubuntu-release-upgrader-cysvr13f/DistUpgrade/DistUpgradeController.py", line 52, in <module>
    from .DistUpgradeQuirks import DistUpgradeQuirks
  File "/tmp/ubuntu-release-upgrader-cysvr13f/DistUpgrade/DistUpgradeQuirks.py", line 36, in <module>
    from janitor.plugincore.manager import PluginManager
  File "/tmp/ubuntu-release-upgrader-cysvr13f/janitor/__init__.py", line 20, in <module>
    import pkg_resources
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 69, in <module>
    __import__('pkg_resources.extern.packaging.version')
  File "/usr/lib/python3/dist-packages/pkg_resources/_vendor/packaging/version.py", line 10, in <module>
    from ._structures import Infinity
  File "<frozen importlib._bootstrap>", line 969, in _find_and_load
  File "<frozen importlib._bootstrap>", line 958, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 673, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 661, in exec_module
  File "<frozen importlib._bootstrap_external>", line 765, in get_code
  File "<frozen importlib._bootstrap_external>", line 476, in _compile_bytecode
ValueError: bad marshal data (invalid reference)
=== Command terminated with exit status 1 (Thu Apr 18 13:50:58 2019) ===
```

At the end I an still in some kind of window and get this message:
```
Press x to destroy or r to resurrect this window
```
pressing 'x' gives this message

```
[screen is terminating]
```

Finally the output seems truncated but I do't know where it is coming from.:
```
xisting
    self.write(f)
  File "/usr/lib/python3/dist-packages/problem_report.py", line 452, in write
    crc = zlib.crc32(block, crc)
TypeError: a bytes-like object is required, not 'str'

```

---

### Post by rsteinmetz70112 on 2019-04-29
Solved it. I eventually reinstalled it but reinstalling python3-pkg-resources seems at least to have eliminated the error above.

```
# apt install --reinstall python3-pkg-resources
```

I earlier had figured out is was a python problem and began reinstalling python packages. I finally got lucky.

I also posted this problem at launchpad and got an answer there, after I had stumbled on the right package to reinstall.

---

