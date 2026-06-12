---
title: "There seems to be a programming error in aptdaemon"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by renfr on 2011-05-23
Hello,
today I wanted to install a new software through the ubuntu software center and when I click on install it gives me a box saying this :
> There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.In details I've got that :
 > Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the gstreamer0.10-ffmpeg package. This might mean you need to manually fix this package.I tried installing random software and the problem still appears.
According to what I see in details I know probably why this happens, saturday I wanted to listen to a .mp3 on my web browser and it asked me to install components such as the gstreamer ffmpeg package but it didn't install properly as the process hanged up while decompressing that latter so I just restarted the computer and now this error is affecting the ubuntu software center.

Any help on that? I'm a complete noob in ubuntu and I have no idea on how to solve that problem.
Thanks in advance.

---

### Post by renfr on 2011-05-24
up

---

