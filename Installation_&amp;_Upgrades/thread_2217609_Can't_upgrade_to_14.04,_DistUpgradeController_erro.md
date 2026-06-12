---
title: "Can't upgrade to 14.04, DistUpgradeController error"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by miskopo on 2014-04-18
Hello!

I try to upgrade my 12.04 desktop to 14.04, but I continously get several errors (via terminal and via upgrade manager either):

```
Traceback (most recent call last): 

File "/tmp/update-manager-WBPSvW/trusty", line 10, in <module> 
sys.exit(main()) 

File "/tmp/update-manager-WBPSvW/DistUpgrade/DistUpgradeMain.py", 
line 243, in main 
if app.run(): 

File 
"/tmp/update-manager-WBPSvW/DistUpgrade/DistUpgradeController.py", 
line 1827, in run 
return self.fullUpgrade() 

File 
"/tmp/update-manager-WBPSvW/DistUpgrade/DistUpgradeController.py", 
line 1780, in fullUpgrade 
if not self.askDistUpgrade(): 

File 
"/tmp/update-manager-WBPSvW/DistUpgrade/DistUpgradeController.py", 
line 988, in askDistUpgrade 
if not self._checkFreeSpace(): 

File 
"/tmp/update-manager-WBPSvW/DistUpgrade/DistUpgradeController.py", 
line 965, in _checkFreeSpace 
required.dir)) 
```

Here are also logs:
[https://dl.dropboxusercontent.com/u/102148475/apt.log](https://dl.dropboxusercontent.com/u/102148475/apt.log)
[https://dl.dropboxusercontent.com/u/102148475/main.log](https://dl.dropboxusercontent.com/u/102148475/main.log)

New sources are already added, upgrade tool was properly downloaded. I aleso tried apt-get -f install and dependecies check, but with no success.

Any ideas? 

Thank you

---

### Post by Mama_Hadija on 2014-04-18
u better backup your stuff and do a new installation all together. i think its the same reason why u cant upgrade from windows xp to windows 8 but you can upgrade from windows xp to say windows 7. compatibility and a overhaul in the kernel from 12 to 14

---

### Post by Mama_Hadija on 2014-04-18
To just check what type of release you can upgrade to, type:
  sudo do-release-upgrade --check-dist-upgrade-only --devel-release

---

### Post by miskopo on 2014-04-18
Thank you, output says, that I can upgrade to 14.04

---

### Post by miskopo on 2014-04-18
Any other ideas? I would really not like to do fresh install, I have so many customizations done.
Thank you

---

### Post by jajodo on 2014-04-18
This is a shot in the dark but make sure you are not using proprietary video drivers like nvidia.  There is no end to the upgrade errors that can cause.  Uninstall them and reinstall after upgrade.

---

### Post by miskopo on 2014-04-19
Lucklessly, I use no proprietary drivers

---

### Post by finni on 2014-05-14
The real problem is the last error here:
```

UnicodeDecodeError: 'ascii' codec can't decode byte 0xc2 in position 1: ordinal not in range(128)

```
I have the exact same problem with Finnish localization when trying to upgrade from 12.04 to 14.04. There seems to be older bug reports from older ubuntu version that have the same issue. Fixes proposed in those seem not to work.

---

### Post by finni on 2014-05-14
Solved it with following instructions (Ubuntu servers):

[https://help.ubuntu.com/community/TrustyUpgrades#Ubuntu_Servers_.28Recommended.29](https://help.ubuntu.com/community/TrustyUpgrades#Ubuntu_Servers_.28Recommended.29)

---

### Post by velmont on 2014-06-01
Really horrible bug.

It's mainly due to apt_pkg's size_to_str function somehow returns a size string with utf-8 encoded (in binary) string in it when your locale gives you something like that back. So the "needed" size is all wrong.

It only triggers when you have too little disk space. This is not neccesarily your main disk, for me, it was /boot/ that had too little space (really, -- can't it just delete the 5-6 old kernels there itself? How is my girlfriend supposed to know this (her machine)!).

Anyway, the fix is to make sure you have enough space.

The real fix is to fix apt_pkg.size_to_str python module I believe. To return a unicode object, not some undecoded binary string.

---

### Post by velmont on 2014-06-01
I did a patch for it. Don't know if they'll take it though. It can also be worked around in the Ubuntu-code.

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=750120](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=750120)

---

### Post by velmont on 2014-06-01
And a bug about the upgrade (needs to be fixed there as well, because they won't take the new version in old Ubuntu anyway):

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1325418](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1325418)

---

