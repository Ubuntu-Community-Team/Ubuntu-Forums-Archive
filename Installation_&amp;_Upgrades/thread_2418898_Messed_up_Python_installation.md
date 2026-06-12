---
title: "Messed up Python installation"
date: 2019-05-13
forum: Installation &amp; Upgrades
---

### Post by utah777 on 2019-05-13
All I can show is two error messages I have in my terminal:

```
15:37:11 ~$ sudo dpkg --configure -a
[sudo] password for sergey: 
dpkg: error processing package python-pip (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package bleachbit (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-libxslt1 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-debian (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on python-debian; however:
  Package python-debian is not configured yet.


dpkg: error processing package update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on python-debian; however:
  Package python-debian is not configured yet.


dpkg: error processing package update-notifier-common (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-pip
 bleachbit
 python-libxslt1
 python-debian
 update-notifier
 update-notifier-common

```

```
15:44:31 ~$ sudo aptitude reinstall python-minimal
The following packages will be REINSTALLED:
  python-minimal 
The following partially installed packages will be configured:
  bleachbit python-debian python-pip update-notifier update-notifier-common 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0 B/300 kB of archives. After unpacking 0 B will be used.
E: Can't find a source to download version '1.1.28-2ubuntu0.1' of 'python-libxslt1:amd64'
E: Can't find a source to download version '1.1.28-2ubuntu0.1' of 'python-libxslt1:amd64'
E: Internal error: couldn't generate list of packages to download

```

It seems I messed up my python installation after playing with symbolic links.

On top of that, I have:

```
15:45:34 ~$ env python
Python 3.6.7 | packaged by conda-forge | (default, Feb 20 2019, 02:51:38) 
[GCC 7.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```

which means I have broken applications dependant on python2, e.g. bleachbit. Though, I am not sure if it;s amenable with these lines in `.bashrc` put by Anaconda distribution:

```
# added by Anaconda3 4.3.1 installer
export PATH="/home/sergey/anaconda3/bin:$PATH"

```
I would be very grateful to restoring python environment and removing `apt-get` errors.

---

### Post by dino99 on 2019-05-13
A few ideas and solutions already used :
[https://askubuntu.com/questions/141370/how-to-fix-a-broken-package-when-apt-get-install-f-does-not-work](https://askubuntu.com/questions/141370/how-to-fix-a-broken-package-when-apt-get-install-f-does-not-work)

---

### Post by utah777 on 2019-05-13
```
sudo rm -rf /var/lib/dpkg/updates/*
sudo rm -rf /var/lib/apt/lists/*
sudo rm /var/cache/apt/*.bin
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update

16:17:42 ~$ sudo dpkg --configure -a
dpkg: error processing package python-pip (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package bleachbit (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-libxslt1 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-debian (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on python-debian; however:
  Package python-debian is not configured yet.


dpkg: error processing package update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on python-debian; however:
  Package python-debian is not configured yet.


dpkg: error processing package update-notifier-common (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-pip
 bleachbit
 python-libxslt1
 python-debian
 update-notifier
 update-notifier-common

```


```

16:20:48 ~$ sudo dpkg --remove --force-remove-reinstreq python-libxslt1
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
(Reading database ... 448240 files and directories currently installed.)
Removing python-libxslt1 (1.1.28-2ubuntu0.1) ...
  File "/usr/bin/pyclean", line 57
    pyfile = (yield)
                  ^
SyntaxError: invalid syntax
dpkg: error processing package python-libxslt1 (--remove):
 subprocess installed pre-removal script returned error exit status 1
  File "/usr/bin/pycompile", line 69
    with file(join(name, fn), 'r') as lines:
            ^
SyntaxError: invalid syntax
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 python-libxslt1

```

Does not seem to work.

---

### Post by dino99 on 2019-05-13
Next step: edit and remove the related faulty packages entries listed above from (use the search feature to find them):

> sudo gedit /var/lib/dpkg/status

and logout/in and update/upgrade again.
Note: also be sure to only use genuine lubuntu packages to avoid conflicts/incompatibilities

---

### Post by rsteinmetz70112 on 2019-05-13
Try :

```
sudo dpkg --configure -a
sudo apt install -f
```
If that doesn't work try
```
sudo apt install --reinstall <package name>
```
For each package listed in the error messages.
After reinstallation run the commands above again to confirm everything is OK.
This may not work if you have some bad links that are not overwritten by the reinstall.

---

### Post by utah777 on 2019-05-13
```
18:09:22 ~$ sudo apt install --reinstall python-pip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python-libxslt1
The following packages will be upgraded:
  python-libxslt1
1 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0 B/431 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 449220 files and directories currently installed.)
Preparing to unpack .../python-libxslt1_1.1.28-2ubuntu0.2_amd64.deb ...
  File "/usr/bin/pyclean", line 57
    pyfile = (yield)
                  ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 57
    pyfile = (yield)
                  ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-libxslt1_1.1.28-2ubuntu0.2_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
  File "/usr/bin/pycompile", line 69
    with file(join(name, fn), 'r') as lines:
            ^
SyntaxError: invalid syntax
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-pip_1.5.4-1ubuntu4_all.deb ...
  File "/usr/bin/pyclean", line 57
    pyfile = (yield)
                  ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 57
    pyfile = (yield)
                  ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-pip_1.5.4-1ubuntu4_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
  File "/usr/bin/pycompile", line 69
    with file(join(name, fn), 'r') as lines:
            ^
SyntaxError: invalid syntax
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-libxslt1_1.1.28-2ubuntu0.2_amd64.deb
 /var/cache/apt/archives/python-pip_1.5.4-1ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
18:10:06 ~$ 

```

---

### Post by rsteinmetz70112 on 2019-05-13
Have you tried reinstalling python-libxslt?
It seems to be the common thread of all the errors.
My next candidate would be python-debian

---

### Post by #&amp;thj^% on 2019-05-13
This has worked for me: 
```

sudo mv /var/lib/dpkg/info/<packagename>.* /tmp/
sudo dpkg --remove --force-remove-reinstreq <packagename>
sudo apt remove <packagename>
sudo apt autoremove && sudo apt autoclean
```

And if that still leaves you in the same state try:
```
sudo apt install --reinstall python-debian python3-debian python-chardet python3-chardet
```

Good Luck

---

### Post by utah777 on 2019-05-13
> **dino99 said:**
> Next step: edit and remove the related faulty packages entries listed above from (use the search feature to find them):



and logout/in and update/upgrade again.
Note: also be sure to only use genuine lubuntu packages to avoid conflicts/incompatibilities

Removed all the culprits from `[COLOR=#000000]*/var/lib/dpkg/status*[/COLOR]`, still:[COLOR=#000000][I]
[/I][/COLOR]
```
18:55:28 ~$ sudo dpkg --configure -a
18:56:22 ~$ sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-debian update-notifier update-notifier-common
The following NEW packages will be installed:
  python-debian update-notifier update-notifier-common
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 211 kB/261 kB of archives.
After this operation, 2,692 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main update-notifier-common all 0.154.1ubuntu6 [165 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main update-notifier amd64 0.154.1ubuntu6 [46.4 kB]
Fetched 211 kB in 0s (220 kB/s)           
Selecting previously unselected package python-debian.
(Reading database ... 448713 files and directories currently installed.)
Preparing to unpack .../python-debian_0.1.21+nmu2ubuntu2_all.deb ...
Unpacking python-debian (0.1.21+nmu2ubuntu2) ...
Selecting previously unselected package update-notifier-common.
Preparing to unpack .../update-notifier-common_0.154.1ubuntu6_all.deb ...
Unpacking update-notifier-common (0.154.1ubuntu6) ...
Selecting previously unselected package update-notifier.
Preparing to unpack .../update-notifier_0.154.1ubuntu6_amd64.deb ...
Unpacking update-notifier (0.154.1ubuntu6) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1.1) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1.1) ...
Segmentation fault (core dumped)
Setting up python-debian (0.1.21+nmu2ubuntu2) ...
  File "/usr/bin/pycompile", line 69
    with file(join(name, fn), 'r') as lines:
            ^
SyntaxError: invalid syntax
dpkg: error processing package python-debian (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on python-debian; however:
  Package python-debian is not configured yet.


dpkg: error processing package update-notifier-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-notifier-common (= 0.154.1ubuntu6); however:
  Package update-notifier-common is not configured yet.
 update-notifier depends on python-debian; however:
  Package python-debian is not configured yet.


dpkg: error processing package update-notifier (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
      No apport report written because the error message indicates its a followup error from a previous failure.
            Errors were encountered while processing:
 python-debian
 update-notifier-common
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)
18:56:46 ~$ 

```

---

### Post by utah777 on 2019-05-13
> **rsteinmetz70112 said:**
> Have you tried reinstalling python-libxslt?
It seems to be the common thread of all the errors.
My next candidate would be python-debian

Tried reinstalling both, the only luck so far with `python-libxslt`, 

```
dpkg: error processing package python-debian (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on python-debian; however:
  Package python-debian is not configured yet.
```

---

### Post by utah777 on 2019-05-13
> **1fallen said:**
> This has worked for me: 
```

sudo mv /var/lib/dpkg/info/<packagename>.* /tmp/
sudo dpkg --remove --force-remove-reinstreq <packagename>
sudo apt remove <packagename>
sudo apt autoremove && sudo apt autoclean
```

And if that still leaves you in the same state try:
```
sudo apt install --reinstall python-debian python3-debian python-chardet python3-chardet
```

Good Luck

Still:

```
19:06:36 ~$ sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up python-debian (0.1.21+nmu2ubuntu2) ...
  File "/usr/bin/pycompile", line 69
    with file(join(name, fn), 'r') as lines:
            ^
SyntaxError: invalid syntax
dpkg: error processing package python-debian (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on python-debian; however:
  Package python-debian is not configured yet.


dpkg: error processing package update-notifier-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-notifier-common (= 0.154.1ubuntu6); however:
  Package update-notifier-common is not configured yet.
 update-notifier depends on python-debian; however:
  Package python-debian is not configured yet.


dpkg: error processing package update-notifier (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
      No apport report written because the error message indicates its a followup error from a previous failure.
            Errors were encountered while processing:
 python-debian
 update-notifier-common
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)
19:07:06 ~$ 

```

---

### Post by #&amp;thj^% on 2019-05-13
This baby has really dug-in hasn't it. :)
Can you us show us this:
```
dpkg -S /usr/lib/python2.7/optparse.py
dpkg -V libpython2.7-minimal
readlink -f /usr/lib/python2.7/optparse.py
```

---

### Post by utah777 on 2019-05-13
> **1fallen said:**
> This baby has really dug-in hasn't it. :)
Can you us show us this:
```
dpkg -S /usr/lib/python2.7/optparse.py
dpkg -V libpython2.7-minimal
readlink -f /usr/lib/python2.7/optparse.py
```


```
19:17:02 ~$ dpkg -S /usr/lib/python2.7/optparse.py
libpython2.7-minimal:amd64: /usr/lib/python2.7/optparse.py
19:18:10 ~$ dpkg -V libpython2.7-minimal
19:18:22 ~$ readlink -f /usr/lib/python2.7/optparse.py
/usr/lib/python2.7/optparse.py
19:18:31 ~$ 

```

---

### Post by #&amp;thj^% on 2019-05-13
Was there any return for: "dpkg -V libpython2.7-minimal"?

---

### Post by utah777 on 2019-05-13
> **1fallen said:**
> Was there any return for: "dpkg -V libpython2.7-minimal"?

None

---

### Post by utah777 on 2019-05-13
Just is case 

```

19:32:53 ~$ ls /usr/bin | grep python
depythontex
depythontex3
dh_python2
dh_python3
python
python2
python2.4
python2.7-config
python2-config
python3
python3.4
python3.4-config
python3.4m
python3.4m-config
python3-config
python3m
python3m-config
python-config
pythontex
pythontex3
x86_64-linux-gnu-python2.7-config
x86_64-linux-gnu-python3.4-config
x86_64-linux-gnu-python3.4m-config
x86_64-linux-gnu-python3-config
x86_64-linux-gnu-python3m-config
x86_64-linux-gnu-python-config

```

---

### Post by #&amp;thj^% on 2019-05-13
Well I like a challenge but this one might be a humbler for me, just to be sure will you show this please:
```
ls -l /usr/lib/python2.7/optparse.py
```

---

### Post by utah777 on 2019-05-13
> **1fallen said:**
> Well I like a challenge but this one might be a humbler for me, just to be sure will you show this please:
```
ls -l /usr/lib/python2.7/optparse.py
```

```
19:32:56 ~$ ls -la /usr/lib/python2.7/optparse.py
-rw-r--r-- 1 root root 61205 Nov 13 16:57 /usr/lib/python2.7/optparse.py
19:38:10 ~$

```

---

### Post by #&amp;thj^% on 2019-05-13
I'm torn here, but try this and post back any errors:
```
sudo apt install --reinstall python3-minimal python-lockfile
```

---

### Post by utah777 on 2019-05-13
> **1fallen said:**
> I'm torn here, but try this and post back any errors:
```
sudo apt install --reinstall python3-minimal python-lockfile
```


```
19:57:07 ~$ sudo apt install --reinstall python3-minimal python-lockfile
[sudo] password for sergey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  python-lockfile
0 upgraded, 1 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 31.3 kB of archives.
After this operation, 58.4 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main python3-minimal amd64 3.4.0-0ubuntu2 [23.2 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/main python-lockfile all 1:0.8-2ubuntu2 [8,090 B]
Fetched 31.3 kB in 0s (57.4 kB/s)          
(Reading database ... 449036 files and directories currently installed.)
Preparing to unpack .../python3-minimal_3.4.0-0ubuntu2_amd64.deb ...
Unpacking python3-minimal (3.4.0-0ubuntu2) over (3.4.0-0ubuntu2) ...
Selecting previously unselected package python-lockfile.
Preparing to unpack .../python-lockfile_1%3a0.8-2ubuntu2_all.deb ...
Unpacking python-lockfile (1:0.8-2ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up python-debian (0.1.21+nmu2ubuntu2) ...
  File "/usr/bin/pycompile", line 69
    with file(join(name, fn), 'r') as lines:
            ^
SyntaxError: invalid syntax
dpkg: error processing package python-debian (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on python-debian; however:
  Package python-debian is not configured yet.


dpkg: error processing package update-notifier-common (--configure):
 dependency problems - leaving unconfigured
Setting up python-pip (1.5.4-1ubuntu4) ...
No apport report written because the error message indicates its a followup error from a previous failure.
        File "/usr/bin/pycompile", line 69
    with file(join(name, fn), 'r') as lines:
            ^
SyntaxError: invalid syntax
dpkg: error processing package python-pip (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-notifier-common (= 0.154.1ubuntu6); however:
  Package update-notifier-common is not configured yet.
 update-notifier depends on python-debian; however:
  Package python-debian is not configured yet.


dpkg: error processing package update-notifier (--configure):
 dependency problems - leaving unconfigured
Setting up python3-minimal (3.4.0-0ubuntu2) ...
No apport report written because MaxReports is reached already
                                                              Setting up python-lockfile (1:0.8-2ubuntu2) ...
  File "/usr/bin/pycompile", line 69
    with file(join(name, fn), 'r') as lines:
            ^
SyntaxError: invalid syntax
dpkg: error processing package python-lockfile (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 python-debian
 update-notifier-common
 python-pip
 update-notifier
 python-lockfile
E: Sub-process /usr/bin/dpkg returned an error code (1)
19:57:20 ~$ 

```

---

### Post by rsteinmetz70112 on 2019-05-13
Try running

```
Sudo dpkg --configue python-debian
```

---

### Post by utah777 on 2019-05-13
> **rsteinmetz70112 said:**
> Try running

```
Sudo dpkg --configue python-debian
```


```
20:08:06 ~$ sudo dpkg --configure python-debian
Setting up python-debian (0.1.21+nmu2ubuntu2) ...
  File "/usr/bin/pycompile", line 69
    with file(join(name, fn), 'r') as lines:
            ^
SyntaxError: invalid syntax
dpkg: error processing package python-debian (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 python-debian
20:08:18 ~$ sudo dpkg --configure python-debian
Setting up python-debian (0.1.21+nmu2ubuntu2) ...
  File "/usr/bin/pycompile", line 69
    with file(join(name, fn), 'r') as lines:
            ^
SyntaxError: invalid syntax
dpkg: error processing package python-debian (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 python-debian
20:08:48 ~$

```

---

### Post by rsteinmetz70112 on 2019-05-13
OK Does this show any thing?

```
sudo dpkg --configure
sudo apt install -f
```

I think something got corrupted but I can't see what. I'm a little pressurized that reinstalling python-debian failed.

---

### Post by utah777 on 2019-05-13
> **rsteinmetz70112 said:**
> OK Does this show any thing?

```
sudo dpkg --configure
sudo apt install -f
```

I think something got corrupted but I can't see what. I'm a little pressurized that reinstalling python-debian failed.

```
20:39:21 ~$ sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up python-debian (0.1.21+nmu2ubuntu2) ...
  File "/usr/bin/pycompile", line 69
    with file(join(name, fn), 'r') as lines:
            ^
SyntaxError: invalid syntax
dpkg: error processing package python-debian (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on python-debian; however:
  Package python-debian is not configured yet.


dpkg: error processing package update-notifier-common (--configure):
 dependency problems - leaving unconfigured
Setting up python-pip (1.5.4-1ubuntu4) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                                              File "/usr/bin/pycompile", line 69
    with file(join(name, fn), 'r') as lines:
            ^
SyntaxError: invalid syntax
dpkg: error processing package python-pip (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-notifier-common (= 0.154.1ubuntu6); however:
  Package update-notifier-common is not configured yet.
 update-notifier depends on python-debian; however:
  Package python-debian is not configured yet.


dpkg: error processing package update-notifier (--configure):
 dependency problems - leaving unconfigured
Setting up python-lockfile (1:0.8-2ubuntu2) ...
  File "/usr/bin/pycompile", line 69
    with file(join(name, fn), 'r') as lines:
            ^
SyntaxError: invalid syntax
dpkg: error processing package python-lockfile (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 python-debian
 update-notifier-common
 python-pip
 update-notifier
 python-lockfile
E: Sub-process /usr/bin/dpkg returned an error code (1)
20:39:44 ~$ 

```

---

### Post by utah777 on 2019-05-13
Just in case it relates to bad links:

```
20:53:42 ~$ ls -lh /usr/bin/python*
lrwxrwxrwx 1 root root   18 May 12 22:33 /usr/bin/python -> /usr/bin/python2.4
lrwxrwxrwx 1 root root    9 Dec 21  2013 /usr/bin/python2 -> python2.7
-rwxr-xr-x 1 root root 2.0M Jan 25  2014 /usr/bin/python2.4
lrwxrwxrwx 1 root root   33 Nov 13 16:59 /usr/bin/python2.7-config -> x86_64-linux-gnu-python2.7-config
lrwxrwxrwx 1 root root   16 Dec 21  2013 /usr/bin/python2-config -> python2.7-config
lrwxrwxrwx 1 root root    9 Mar 23  2014 /usr/bin/python3 -> python3.4
-rwxr-xr-x 2 root root 3.6M Nov 13 03:36 /usr/bin/python3.4
lrwxrwxrwx 1 root root   33 Nov 13 03:36 /usr/bin/python3.4-config -> x86_64-linux-gnu-python3.4-config
-rwxr-xr-x 2 root root 3.6M Nov 13 03:36 /usr/bin/python3.4m
lrwxrwxrwx 1 root root   34 Nov 13 03:36 /usr/bin/python3.4m-config -> x86_64-linux-gnu-python3.4m-config
lrwxrwxrwx 1 root root   16 Mar 23  2014 /usr/bin/python3-config -> python3.4-config
lrwxrwxrwx 1 root root   10 Mar 23  2014 /usr/bin/python3m -> python3.4m
lrwxrwxrwx 1 root root   17 Mar 23  2014 /usr/bin/python3m-config -> python3.4m-config
lrwxrwxrwx 1 root root   16 Dec 21  2013 /usr/bin/python-config -> python2.7-config
lrwxrwxrwx 1 root root   58 Feb 20  2014 /usr/bin/pythontex -> ../share/texlive/texmf-dist/scripts/pythontex/pythontex.py
-rwxr-xr-x 1 root root  306 Feb 20  2014 /usr/bin/pythontex3

```

---

### Post by rsteinmetz70112 on 2019-05-15
/usr/bin/pycompile seems to be throwing off the error. pycompile is part of package python-minimal you might try reinstalling that

---

### Post by oldfred on 2019-05-15
```
lrwxrwxrwx 1 root root   18 May 12 22:33 /usr/bin/python -> /usr/bin/python2.4
```

What version of Ubuntu are you using?
I do not think 2.4 as been the default for years, and it is normally the default install of 2.7. But many programs now use python3, but must specify that.

---

