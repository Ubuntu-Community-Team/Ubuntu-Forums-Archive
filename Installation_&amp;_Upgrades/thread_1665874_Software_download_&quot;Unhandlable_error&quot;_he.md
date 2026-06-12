---
title: "Software download &quot;Unhandlable error&quot; help!"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by Redding on 2011-01-12
Hello...
tried to install some things from Software Center and continue to get this error below:

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 769, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 948, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

What gives? I'm still REALLY to new to Linux, so please help and for the love of God......be gentle. Thanks! :D

---

### Post by sikander3786 on 2011-01-13
Try these commands and post the output.

Applications > Accessories > Terminal:

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by Redding on 2011-01-13
**Hello, **

**Output for first command is:**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ttf-mscorefonts-installer
The following packages will be upgraded:
  ttf-mscorefonts-installer
1 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
1 not fully installed or removed.
Need to get 0B/40.3kB of archives.
After this operation, 221kB of additional disk space will be used.
Do you want to continue [Y/n]? 

[B]I clicked Yes. Now...I believe this is where I got jammed up last time and what caused the problem. After clicking Yes, I get a long disclaimer titled "Configuring ttf-mscorefonts-installer " 
Now....the only problem is this.....HOW THE HECK DO i CHOOSE <OK> AT THE END OF THIS DISCLAIMER? What I mean is this....it gives me the  <OK> option of the disclaimer, but I can't do anything with it. Can't click it, etc.....so I just ended up  exiting the window.
I haven't tried the second command yet. Sorry this is so long and thanks for the help so far.

[/B]

---

### Post by sikander3786 on 2011-01-13
I think you might need to press <TAB> and then hit <Enter>.

---

### Post by Redding on 2011-01-13
Told you that I was a Linux virgin. Problem solved. Now I feel silly. Thanks for your help, man.

---

### Post by chrisetlo on 2011-01-14
Ahhhhh!  That's been driving me crazy, too.  Thanks!

---

### Post by Snigelmannen on 2011-01-29
> **sikander3786 said:**
> I think you might need to press <TAB> and then hit <Enter>. Not that used to Linux, just installed it again due to my work, this helped alot ;) Thanks

---

