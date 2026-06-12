---
title: "Cannot upgrade to 19.04 from 18.10"
date: 2019-04-20
forum: Installation &amp; Upgrades
---

### Post by jkcclemens on 2019-04-20
[Here]("https://paste.gg/p/jkcclemens/f8877c0f0e7948d89571d8bdc113b985") is a link to the process I used. After do-release-upgrade fails, I restore the old sources files. Unfortunately, I can't figure out what's going wrong.

How do I fix this so I can upgrade?

---

### Post by Frogs Hair on 2019-04-20
Welcome jkcclemens:

What are you using opensuse and Debian stable repositories for ? Mixing repositories from different distributions is not a good idea and package dependencies from these repositories could be the source of the problem even though they were disabled during the upgrade.

---

### Post by jkcclemens on 2019-04-20
That openSUSE repo is specifically for Ubuntu (they host repositories) for the Albert program. The other two are for Riot, which isn't even installed now, and Yarn, which is compatible. I appreciate your response and concern, but I find it highly unlikely that those are the problem, especially considering that third-party repositories are disabled, and I would see a package conflict if their requirements conflicted, not whatever this error is.

---

### Post by Frogs Hair on 2019-04-20
This part of the output gives a starting point these errors are noted on various forums. 

```
  [B][U] Error in sys.excepthook:
    [/U][/B]
Traceback (most recent call last):
    
  **_File "/usr/lib/python3/dist-packages/problem_report.py_**", line 497, in add_to_existing
    
    self.write(f)
    
  File "/usr/lib/python3/dist-packages/problem_report.py", line 450, in write
    
    block = f.read(1048576)
    
  File "/usr/lib/python3.6/codecs.py", line 321, in decode
    
    (result, consumed) = self._buffer_decode(data, self.errors, final)
    
UnicodeDecodeError: 'utf-8' codec can't decode byte 0x8b in position 1: invalid start byte
    
 
    
Original exception was:
    
Traceback (most recent call last):
    
  File "/tmp/ubuntu-release-upgrader-ulyhdapj/disco", line 8, in <module>
    
    sys.exit(main())
    
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeMain.py", line 238, in main
    
    if app.run():
    
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeController.py", line 2085, in run
    
    return self.fullUpgrade()
    
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeController.py", line 1946, in fullUpgrade
    
    self.openCache(restore_sources_list_on_fail=True)
    
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeController.py", line 215, in openCache
    
    return self._openCache(lock)
    
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeController.py", line 243, in _openCache
    
    lock)
    
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeCache.py", line 140, in __init__
    
    apt.Cache.__init__(self, progress)
    
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 138, in __init__
    
    self.open(progress)
    
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 198, in open
    
    self._cache = apt_pkg.Cache(progress)
    
apt_pkg.Error: E:The value 'cosmic' is invalid for APT::Default-Release as such a release is not availab
    
le in the sources
```

---

### Post by jkcclemens on 2019-04-20
Searching for 

```

apt_pkg.Error: E:The value 'cosmic' is invalid for APT::Default-Release as such a release is not available in the sources

```

did not show me any relevant issues to my situation when I searched. Coming here was my last resort; if I hadn't already attempted to search for a solution, I wouldn't be here. Presumably you searched and found information in order to tell me that I should search. Did you consider sharing with me what you found instead of just telling me to find it myself after I already tried?

I came to these forums for help, and I appreciate you taking time to respond to me, but you have yet to actually provide any actionable suggestions or ideas. I'm not sure why any trace of cosmic is left, as do-release-upgrade changes all lines in the apt sources that contain cosmic to contain disco instead. I've searched for "cosmic" in all of /etc/apt and not found anything to change. I'm not sure where the error is coming from, and I have been unable to find relevant information searching for the error.

---

### Post by jkcclemens on 2019-04-20
Alright, so if anyone finds this issue, I eventually managed to solve it myself through dumb luck. I decided to have grep search symlinks too in /etc/apt, and I found that there was a symlinked file at /etc/apt/apt.conf.d/01-vendor-ubuntu that contained the offending line. I added .bak to the end of the file and ran do-release-upgrade. It appears to be upgrading fine now. As far as I can tell, you cannot change that file to say disco instead of cosmic before, during, or after do-release-upgrade, so just rename it. I imagine it can be removed. Whatever you do, don't come here and ask for support; you'll just get red herrings and told to search harder.

---

