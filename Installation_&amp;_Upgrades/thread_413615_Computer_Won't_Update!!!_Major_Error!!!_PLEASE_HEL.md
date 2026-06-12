---
title: "Computer Won't Update!!! Major Error!!! PLEASE HELP!!!"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by smartboyathome on 2007-04-19
I tried updating my system from 6.06 to 6.10, but python2.4-minimalist crashed it. Then, I tried reinstalling it, and it removed a whole bunch of packages (then crashed it).  Now I get this error:

> 
Could not launch menu item

Details: Failed to execute child process "gksu" (No such file or directory)


I get this when I try to open the terminal, the synaptics manager, and who knows where else this will pop up... HELP!!!

---

### Post by smartboyathome on 2007-04-19
Someone please help me!!! I can't access any of my Administration stuff!!!

---

### Post by Podex on 2007-04-19
In a terminal try

```
sudo apt-get install gksu
```

to (re)install gksu

---

### Post by smartboyathome on 2007-04-19
Python2.4-minimalist messed it up again...

Here is the error:
> 
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libgksu2-0 xbase-clients xutils xutils-dev
The following NEW packages will be installed:
  gksu libgksu2-0 xbase-clients xutils xutils-dev
0 upgraded, 5 newly installed, 0 to remove and 1171 not upgraded.
3 not fully installed or removed.
Need to get 0B/435kB of archives.
After unpacking, 2589kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python2.4-minimal (2.4.4~c1-0ubuntu1) ...
Linking and byte-compiling packages for runtime python2.4...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1373, in ?
    main()
  File "/usr/bin/pycentral", line 1363, in main
    if action.check_args(global_options):
  File "/usr/bin/pycentral", line 971, in check_args
    for rt in get_installed_runtimes():
  File "/usr/bin/pycentral", line 195, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 129, in default_version
    if not _default_version in (debian_default, os.path.join('/usr/bin', debian_default)):
  File "/usr/lib/python2.4/posixpath.py", line 60, in join
    if b.startswith('/'):
AttributeError: 'NoneType' object has no attribute 'startswith'
dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python2.4-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by Podex on 2007-04-19
Try

```
sudo dpkg --clear-avail
```

I just saw it in another thread :P

Then try

```
sudo apt-get update && sudo apt-get upgrade
```

Btw, how did you try upgrading from 6.06 to 6.10?

---

### Post by smartboyathome on 2007-04-19
The official meathod. It deleted itself while upgrading...

---

### Post by smartboyathome on 2007-04-19
i got the same error using that code as I did above...

---

### Post by Podex on 2007-04-19
So you used gksu "update-manager -c"  ?
You could also use apt-get to dist-upgrade. From what I can tell you haven't been upgraded to Edgy.
Here is a page how to do it: [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

If that python2.4-minimal is still bitching you could try to hold the current version with
```
sudo aptitude hold python2.4-minimal
```
but I'm not sure if that is a good idea because it could break more dependencies.

---

### Post by smartboyathome on 2007-04-19
Actually, I am soooo desperate, I removed it completely. Now, it is removing almost EVERYTHING, including ubuntu-base and ubuntu-minimal!!!

---

### Post by smartboyathome on 2007-04-19
Now, it is removing practically everything on my system... :'(

---

### Post by smartboyathome on 2007-04-19
It IS removing every program on my system!!! NOOOOOOOOOOOO!

---

### Post by Podex on 2007-04-19
Ctrl-Z, Ctrl-C !! :O:O

---

### Post by smartboyathome on 2007-04-19
It already removed all my programs AND the OS. I had to reinstall everything...

---

