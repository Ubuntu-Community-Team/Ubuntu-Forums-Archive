---
title: "apt package list error"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by vkkim on 2007-05-12
I just upgraded to Feisty, and when I run "aptitude update" or any of its varients I get:

```
Fetched 10B in 1s (6B/s) 
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: Error occurred while processing python-musicbrainz2 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: Error occurred while processing python-musicbrainz2 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: Error occurred while processing python-musicbrainz2 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

---

### Post by jfinkels on 2007-05-12
Maybe try to remove or reinstall python-musicbrainz? ```
sudo aptitude reinstall python-musicbrainz2
```

If that doesn't work, try ```
sudo apt-get -f install
```

---

### Post by vkkim on 2007-05-12
Both result in:
```
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: Error occurred while processing python-musicbrainz2 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

---

### Post by bapoumba on 2007-05-12
```
df -H
```
To see if this "run out of room" actually means one of your partition is full.

```
sudo aptitude clean
```
Will make some room in your root (/) partition.
Clean up your /home too.

---

### Post by vkkim on 2007-05-12
Yup, first thing I checked, still have a good 50 gigs or so left.

---

### Post by taurus on 2007-05-12
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by bapoumba on 2007-05-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/debian/+source/apt/+bug/24626](https://bugs.launchpad.net/debian/+source/apt/+bug/24626) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				```
$ sudo apt-get update -o APT::Cache-Limit=25165824
```

---

### Post by vkkim on 2007-05-14
> **bapoumba said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/debian/+source/apt/+bug/24626](https://bugs.launchpad.net/debian/+source/apt/+bug/24626) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				```
$ sudo apt-get update -o APT::Cache-Limit=25165824
```

That did the trick, thanks!

---

### Post by bapoumba on 2007-05-15
Your welcome!

---

### Post by ukjmn on 2007-06-20
had this same problem! thanks much!

---

### Post by yellat on 2007-07-25
I have been having a bit of trouble updating recently and was wondering if someone could point out what I'm doing wrong.  I have tried the solutions listed in this thread as they seemed relevant to the problem I am having, as well as the recommended update method. This is driving me a bit nuts.

> \warning: could not initiate dbus
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 87, in ?
    app.main(options)
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 960, in main
    self.fillstore()
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 808, in fillstore
    self.initCache()
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 898, in initCache
    self.cache = MyCache(progress)
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 90, in __init__
    apt.Cache.__init__(self, progress)
  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 36, in __init__
    self.open(progress)
  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 53, in open
    self._cache = apt_pkg.GetCache(progress)
SystemError: E:Dynamic MMap ran out of room, E:Error occurred while processing sbcl (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.



edit - another error message that results
> E: Dynamic MMap ran out of room
E: Error occurred while processing libgd2-noxpm (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


---

### Post by acidtop on 2007-07-31
ran into the same problem
E:Dynamic MMap ran out of room, E:Dynamic MMap ran out of room, E:Error occurred while processing acroread-plugins (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/medibuntu.sos-sts.com_repo_dists_feisty_non-free_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.
checked df  -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               20G   3.7G    15G  20% /
varrun                 164M    99k   164M   1% /var/run
varlock                164M      0   164M   0% /var/lock
procbususb             164M    87k   164M   1% /proc/bus/usb
udev                   164M    87k   164M   1% /dev
devshm                 164M      0   164M   0% /dev/shm
lrm                    164M    35M   130M  22% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1               57G    34G    21G  63% /media/60gig
looks like i have plenty of room avalible
i ran sudo apt-get update -o APT::Cache-Limit=25165824
then i got an erro message E: Line 1 too long (max 1024)
I am asuming that this means i added to much 
ran into a wall dont know how to fix 
any ides?

---

### Post by nrweber on 2007-08-07
Found this on another forum and it worked for me....

sudo rm -vf /var/lib/apt/lists/*

after I did that I was able to update and upgrade :^)

---

