---
title: "dpkg: error processing package update-notifier-common (--configure)"
date: 2016-09-26
forum: Installation &amp; Upgrades
---

### Post by neonlinx on 2016-09-26
Hi,

after ```
apt-get update && apt-get upgrade
``` I got this:

```
Setting up update-notifier-common (0.154.1ubuntu2) ...
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 26, in <module>
    import debian.deb822
ImportError: No module named debian.deb822
dpkg: error processing package update-notifier-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 update-notifier-common


Setting up update-notifier-common (0.154.1ubuntu2) ...
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 26, in <module>
    import debian.deb822
ImportError: No module named debian.deb822
dpkg: error processing package update-notifier-common (--configure):
 subprocess installed post-installation script returned error exit status 1

```

I tried with autoremove and reinstall but nothing seems to work.

Sorry but I'm a noob with Ubuntu, so feel free to ask for more infos

P.s.: I use Ubuntu Server 14.04.05 LTS

---

### Post by ian-weisser on 2016-09-26
Reinstall the 'python-debian' package. It provides debian.822
```
sudo apt install --reinstall python-debian
```

---

### Post by neonlinx on 2016-09-28
Hi,

Thanks for reply and sorry for delay...

I've done what you suggest but without success. This is the result:
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 49.7 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://ubuntu.mirrors.ovh.net/ftp.ubuntu.com/ubuntu/](http://ubuntu.mirrors.ovh.net/ftp.ubuntu.com/ubuntu/) trusty/main python-debian all 0.1.21+nmu2ubuntu2 [49.7 kB]
Fetched 49.7 kB in 0s (217 kB/s)
(Reading database ... 66536 files and directories currently installed.)
Preparing to unpack .../python-debian_0.1.21+nmu2ubuntu2_all.deb ...
Unpacking python-debian (0.1.21+nmu2ubuntu2) over (0.1.21+nmu2ubuntu2) ...
Setting up python-debian (0.1.21+nmu2ubuntu2) ...
Setting up update-notifier-common (0.154.1ubuntu2) ...
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 26, in <module>
    import debian.deb822
ImportError: No module named debian.deb822
dpkg: error processing package update-notifier-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 update-notifier-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


EDIT: from what I remember, some time ago I had installed different versions of python. But probably, being a novice, I must have done something wrong; for example to tell the system which version to use or an incorrect directory installation.

---

### Post by ian-weisser on 2016-09-28
You don't get to tell the system which version of Python to use.
Doing so breaks lots of stuff. Python does not run on top of your system - it's an integral part. Many important system services and features use python.
Changing versions breaks those scripts.

Go to [http://packages.ubuntu.com/trusty/python-debian](http://packages.ubuntu.com/trusty/python-debian)
Download the package to your desktop.
Open a terminal
```
sudo dpkg --install ~/Desktop/<PACKAGE_NAME>
```
Then see if apt works.

---

### Post by neonlinx on 2016-10-01
Thanks,

I downloaded the .dsc package. Then I did:

```
dpkg-source -x python-debian_0.1.21+nmu2ubuntu2.dsc

```

Then...

```
dpkg-buildpackage -rfakeroot -b

```

but unfortunately I got this:

```
dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: source package python-debian
dpkg-buildpackage: source version 0.1.21+nmu2ubuntu2
dpkg-buildpackage: source distribution trusty
dpkg-buildpackage: source changed by Matthias Klose <doko@ubuntu.com>
dpkg-buildpackage: host architecture amd64
 dpkg-source --before-build python-debian-0.1.21+nmu2ubuntu2
dpkg-checkbuilddeps: Unmet build dependencies: debhelper (>= 5.0.37.2) python3-setuptools python3-chardet python3-six
dpkg-buildpackage: warning: build dependencies/conflicts unsatisfied; aborting
dpkg-buildpackage: warning: (Use -d flag to override.)

```

I managed to solve this. Anyway then I got this:

```

dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: source package python-debian
dpkg-buildpackage: source version 0.1.21+nmu2ubuntu2
dpkg-buildpackage: source distribution trusty
dpkg-buildpackage: source changed by Matthias Klose <doko@ubuntu.com>
dpkg-buildpackage: host architecture amd64
 dpkg-source --before-build python-debian-0.1.21+nmu2ubuntu2
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
# Add here commands to clean up after the build process.
python setup.py clean
running clean
python3 setup.py clean
running clean
rm -rf lib/python_debian.egg-info
rm -rf build/
rm -f README.debtags
rm -f setup.py
find lib/debian -type f -name '*.pyc' -exec rm {} \;
dh_clean
 debian/rules build
sed -e 's/__CHANGELOG_VERSION__/0.1.21+nmu2ubuntu2/' < setup.py.in > setup.py
dh_testdir
# Add here commands to compile the package.
python setup.py build
running build
running build_py
creating build
creating build/lib
copying lib/deb822.py -> build/lib
creating build/lib/debian
copying lib/debian/debian_support.py -> build/lib/debian
copying lib/debian/changelog.py -> build/lib/debian
copying lib/debian/debtags.py -> build/lib/debian
copying lib/debian/deprecation.py -> build/lib/debian
copying lib/debian/__init__.py -> build/lib/debian
copying lib/debian/deb822.py -> build/lib/debian
copying lib/debian/arfile.py -> build/lib/debian
copying lib/debian/debfile.py -> build/lib/debian
creating build/lib/debian_bundle
copying lib/debian_bundle/__init__.py -> build/lib/debian_bundle
python3 setup.py build
running build
running build_py
# run the tests
cd tests && ./test_deb822.py
.................................................
----------------------------------------------------------------------
Ran 49 tests in 0.227s


OK
cd tests && ./test_debfile.py
..........
----------------------------------------------------------------------
Ran 10 tests in 0.289s


OK
cd tests && ./test_debtags.py
...
----------------------------------------------------------------------
Ran 3 tests in 0.017s


OK
cd tests && ./test_changelog.py
.................
----------------------------------------------------------------------
Ran 17 tests in 0.065s


OK
cd tests && ./test_debian_support.py
......
----------------------------------------------------------------------
Ran 6 tests in 0.009s


OK
cd tests && python3 ./test_deb822.py
.................................................
----------------------------------------------------------------------
Ran 49 tests in 0.139s


OK
cd tests && python3 ./test_debfile.py
..........
----------------------------------------------------------------------
Ran 10 tests in 0.232s


OK
cd tests && python3 ./test_debtags.py
...
----------------------------------------------------------------------
Ran 3 tests in 0.004s


OK
cd tests && python3 ./test_changelog.py
.................
----------------------------------------------------------------------
Ran 17 tests in 0.029s


OK
cd tests && python3 ./test_debian_support.py
......
----------------------------------------------------------------------
Ran 6 tests in 0.016s


OK
lib/debian/doc-debtags > README.debtags
touch build-stamp
 fakeroot debian/rules binary
dh_testdir
dh_testroot
dh_clean
dh_installdirs
# Add here commands to install the package into debian/tmp
python setup.py install --root="/root/python-debian-0.1.21+nmu2ubuntu2/debian/python-debian" --no-compile --install-layout=deb
usage: setup.py [global_opts] cmd1 [cmd1_opts] [cmd2 [cmd2_opts] ...]
   or: setup.py --help [cmd1 cmd2 ...]
   or: setup.py --help-commands
   or: setup.py cmd --help


error: option --install-layout not recognized
make: *** [install] Error 1
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2



```

:(

---

### Post by ian-weisser on 2016-10-01
I suggest downloading and installing the pre-built .deb instead building it yourself using the .dsc

---

### Post by neonlinx on 2016-10-13
Sorry again for the delay but in these days I have some personal problems (I was at Hospital...)

Anyway.....I tried your suggestion but without success. The error remains.

Don't know if can be useful but if I do

> dpkg -C

this is the result:

> The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 update-notifier-common Files shared between update-notifier and other packages


The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 module-init-tools    transitional dummy package (module-init-tools to kmod)
 libjson0:amd64       JSON manipulation library (transitional package)
 default-jre          Standard Java or Java compatible Runtime

Thanks again for your help and patience


EDIT:

Don't know if can help....this is my python....

> ls -l /usr/bin/python
lrwxrwxrwx 1 root root 21 Aug 25  2015 /usr/bin/python -> /usr/local/bin/python


If i do

> readlink -f $(which python)

the output is:

> /usr/local/bin/python2.7


---

### Post by ian-weisser on 2016-10-13
Switch your symlink back to the system-provided Python, and try again.
As I mentioned before, your system depends upon a specific version of Python. When you change it, you break your system.

---

### Post by neonlinx on 2016-10-14
Ok.

I've done this in the past but.....can you tell me the correct procedure?? because sincerly I'm afraid that I have some serious chaos on my system.

This is the results of some commands:

> python -V
Python 2.7.10

> which python
/usr/local/bin/python


> ls /usr/bin/python*
/usr/bin/python   /usr/bin/python2.7         /usr/bin/python2-config  /usr/bin/python3.2    /usr/bin/python3.3   /usr/bin/python3.4   /usr/bin/python3m
/usr/bin/python2  /usr/bin/python2.7-config  /usr/bin/python3         /usr/bin/python3.2mu  /usr/bin/python3.3m  /usr/bin/python3.4m  /usr/bin/python-config


> update-alternatives --list python
/usr/bin/python2.7
/usr/lib/python2.7.10



> update-alternatives --config python
There are 2 choices for the alternative python (providing /usr/lib/python).


  Selection    Path                   Priority   Status
------------------------------------------------------------
* 0            /usr/lib/python2.7.10   50        auto mode
  1            /usr/bin/python2.7      10        manual mode
  2            /usr/lib/python2.7.10   50        manual mode



I hope that these informations can help you to understand the chaos on my system and the proper way to help me. Sorry for this confusion...

---

### Post by ian-weisser on 2016-10-14
How to uninstall all those versions of python depends upon how you installed them in the first place.

Were it me, I would wipe the whole thing and reinstall. Mixing up your python and breaking apt means the potential for a lot of other deep problems. A reinstall takes an hour - mucking about with apt in the forums has already taken days.
Next time, consider experimenting with major changes to your system in a VM first.

---

### Post by neonlinx on 2016-10-18
Probably you're right.

unfortunately, at this time I have some software that work 24h/day. I need to wait about 2 months to do a clean install.

And..... doing "dist-upgrade" can be useful?? or is there a way (I imagine is not possible but who know?) to reinstall only the system, maintaining the installed programs and home directory??

---

