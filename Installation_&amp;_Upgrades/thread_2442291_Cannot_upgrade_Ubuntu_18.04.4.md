---
title: "Cannot upgrade Ubuntu 18.04.4"
date: 2020-05-01
forum: Installation &amp; Upgrades
---

### Post by digital-junkie on 2020-05-01
I have an issue with my Ubuntu.

Each time I want to upgrade from the terminal using ```
update-manager - d
```, I get this error:
```
cannot import name 'gi' from 'gi' user/bin/python3... 
```

And also, prior before this, I have this error red circle at the top right screen of my system. Ever since I noticed this red circle. I can't access update manager, or live patch. 

I can't basically do anything regards update or upgrade.

Please how can I resolve this?

---

### Post by deadflowr on 2020-05-01
The red circle icon usually  means something's broken or, at least, in a undesirably state.
Please open the terminal and run
```
sudo apt update
sudo apt upgrade
```
and post back the results.

Also, I'm not sure it is just a formatting issue or not but the update-manager command is off.
it should be -d and not - d like
```
update-manager -d
```
and not
```
update-manager - d
```

---

### Post by digital-junkie on 2020-05-02
I tried the 'sudo apt update' and 'sudo apt upgrade' command.

This is the error a getting back, am downloading and processing for a long time. 

```
 Errors were encountered while processing:
/var/catche/apt/thunderbird-addons/extensions/langpack-en-GB@thunderbird.mozilla.org.xpi' to usr/usr/lib/thunderbird-addons/extensions... 
E: sub-process usr/bin/dpkg returned and error code(1)
```

Again, I tried the ```
 update-manager - d
```

It still returned back the same error.

---

### Post by CelticWarrior on 2020-05-02
Again, it's ```
update-manager -d
```
(there's no space after the dash)

And please post the complete error messages.

---

### Post by digital-junkie on 2020-05-02
okay, it stll returns the same error message. here are the error messages:

---

### Post by digital-junkie on 2020-05-02
It still returns the same error message.... Here are the error messages:

sudo apt update:


```
 unique@digital-junkie-hp-folio:~$ sudo apt update
[sudo] password for unique: 
Hit:1 http://ppa.launchpad.net/openlp-core/release/ubuntu bionic InRelease
Get:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]    
Hit:3 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
Get:4 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [38.7 kB]
Hit:5 https://deb.nodesource.com/node_12.x bionic InRelease                    
Get:6 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Get:7 http://security.ubuntu.com/ubuntu bionic-security/main DEP-11 48x48 Icons [17.6 kB]
Get:8 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [42.1 kB]
Get:9 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:10 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [932 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [675 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [301 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [142 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted i386 Packages [9,888 B]
Get:16 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted amd64 Packages [50.2 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [273 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse i386 Packages [8,748 B]
Get:19 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 Packages [15.5 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:21 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [7,972 B]
Fetched 2,770 kB in 12s (229 kB/s)                                             
Traceback (most recent call last):
  File "/usr/lib/cnf-update-db", line 8, in <module>
    from CommandNotFound.db.creator import DbCreator
  File "/usr/lib/python3/dist-packages/CommandNotFound/db/creator.py", line 11, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 63, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in <module>
    import apport.fileutils
  File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 23, in <module>
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 24, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'


Original exception was:
Traceback (most recent call last):
  File "/usr/lib/cnf-update-db", line 8, in <module>
    from CommandNotFound.db.creator import DbCreator
  File "/usr/lib/python3/dist-packages/CommandNotFound/db/creator.py", line 11, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code
 
```


```
 sudo apt upgrade: 
```


```
 unique@digital-junkie-hp-folio:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 thunderbird-gnome-support : Depends: thunderbird (= 1:68.7.0+build1-0ubuntu0.18.04.1) but 1:68.4.1+build1-0ubuntu0.18.04.1 is installed
 thunderbird-locale-en : Depends: thunderbird (>= 1:68.7.0+build1-0ubuntu0.18.04.1) but 1:68.4.1+build1-0ubuntu0.18.04.1 is installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
 
```


apt --fix-broken install:


```
 root@digital-junkie-hp-folio:~# apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  thunderbird
Suggested packages:
  ttf-lyx
The following packages will be upgraded:
  thunderbird
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
183 not fully installed or removed.
Need to get 0 B/43.4 MB of archives.
After this operation, 487 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
E: Invalid archive member header ]_&#65533;%&#65533;&#65533;|a&#65533;&#65533;&#65533;,&#65533;0&#65533;&#65533;&#65533;;q&#65533;y)iC&#42881;>I5&#65533;Pu-m&#65533;X&#65533;&#65533;o&#65533;Z&#65533;&#65533;4&#65533;'&#65533;)&#65533;&#65533;&#65533;F&#65533;
     %9&#65533;
E: Prior errors apply to /var/cache/apt/archives/thunderbird_1%3a68.7.0+build1-0ubuntu0.18.04.1_amd64.deb
debconf: apt-extracttemplates failed: No such file or directory
(Reading database ... 219903 files and directories currently installed.)
Preparing to unpack .../thunderbird_1%3a68.7.0+build1-0ubuntu0.18.04.1_amd64.deb ...
Unpacking thunderbird-locale-en (1:68.7.0+build1-0ubuntu0.18.04.1) over (1:68.7.0+build1-0ubuntu0.18.04.1) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: <decompress> subprocess returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/thunderbird_1%3a68.7.0+build1-0ubuntu0.18.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './usr/lib/thunderbird-addons/extensions/langpack-en-GB@thunderbird.mozilla.org.xpi' to '/usr/lib/thunderbird-addons/extensions/langpack-en-GB@thunderbird.mozilla.org.xpi.dpkg-new': unexpected end of file or stream
Errors were encountered while processing:
 /var/cache/apt/archives/thunderbird_1%3a68.7.0+build1-0ubuntu0.18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


update-manager -d:


```
 unique@digital-junkie-hp-folio:~$ update-manager -d
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in <module>
    import gi
  File "/usr/lib/python3/dist-packages/gi/__init__.py", line 42, in <module>
    from . import _gi
ImportError: cannot import name '_gi' from 'gi' (/usr/lib/python3/dist-packages/gi/__init__.py)
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 63, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in <module>
    import apport.fileutils
  File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 23, in <module>
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 24, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'


Original exception was:
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in <module>
    import gi
  File "/usr/lib/python3/dist-packages/gi/__init__.py", line 42, in <module>
    from . import _gi
ImportError: cannot import name '_gi' from 'gi' (/usr/lib/python3/dist-packages/gi/__init__.py) 
```

---

### Post by CelticWarrior on 2020-05-02
It goes without saying that users MUST NOT try a release upgrade with such errors in APT.
And the errors are apparently related to python. Do you remember installing something Python related recently?

---

### Post by digital-junkie on 2020-05-02
Yes, I have issues with my Python. The default version of Python on my system was 2.0. I wanted changing it to version 3.0. It was however not successful. 

I think I must have messed with some file settings. That's why I thought running an upgrade will solve the problem.

---

### Post by CelticWarrior on 2020-05-02
Python is an integral part of the OS and shouldn't be messed with by users who have no clue about what they're doing. Experienced users can install and use different versions and select either one accordingly.

I'm not an experienced user and I have no idea how to correct such mistakes, if they're correctable at all... What I do know is that with such errors trying to release upgrade is insane. Unless there are other suggestions perhaps a fresh install is the best solution.

---

### Post by mörgæs on 2020-05-02
Yes, do a fresh install of 20.04. It will by default bring you Python 3.8 alone (without Python 2).

---

### Post by digital-junkie on 2020-05-02
Thank you, I will have to backup my data and run a fresh installation.

---

### Post by Impavidus on 2020-05-02
I hope for you that's all, but I see some random file corruption, which could be an indication of hard drive trouble. You should keep excellent backups at all times. And upgrades don't fix problems (other than driver problems).

FYI, Ubuntu 18.04 comes with both Python 2.7 and Python 3.6. The default is Python 2, because the scripts that need Python 2 don't say so explicitly, whilst the scripts that need Python 3 do say so.

---

