---
title: "Install RELEASE and Software Manager are tweaking out."
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by AlmondOK on 2011-05-26
I installed Natty Narwhal from a pendrive I set up, which was a bit of a messy install to begin with. However, after booting into Ubuntu, this application called "Install RELEASE" appears. When I run it, it shows up just like I'm installing Ubuntu again. After following it through, it will stop and say that it must unmount /. It offers two options, Go Back, or Continue. Picking either does nothing. This hasn't seemed too big an issue. I can still run it fine. However, the Software Centre is an issue. Whenever I try to download something from it, I get this error:

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.

Any ideas?

---

### Post by mörgæs on 2011-05-26
Hi, welcome to the fora.

You could try to boot the computer and run the commands

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```In any error message appears, please post it.

---

### Post by AlmondOK on 2011-05-26
The first two went off without a hitch. The third one prompted me with this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.

I typed it in, it requested to install sun-java6.
After it finished, I went to the Software Centre, and I could download and install new applications. Thanks for the help! What a wonderful welcome this has been!

---

### Post by mörgæs on 2011-05-26
You are welcome. This is just 'Ubuntu' :-)

Please mark the thread 'solved' using 'thread tools'. It will help people searching for an answer.

---

