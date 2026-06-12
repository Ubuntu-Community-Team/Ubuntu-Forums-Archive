---
title: "Package corruption"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by originalchoice on 2011-01-08
Hello everyone. 

I tried to install ffmpeg for Firefox videodownloader addon but did some nasty damage. First of all, I followed this guide: [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

I'm using Ubuntu 10.10 Maverick 32-bit version

The installation froze after this: 
> Unpacking replacement x11proto-core-dev ...Couldn't find anyone having the same issue on the net, so I just exited the terminal and then I couldn't do anything anymore. When I tried to install again (or remove) that thingy, i got this in console:

> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?Then I typed this and tried to remove that package again:
> sudo rm /var/lib/dpkg/lockIt returned this:
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.Did that and tried again. Then i received this:
> originalchoice@mikua:~$ sudo apt-get remove x11proto-core.dev
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Note, selecting 'x11proto-core-dev' for regex 'x11proto-core.dev'
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  x11proto-core-dev
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
Used this to remove the lock:
> sudo pkill aptTried again:
> originalchoice@mikua:~$ sudo apt-get remove x11proto-core.dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'x11proto-core-dev' for regex 'x11proto-core.dev'
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  x11proto-core-dev
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing x11proto-core-dev (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 x11proto-core-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
So, when trying to reinstall it hangs on the 'unpacking replacement blahblahblah'. On top of that, I cannot install anything in Software center either. I receive an error:
> **An unhandlable error occured**.
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

*Details*:

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 769, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 948, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the x11proto-core-dev package. This might mean you need to manually fix this package.
Well, that's pretty much it.. If i'm missing anything, please let me know. Hope you can help me with this dubious enterprise.. :(

---

### Post by dino99 on 2011-01-08
all the packages you need can be found into synaptic (system admin synaptic)

[http://packages.ubuntu.com/fr/maverick/gstreamer0.10-ffmpeg](http://packages.ubuntu.com/fr/maverick/gstreamer0.10-ffmpeg)

into synaptic, select & install: gstreamer0.10-ffmpeg

that it, nothing else :)

Ubuntu is designed for HUMAN

note: dont follow the oldish(and no more maintained) threads/howto

---

### Post by originalchoice on 2011-01-08
Thank you, that solved everything. Will use synaptic from now on))

---

### Post by FakeOutdoorsman on 2011-01-08
> **dino99 said:**
> note: dont follow the oldish(and no more maintained) threads/howto

If you are referring to the thread originalchoice mentioned then you would be mistaken on the assumption that it is old and unmaintained.

---

