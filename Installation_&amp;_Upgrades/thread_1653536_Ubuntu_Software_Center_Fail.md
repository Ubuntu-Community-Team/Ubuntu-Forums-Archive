---
title: "Ubuntu Software Center Fail"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by hexadecimal83 on 2010-12-27
Hey guys, I have been using Ubuntu since version 9 and have never ran across any unmanageable problems until now. All of a sudden I cannot download any software or applications from the Ubuntu software center. I can sudo anything, I just cant use the gui from the software center itself. I just get the following error: 

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 938, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

Please advise. Any input is much appreciated, 

Hexadecimal83

---

### Post by QIII on 2010-12-27
Have a look here

[https://bugs.launchpad.net/aptdaemon/+bug/659438](https://bugs.launchpad.net/aptdaemon/+bug/659438)

towards the bottom.  

If it is any consolation, I had something very similar happen with yum in Fedora.

---

### Post by sikander3786 on 2010-12-27
Welcome to the forums :-)

From Applications > Accessories > Terminal, post the output of these commands.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

