---
title: "Failed upgrade from 14.10 to 15.04 - UnicodeDecodeError: 'utf-8'"
date: 2015-04-29
forum: Installation &amp; Upgrades
---

### Post by Andrei_Tarkovsky on 2015-04-29
Good afternoon. 

I have repeatedly tried to upgrade from 14.10 server to 15.04, only to fail miserably, no matter what I did. 
[B]
I am without ideas. Anything is greatly appreciated. Thank you!
[/B]
The error I receive from do-dist-upgrade is :

> A fatal error occurred

Please report this as a bug and include the files
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in
your report. The upgrade has aborted.
Your original sources.list was saved in
/etc/apt/sources.list.distUpgrade.

Traceback (most recent call last):

File "/tmp/ubuntu-release-upgrader-zaemm4gk/vivid", line 8, in
<module>
sys.exit(main())

File
"/tmp/ubuntu-release-upgrader-zaemm4gk/DistUpgrade/DistUpgradeMain.py",
line 240, in main
if app.run():

File
"/tmp/ubuntu-release-upgrader-zaemm4gk/DistUpgrade/DistUpgradeController.py",
line 1831, in run
return self.fullUpgrade()

File
"/tmp/ubuntu-release-upgrader-zaemm4gk/DistUpgrade/DistUpgradeController.py",
line 1712, in fullUpgrade
if not self.doPostInitialUpdate():

File
"/tmp/ubuntu-release-upgrader-zaemm4gk/DistUpgrade/DistUpgradeController.py",
line 898, in doPostInitialUpdate
self.tasks = self.cache.installedTasks

File
"/tmp/ubuntu-release-upgrader-zaemm4gk/DistUpgrade/DistUpgradeCache.py",
line 778, in installedTasks
for line in pkg._pcache._records.record.split("\n"):

UnicodeDecodeError: 'utf-8' codec can't decode byte 0xae in position
337: invalid start byte

Regarding locale : 

> root@1:~# locale
LANG=en_US.UTF-8
LANGUAGE=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=en_US.UTF-8

Regarding locale - a

> root@1:~# locale -a
C
C.UTF-8
en_US.utf8
POSIX
root@sd-70379:~#


---

### Post by bapoumba on 2015-04-29
Please post the outputs to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by Andrei_Tarkovsky on 2015-04-30
> 
root@1:~# cat -n /etc/apt/sources.list
     1  # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     2  # newer versions of the distribution.
     3  deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) utopic main restricted
     4  deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) utopic main restricted
     5
     6  ## Major bug fix updates produced after the final release of the
     7  ## distribution.
     8  deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) utopic-updates main restricted
     9  deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) utopic-updates main restricted
    10
    11  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12  ## team. Also, please note that software in universe WILL NOT receive any
    13  ## review or updates from the Ubuntu security team.
    14  deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) utopic universe
    15  deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) utopic universe
    16  deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) utopic-updates universe
    17  deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) utopic-updates universe
    18
    19  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    20  ## team, and may not be under a free licence. Please satisfy yourself as to
    21  ## your rights to use the software. Also, please note that software in
    22  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    23  ## security team.
    24  deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) utopic multiverse
    25  deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) utopic multiverse
    26  deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) utopic-updates multiverse
    27  deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) utopic-updates multiverse
    28
    29  ## N.B. software from this repository may not have been tested as
    30  ## extensively as that contained in the main release, although it includes
    31  ## newer versions of some applications which may provide useful features.
    32  ## Also, please note that software in backports WILL NOT receive any review
    33  ## or updates from the Ubuntu security team.
    34  deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) utopic-backports main restricted universe multiverse
    35  deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) utopic-backports main restricted universe multiverse
    36
    37  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security main restricted
    38  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security main restricted
    39  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security universe
    40  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security universe
    41  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security multiverse
    42  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security multiverse
    43
    44  ## Uncomment the following two lines to add software from Canonical's
    45  ## 'partner' repository.
    46  ## This software is not part of Ubuntu, but is offered by Canonical and the
    47  ## respective vendors as a service to Ubuntu users.
    48  # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) utopic partner
    49  # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) utopic partner
    50
    51  ## This software is not part of Ubuntu, but is offered by third-party
    52  ## developers who want to ship their latest software.
    53  # deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) utopic main
    54  # deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) utopic main


> 
root@1:~# ls -la /etc/apt/sources.list.d
total 8
drwxr-xr-x 2 root root 4096 Oct 17  2014 .
drwxr-xr-x 6 root root 4096 Apr 29 16:42 ..


> 
root@1:~# tail -v -n +1 /etc/apt/sources.list.d/*
tail: cannot open â/etc/apt/sources.list.d/*â for reading: No such file or directory


Thank you, bapoumba.

---

### Post by bapoumba on 2015-04-30
```
â/etc/apt/sources.list.d/*â
```
What is this ? That probably what is blocking you.

---

### Post by Andrei_Tarkovsky on 2015-05-01
bapoumba, I have no ideea. Any sugestion? (If relevant, initially, the locale also had french installed, but I removed it).

Thanks.

---

### Post by bapoumba on 2015-05-02
I have no idea either. I do have French and English set up here.
ls does not find anything but tail fails on a non existing file with the â character at the beginning and at the end of the file name. Would that char replace space in the terminal for some reason ?
Edit : or in your .bashrc file ?


When I look for zaemm4gk, I do not find anything but your thread. Do you know what this is ?

---

