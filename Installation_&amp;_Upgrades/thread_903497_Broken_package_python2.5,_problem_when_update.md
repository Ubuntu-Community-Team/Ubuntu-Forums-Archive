---
title: "Broken package python2.5, problem when update"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by SpintroniK on 2008-08-28
Hello, 

I've a probleme when I try to upgrade my xubuntu 7.10 gutsy.
Python 2.5 seems to be broken so tried 'apt-get install -f' and I got the following :
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  python2.5
Suggested packages:
  python2.5-doc python-profiler
The following packages will be upgraded:
  python2.5
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/2871kB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 122615 files and directories currently installed.)
Preparing to replace python2.5 2.5.1-5ubuntu5.1 (using .../python2.5_2.5.1-5ubuntu5.2_i386.deb) ...
Unpacking replacement python2.5 ...
dpkg: error processing /var/cache/apt/archives/python2.5_2.5.1-5ubuntu5.2_i386.deb (--unpack):
 unable to create `./usr/lib/python2.5/lib-dynload/_ctypes.so': Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python2.5_2.5.1-5ubuntu5.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

thanks for your help.

---

### Post by SpintroniK on 2008-09-01
UP

I don't have the solution...
I hope someone will fix this problem because I can't install some software...

Thanks

---

### Post by manishtech on 2008-09-02
```
sudo dpkg-reconfigure python
```Hope this works, run this command in terminal

---

### Post by SpintroniK on 2008-09-02
Your command return no error but I've done an  sudo apt-get install -f just after and I've the following (which ends with an error code (1)) : 
```
 sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  libdc1394-13 libavformat1d gettext
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gettext libavformat1d libdc1394-13 python2.5
Suggested packages:
  cvs gettext-doc python2.5-doc python-profiler
The following packages will be REMOVED
  blender emesene
The following NEW packages will be installed
  gettext libavformat1d libdc1394-13
The following packages will be upgraded:
  python2.5
1 upgraded, 3 newly installed, 2 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 4744kB of archives.
After unpacking 20.7MB disk space will be freed.
Do you want to continue [Y/n]? Y
Get: 1 http://fr.archive.ubuntu.com gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]
Get: 2 http://security.ubuntu.com gutsy-security/main python2.5 2.5.1-5ubuntu5.2 [2871kB]
Get: 3 http://security.ubuntu.com gutsy-security/main libavformat1d 3:0.cvs20070307-5ubuntu4.1 [287kB]
Get: 4 http://fr.archive.ubuntu.com gutsy/main libdc1394-13 1.1.0-3ubuntu3 [34.4kB]
Fetched 4744kB in 39s (121kB/s)                                                
(Reading database ... 123248 files and directories currently installed.)
Removing blender ...
Removing emesene ...
(Reading database ... 122620 files and directories currently installed.)
Preparing to replace python2.5 2.5.1-5ubuntu5.1 (using .../python2.5_2.5.1-5ubuntu5.2_i386.deb) ...
Unpacking replacement python2.5 ...
[B]dpkg: error processing /var/cache/apt/archives/python2.5_2.5.1-5ubuntu5.2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/python2.5/lib-dynload', which is also in package python2.5-minimal[/B]
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.16.1-2ubuntu3_i386.deb) ...
Selecting previously deselected package libdc1394-13.
Unpacking libdc1394-13 (from .../libdc1394-13_1.1.0-3ubuntu3_i386.deb) ...
Selecting previously deselected package libavformat1d.
Unpacking libavformat1d (from .../libavformat1d_3%3a0.cvs20070307-5ubuntu4.1_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/python2.5_2.5.1-5ubuntu5.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Hope someone will find a solution.


EDIT : Now it works, I've just removed this folder : /usr/lib/python2.5/lib-dynload 

Thanks a lot.

---

