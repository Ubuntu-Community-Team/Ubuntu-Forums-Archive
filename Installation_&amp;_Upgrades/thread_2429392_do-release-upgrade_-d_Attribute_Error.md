---
title: "do-release-upgrade -d Attribute Error"
date: 2019-10-17
forum: Installation &amp; Upgrades
---

### Post by seanferd on 2019-10-17
I'm on 19.04, trying to upgrade to 19.10. I was previously using the disco-proposed repository, so I assumed that this upgrade would be more or less changing my repositories to point to Eoan on my behalf.

I've tried do-release-upgrade, which finds nothing still. However, when I run do-release-upgrade -d it does try to download but fails to actually get started:```

sean@ubuntu19:~/scripts$ sudo do-release-upgrade -d
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [1,554 B]                                         
Get:2 Upgrade tool [1,319 kB]                                                  
Fetched 1,320 kB in 0s (0 B/s)                                                 
authenticate 'eoan.tar.gz' against 'eoan.tar.gz.gpg' 
extracting 'eoan.tar.gz'
Reading cache
Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) disco InRelease                        
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security InRelease [97.5 kB]     
Hit [http://ppa.launchpad.net/vantuz/cool-retro-term/ubuntu](http://ppa.launchpad.net/vantuz/cool-retro-term/ubuntu) disco InRelease     
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) disco-updates InRelease [97.5 kB]    
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) disco-backports InRelease [88.8 kB]  
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) disco-proposed InRelease               
Fetched 284 kB in 0s (0 B/s)                                                   
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeQuirks.py", line 802, in _prepare_snap_replacement_data
    di.version('%s' % self.controller.fromDist).split()[0]
AttributeError: 'UbuntuDistroInfo' object has no attribute 'version'
```
During handling of the above exception, another exception occurred:
```
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-f5587x_j/eoan", line 8, in <module>
    sys.exit(main())
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeMain.py", line 238, in main
    if app.run():
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeController.py", line 2084, in run
    return self.fullUpgrade()
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeController.py", line 1921, in fullUpgrade
    if not self.doPostInitialUpdate():
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeController.py", line 927, in doPostInitialUpdate
    self.quirks.run("PostInitialUpdate")
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeQuirks.py", line 97, in run
    func()
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeQuirks.py", line 129, in eoanPostInitialUpdate
    self._calculateSnapSizeRequirements()
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeQuirks.py", line 459, in _calculateSnapSizeRequirements
    self._prepare_snap_replacement_data()
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeQuirks.py", line 808, in _prepare_snap_replacement_data
    (r.version for r in di.get_all("object")
AttributeError: 'UbuntuDistroInfo' object has no attribute 'get_all'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/problem_report.py", line 477, in add_to_existing
    self.write(f)
  File "/usr/lib/python3/dist-packages/problem_report.py", line 430, in write
    block = f.read(1048576)
  File "/usr/lib/python3.7/codecs.py", line 322, in decode
    (result, consumed) = self._buffer_decode(data, self.errors, final)
UnicodeDecodeError: 'utf-8' codec can't decode byte 0x8b in position 1: invalid start byte
```
Original exception was:
```
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeQuirks.py", line 802, in _prepare_snap_replacement_data
    di.version('%s' % self.controller.fromDist).split()[0]
AttributeError: 'UbuntuDistroInfo' object has no attribute 'version'
```
During handling of the above exception, another exception occurred:
```
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-f5587x_j/eoan", line 8, in <module>
    sys.exit(main())
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeMain.py", line 238, in main
    if app.run():
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeController.py", line 2084, in run
    return self.fullUpgrade()
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeController.py", line 1921, in fullUpgrade
    if not self.doPostInitialUpdate():
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeController.py", line 927, in doPostInitialUpdate
    self.quirks.run("PostInitialUpdate")
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeQuirks.py", line 97, in run
    func()
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeQuirks.py", line 129, in eoanPostInitialUpdate
    self._calculateSnapSizeRequirements()
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeQuirks.py", line 459, in _calculateSnapSizeRequirements
    self._prepare_snap_replacement_data()
  File "/tmp/ubuntu-release-upgrader-f5587x_j/DistUpgrade/DistUpgradeQuirks.py", line 808, in _prepare_snap_replacement_data
    (r.version for r in di.get_all("object")
AttributeError: 'UbuntuDistroInfo' object has no attribute 'get_all'
```
I've been on proposed for a month or so, I've had this do-release-upgrade -d issue above for the last couple weeks. I was hoping that actual release day would resolve this but it doesn't look like it has. Any ideas on how to get around this? I'm currently downloading the 19.10 ISO and hoping that upgrade will work, but it has more than an hour to go. 

Any help is appreciated here! This is a VM, so if we can't get the upgrade to work, would it be possible to migrate easily to another VM with 19.10 already installed??

---

### Post by seanferd on 2019-10-17
Oh, I also tried upgrading to Python 3.8 earlier this week to hopefully get around this. It didn't help because I think most everything relies on 3.7. I tried looking at the DistUpgradePerks.py script and I have no idea what to look for - I've made no changes in this area besides the Disco proposed stuff.

---

### Post by rsteinmetz70112 on 2019-10-17
I suspect that your python is somehow out of sync. Possible some of the 3.8 is still there or superseding python 3.7

Have your tried 
```
sudo dpkg --configure -a 
sudo apy install -f
```

That may point to some errors or it may fix the problem.

Also do you have any software from any non Ubuntu repositories or PPAs?

---

### Post by seanferd on 2019-10-17
Hey, thanks for the reply! I'm not sure I follow the 7.8 comment..

No, I don't have any PPA repos enabled, nothing crazy. Really the only 'custom' thing I can think of was compiling ssh from source to use a less secure key length (company requirement). But it's installed in /usr/bin and the OS included version is still installed.

I ran your commands, the first one had no output and the second one can't find apy. I assume you meant apt, which found nothing to install / upgrade / remove.

---

### Post by seanferd on 2019-10-17
I tried running the Software Updater to see if it would tell me that an update was available and it kept crashing saying "You stopped the check for updates". I found a link stating that this was a pip / wheel issue and ran the following:

[COLOR=#242729][FONT=Consolas]sudo pip3 install --upgrade pip setuptools wheel

This fixed the software updater, but no luck anywhere else. [/FONT][/COLOR]

---

### Post by seanferd on 2019-10-17
Alright, the last update got me on the right path, I think. I found a command that listed the out of date pip modules, one of which was dist-info at version 0.0.0. I tried upgrading it and it "successfully" upgraded to the same version. After doing a pip uninstall it showed version distro-info==0.21ubuntu2. Now the do-release-upgrade -d worked as expected!

---

### Post by rsteinmetz70112 on 2019-10-18
> **seanferd said:**
> Hey, thanks for the reply! I'm not sure I follow the 7.8 comment..

No, I don't have any PPA repos enabled, nothing crazy. Really the only 'custom' thing I can think of was compiling ssh from source to use a less secure key length (company requirement). But it's installed in /usr/bin and the OS included version is still installed.

I ran your commands, the first one had no output and the second one can't find apy. I assume you meant apt, which found nothing to install / upgrade / remove.

Sorry typo meant to say 3.8 and apt.

---

