---
title: "can't upgrade from 18.04 to 20.04"
date: 2020-08-11
forum: Installation &amp; Upgrades
---

### Post by anewbie on 2020-08-11
I'm trying to upgrade from 18.04 to 20.04. When I try do-release-upgrade it sez no release:
--
```
apt-get update
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                     
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Hit:4 [http://ppa.launchpad.net/alex-p/qcad/ubuntu](http://ppa.launchpad.net/alex-p/qcad/ubuntu) bionic InRelease      
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Reading package lists... Done                     
--
root@pc1:~> apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
---

```
root@pc1:~> do-release-upgrade 
Checking for a new Ubuntu release
There is no development version of an LTS available.
To upgrade to the latest non-LTS develoment release 
set Prompt=normal in /etc/update-manager/release-upgrades.
```
--
```
root@pc1:~>  cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.5 LTS"
--
root@pc1:~> cat /etc/update-manager/release-upgrades
# Default behavior for the release upgrader.

[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for, or allow upgrading to, a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the supported release that immediately succeeds the
#           currently-running release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that if this option is used and
#           the currently-running release is not itself an LTS release the
#           upgrader will assume prompt was meant to be normal.
Prompt=lts
```
---



I then try do-release-upgrade -d and got an error:
```
root@pc1:~> do-release-upgrade  -d
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [1554 B]                                          
Get:2 Upgrade tool [1333 kB]                                                   
Fetched 1334 kB in 0s (0 B/s)                                                  
authenticate 'focal.tar.gz' against 'focal.tar.gz.gpg' 
extracting 'focal.tar.gz'

Reading cache

Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                       
Hit [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease                
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease               
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease             
Hit [http://ppa.launchpad.net/alex-p/qcad/ubuntu](http://ppa.launchpad.net/alex-p/qcad/ubuntu) bionic InRelease               
Fetched 0 B in 0s (0 B/s)                                                      
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

Checking for installed snaps

Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/focal", line 8, in <module>
    sys.exit(main())
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/DistUpgrade/DistUpgradeMain.py", line 238, in main
    if app.run():
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/DistUpgrade/DistUpgradeController.py", line 2081, in run
    return self.fullUpgrade()
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/DistUpgrade/DistUpgradeController.py", line 1918, in fullUpgrade
    if not self.doPostInitialUpdate():
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/DistUpgrade/DistUpgradeController.py", line 924, in doPostInitialUpdate
    self.quirks.run("PostInitialUpdate")
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/DistUpgrade/DistUpgradeQuirks.py", line 99, in run
    func()
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/DistUpgrade/DistUpgradeQuirks.py", line 132, in focalPostInitialUpdate
    self._calculateSnapSizeRequirements()
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/DistUpgrade/DistUpgradeQuirks.py", line 516, in _calculateSnapSizeRequirements
    self._prepare_snap_replacement_data()
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/DistUpgrade/DistUpgradeQuirks.py", line 956, in _prepare_snap_replacement_data
    stdout=subprocess.PIPE).communicate()
  File "/usr/lib/python3.6/subprocess.py", line 850, in communicate
    stdout = self.stdout.read()
  File "/usr/lib/python3.6/encodings/ascii.py", line 26, in decode
    return codecs.ascii_decode(input, self.errors)[0]
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 1072: ordinal not in range(128)
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/problem_report.py", line 497, in add_to_existing
    self.write(f)
  File "/usr/lib/python3/dist-packages/problem_report.py", line 450, in write
    block = f.read(1048576)
  File "/usr/lib/python3.6/encodings/ascii.py", line 26, in decode
    return codecs.ascii_decode(input, self.errors)[0]
UnicodeDecodeError: 'ascii' codec can't decode byte 0x8b in position 1: ordinal not in range(128)

Original exception was:
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/focal", line 8, in <module>
    sys.exit(main())
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/DistUpgrade/DistUpgradeMain.py", line 238, in main
    if app.run():
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/DistUpgrade/DistUpgradeController.py", line 2081, in run
    return self.fullUpgrade()
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/DistUpgrade/DistUpgradeController.py", line 1918, in fullUpgrade
    if not self.doPostInitialUpdate():
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/DistUpgrade/DistUpgradeController.py", line 924, in doPostInitialUpdate
    self.quirks.run("PostInitialUpdate")
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/DistUpgrade/DistUpgradeQuirks.py", line 99, in run
    func()
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/DistUpgrade/DistUpgradeQuirks.py", line 132, in focalPostInitialUpdate
    self._calculateSnapSizeRequirements()
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/DistUpgrade/DistUpgradeQuirks.py", line 516, in _calculateSnapSizeRequirements
    self._prepare_snap_replacement_data()
  File "/tmp/ubuntu-release-upgrader-6onxj1yd/DistUpgrade/DistUpgradeQuirks.py", line 956, in _prepare_snap_replacement_data
    stdout=subprocess.PIPE).communicate()
  File "/usr/lib/python3.6/subprocess.py", line 850, in communicate
    stdout = self.stdout.read()
  File "/usr/lib/python3.6/encodings/ascii.py", line 26, in decode
    return codecs.ascii_decode(input, self.errors)[0]
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 1072: ordinal not in range(128)
root@pc1:~>
```
---
When will 20.04 be available as an upgrade from 18.04 ?

---

### Post by yavnest on 2020-08-11
AFAIK, they delay the "pushing" of the LTS *04.01 to the LTS users a few days to make sure there are no issues with it - since LTS users are supposedly big on stability.

---

### Post by anewbie on 2020-08-12
Ok thank you. i tried check if such was the case but couldn't find anything definitive. Also the error i got when using -d was a bit concerning. I keep getting video crashes with 18.04 so was hopeful they fixed (or improved) the ati driver for 20.04 or at least fix video for sandybridge in the kernel (16.04 worked fine with native video in sandybridge; but then 18.04 broke it).

---

