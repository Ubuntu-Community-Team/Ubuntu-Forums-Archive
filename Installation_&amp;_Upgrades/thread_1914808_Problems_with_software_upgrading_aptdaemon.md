---
title: "Problems with software upgrading: aptdaemon"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by theKuch on 2012-01-25
When I tried to upgrade the ubuntu s/w, I received the following error messages:

================================================================
An unhandleable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Details: 
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:The package index files are corrupted. No Filename: field for package ubufox.
================================================================

Any ideas what may be causing this?

Thanks

---

### Post by cortman on 2012-01-25
> **theKuch said:**
> When I tried to upgrade the ubuntu s/w, I received the following error messages:

================================================================
An unhandleable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Details: 
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:The package index files are corrupted. No Filename: field for package ubufox.
================================================================

Any ideas what may be causing this?

Thanks

Apparently your packages are a bit out of whack. Try running

```
sudo apt-get install -f
```

and

```
sudo apt-get update
```

And post the results here, if you get an error. Good luck!

---

### Post by theKuch on 2012-01-25
Thanks, but it didn't seem to loke that :-(

me@Ubuntu:~$ sudo apt-get install -f
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgladeui-1-11 libhighgui2.2 linux-headers-3.0.0-12 libcvaux2.2 libunicap2
  linux-headers-3.0.0-12-generic-pae libcv2.2 oxygen-cursor-theme
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 146 not upgraded.

me@Ubuntu:~$ sudo apt-get autoremove
Unknown id: apt-get
me@Ubuntu:~$

---

### Post by cortman on 2012-01-25
Hm... It looks as though ubufox is causing trouble. Try uninstalling it and (if you want) reinstalling it-

```
sudo apt-get purge ubufox
sudo apt-get install ubufox
```

---

### Post by theKuch on 2012-01-25
[COLOR=Sienna]Maybe more is corrupted.[/COLOR]

sudo apt-get purge ubufox
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubufox*
0 upgraded, 0 newly installed, 1 to remove and 165 not upgraded.
After this operation, 41.0 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 226411 files and directories currently installed.)
Removing ubufox ...
me@Ubuntu:~$ sudo apt-get install ubufox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ubufox
0 upgraded, 1 newly installed, 0 to remove and 165 not upgraded.
E: The package index files are corrupted. No Filename: field for package ubufox.
me@Ubuntu:~$

---

### Post by cortman on 2012-01-25
Ok, run this, but copy/paste so you don't total your system!

```
sudo rm /var/lib/apt/lists/*
sudo apt-get update
```

---

### Post by theKuch on 2012-01-25
[COLOR=Sienna]Didn't like that!

[COLOR=Black]sudo rm /var/lib/apt/lists/*
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
[/COLOR]
[/COLOR]

---

### Post by theKuch on 2012-01-25
me@Ubuntu:~$ sudo ls /var/lib/apt/lists/
partial

and partial is an empty directory

---

### Post by cortman on 2012-01-25
> **theKuch said:**
> me@Ubuntu:~$ sudo ls /var/lib/apt/lists/
partial

and partial is an empty directory

```
sudo rm -r /var/lib/apt/lists/partial
```

Then run the update and see if that fixes it.

---

### Post by theKuch on 2012-01-25
Great -- seems to be working now!  Thanks!!!

---

### Post by cortman on 2012-01-25
> **theKuch said:**
> Great -- seems to be working now!  Thanks!!!

Great! Mark this thread as [SOLVED], using the thread tools, if you would. Have fun with Ubuntu!

---

