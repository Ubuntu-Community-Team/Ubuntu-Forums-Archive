---
title: "&quot;Unhandaleable Error Occoured&quot;"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by onewaylimited on 2011-01-12
Every time I try to install a package a message pops up saying "An Unhandlable Error Has Occured" 
IT then says this: **There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.** I am fairly new to ubuntu and i am running 10.10 Gnome. Please help!!!

---

### Post by wkulecz on 2011-01-12
Report the error as it says, often at the launchpad site you will find the solution or a work-around.

---

### Post by onewaylimited on 2011-01-12
I have done this and there is no patch. Any idea how to fix this?

---

### Post by sikander3786 on 2011-01-13
Welcome to the forums :-)

I suspect you are getting this error from Software Center only. It shouldn't appear in Synaptic or apt-get. Any how, please post the output of these commands.

Applications > Accessories > Terminal:

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by onewaylimited on 2011-01-13
For the first one i got:[B] E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]

The second one i got: **dpkg: status database area is locked by another process**

I checked and software center is not running.

---

### Post by onewaylimited on 2011-01-13
I dont know if this helps but, when i get the error and click on the details button, i get this

[SIZE=3][B]Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 769, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 948, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package. 
[/B][/SIZE]

---

### Post by sikander3786 on 2011-01-13
> **onewaylimited said:**
> For the first one i got:[B] E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]

The second one i got: **dpkg: status database area is locked by another process**

I checked and software center is not running.
Please close any other package manager that is running e.g, Software Center, Synaptic or Update Manager and run those commands again.

If no pacakge manager is running and you still get the error, log out and log back in and try those commands.

---

### Post by onewaylimited on 2011-01-13
IT WORKED!!! Thanks very much. I indeed had update manager running and didn't know it. Thanks for the help, your awesome:)

---

### Post by andyit74 on 2011-01-21
> **sikander3786 said:**
> Please close any other package manager that is running e.g, Software Center, Synaptic or Update Manager and run those commands again.

If no pacakge manager is running and you still get the error, log out and log back in and try those commands.

Hi,

I am only new Ubuntu but i was getting the extact same error from the software center and the instructions did not work for me.

Please find screenshots attached. 

The 1st error was displayed relating to ffmpeg when i tried install ubuntu restricted extras

The 2nd error was displayed when i selected Install Anyway

Any answers would be much appreciated

---

