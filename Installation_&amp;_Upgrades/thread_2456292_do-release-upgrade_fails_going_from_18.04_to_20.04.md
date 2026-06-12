---
title: "do-release-upgrade fails going from 18.04 to 20.04 invalid char 0xe2"
date: 2021-01-08
forum: Installation &amp; Upgrades
---

### Post by anewbie on 2021-01-08
When I execute do-release upgrade it fails with invalid character 0xe2:

Is there an easy fix for this issue ?

```


root@pc1:~> do-release-upgrade 
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [1554 B]                                          
Get:2 Upgrade tool [1340 kB]                                                   
Fetched 1342 kB in 0s (0 B/s)                                                  
authenticate 'focal.tar.gz' against 'focal.tar.gz.gpg' 
extracting 'focal.tar.gz'

Reading cache

Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                       
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease               
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease             
Hit [http://ppa.launchpad.net/alex-p/qcad/ubuntu](http://ppa.launchpad.net/alex-p/qcad/ubuntu) bionic InRelease               
Hit [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease                
Fetched 0 B in 0s (0 B/s)                                                      
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

Checking for installed snaps

Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/focal", line 8, in <module>
    sys.exit(main())
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/DistUpgrade/DistUpgradeMain.py", line 238, in main
    if app.run():
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/DistUpgrade/DistUpgradeController.py", line 2089, in run
    return self.fullUpgrade()
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/DistUpgrade/DistUpgradeController.py", line 1926, in fullUpgrade
    if not self.doPostInitialUpdate():
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/DistUpgrade/DistUpgradeController.py", line 924, in doPostInitialUpdate
    self.quirks.run("PostInitialUpdate")
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/DistUpgrade/DistUpgradeQuirks.py", line 99, in run
    func()
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/DistUpgrade/DistUpgradeQuirks.py", line 135, in focalPostInitialUpdate
    self._calculateSnapSizeRequirements()
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/DistUpgrade/DistUpgradeQuirks.py", line 566, in _calculateSnapSizeRequirements
    self._prepare_snap_replacement_data()
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/DistUpgrade/DistUpgradeQuirks.py", line 1016, in _prepare_snap_replacement_data
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
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/focal", line 8, in <module>
    sys.exit(main())
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/DistUpgrade/DistUpgradeMain.py", line 238, in main
    if app.run():
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/DistUpgrade/DistUpgradeController.py", line 2089, in run
    return self.fullUpgrade()
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/DistUpgrade/DistUpgradeController.py", line 1926, in fullUpgrade
    if not self.doPostInitialUpdate():
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/DistUpgrade/DistUpgradeController.py", line 924, in doPostInitialUpdate
    self.quirks.run("PostInitialUpdate")
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/DistUpgrade/DistUpgradeQuirks.py", line 99, in run
    func()
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/DistUpgrade/DistUpgradeQuirks.py", line 135, in focalPostInitialUpdate
    self._calculateSnapSizeRequirements()
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/DistUpgrade/DistUpgradeQuirks.py", line 566, in _calculateSnapSizeRequirements
    self._prepare_snap_replacement_data()
  File "/tmp/ubuntu-release-upgrader-6o56cw_s/DistUpgrade/DistUpgradeQuirks.py", line 1016, in _prepare_snap_replacement_data
    stdout=subprocess.PIPE).communicate()
  File "/usr/lib/python3.6/subprocess.py", line 850, in communicate
    stdout = self.stdout.read()
  File "/usr/lib/python3.6/encodings/ascii.py", line 26, in decode
    return codecs.ascii_decode(input, self.errors)[0]
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 1072: ordinal not in range(128)
root@pc1:~>


```

---

### Post by #&amp;thj^% on 2021-01-08
Haven't seen this for quite some time, not sure I can help but show us this please:
```
locale -a
```

---

### Post by anewbie on 2021-01-08
root@pc1:~> locale -a
root@pc1:~> locale -a
C
C.UTF-8
POSIX
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IL
en_IL.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZM
en_ZM.utf8
en_ZW.utf8

---

### Post by #&amp;thj^% on 2021-01-08
Well you do have that,, one more please:
```
locale
```

---

### Post by anewbie on 2021-01-08
see above - i fixed it when i saw my typo.
--
sorry i see you want the current setting:
locale
LANG=
LANGUAGE=en_US:en
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=

---

### Post by #&amp;thj^% on 2021-01-08
That was "locale -a" and thanks for that but now I have to see:
```
locale
```

---

### Post by anewbie on 2021-01-08
see above i posted it ...

---

### Post by #&amp;thj^% on 2021-01-08
Ok I now have a clue, would you try this:
```
sudo locale-gen en_US.UTF-8
export LANG=en_US.UTF-8

``` 
You also may want to add "export" to all the lines that **_"locale -a"_** shows. NOTE: Not "locale" but all in 'locale -a'
****Just a Tip**** if this works, make sure you have no active *PPA's* in your software sources.
Then run:
```
sudo apt update   ###Followed with
sudo apt full-upgrade
sudo apt autoremove
```

---

### Post by anewbie on 2021-01-08
thanks this got it past the error:
locale-gen en_US.UTF-8
export LANG=en_US.UTF-8

---

### Post by anewbie on 2021-01-08
unrelated but one last question - is there a way to disable chromium browser chroot sandbox. I understand the purpose but it makes frequent saving of downloaded objects a pia because they end up in the chroot directory.

---

### Post by #&amp;thj^% on 2021-01-08
> **anewbie said:**
> unrelated but one last question - is there a way to disable chromium browser chroot sandbox. I understand the purpose but it makes frequent saving of downloaded objects a pia because they end up in the chroot directory.

You could disable all sandboxing (for testing) with **"--no-sandbox"**

---

### Post by anewbie on 2021-01-08
thanks again.

---

### Post by #&amp;thj^% on 2021-01-08
Your Welcome.

---

