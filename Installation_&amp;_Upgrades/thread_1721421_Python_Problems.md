---
title: "Python Problems"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by tedshaw on 2011-04-04
Python (2.6) is messed up and everything dependent on python is messed up also.

I can not reinstall any of these packages via synaptic package manager.

This is my error:

sudo apt-get install python
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
9 not fully installed or removed.
Need to get 0B/898kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 137448 files and directories currently installed.)
Preparing to replace python-gtk2 2.21.0-0ubuntu1 (using .../python-gtk2_2.21.0-0ubuntu1_amd64.deb) ...
/var/lib/dpkg/info/python-gtk2.prerm: 6: update-python-modules: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: update-python-modules: not found
dpkg: error processing /var/cache/apt/archives/python-gtk2_2.21.0-0ubuntu1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/python-gtk2.postinst: 10: update-python-modules: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/python-gtk2_2.21.0-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Thanks!

---

### Post by Frogs Hair on 2011-04-04
I'm not sure if can help , you wrote Python was messed up . What lead you to reinstall the package to begin with ? (explain messed up)

The output from the terminal is strange because if the latest version of a  package is installed it usually stops at 0 to remove and 0 to be upgraded.  

Did you mark the python package for re-installation in the synaptic package manager or just run sudo apt-get install python ?

---

### Post by tedshaw on 2011-04-04
I was having problems with Desklets and Screenlets.  They both were not working and I think it is Python related.  I installed Python 2.7 from source (bad idea, I know) thinking it would help but only broke my system even more.  Any ideas to get my system back to Python 2.6? Thanks

I can not install, reinstall, or remove programs since ubuntu relies on python for this. I can still make/make install.  Argh this is frustrating.

---

### Post by Frogs Hair on 2011-04-04
I don't know what to do about the catch 22 , as a last resort backup and reinstall . Someone may have an answer for this so give it some time .

---

### Post by tedshaw on 2011-04-04
I fixed this problem by manually downloading and extracting packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

A very time consuming task....

Thank You very much for your help Frogs Hair!

---

### Post by gxwilson on 2011-04-09
Do you have any details on how you did they manual install. I'm having a similar problem and may need to go down the same path.

---

### Post by tedshaw on 2011-04-09
> **gxwilson said:**
> Do you have any details on how you did they manual install. I'm having a similar problem and may need to go down the same path.
 
Go here: [http://packages.ubuntu.com/maverick/python/](http://packages.ubuntu.com/maverick/python/)
 
and download the following packages:
python
python-apt
python-aptdaemon
python-minimal
 
You might need more depending on your system, but I think I only needed those packages.
 
When you download it, go into the directory via terminal.  Then type
sudo apt-get install <package name>
 
 
NOTE: I did this and it managed to fix most things but a lot of stuff was still messed up.  I was fustrated so I did a reinstall (lucky for me my home folder was on another partition).  That completely solved my problem.  This has been a learning experience for me...

---

