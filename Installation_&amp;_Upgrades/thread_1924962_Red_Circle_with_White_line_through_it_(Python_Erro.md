---
title: "Red Circle with White line through it (Python Error?)"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by Wesley32 on 2012-02-13
Hi, 

I recently installed python3.2.2 on my machine. I now have this red circle at the top of my screen and will not go away or let me click on the update link or anything. I will post what I have in the terminal:



user@user-OptiPlex-GX620:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  python-software-properties software-properties-common software-properties-gtk
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
46 not fully installed or removed.
Need to get 0 B/63.5 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 261051 files and directories currently installed.)
Preparing to replace python-software-properties 0.81.13.2 (using .../python-software-properties_0.81.13.3_all.deb) ...
/var/lib/dpkg/info/python-software-properties.prerm: 12: pyclean: Permission denied
dpkg: warning: subprocess old pre-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 12: pyclean: Permission denied
dpkg: error processing /var/cache/apt/archives/python-software-properties_0.81.13.3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 126
No apport report written because MaxReports is reached already
                                                              /var/lib/dpkg/info/python-software-properties.postinst: 7: pycompile: Permission denied
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 126
Preparing to replace software-properties-common 0.81.13.2 (using .../software-properties-common_0.81.13.3_all.deb) ...
/var/lib/dpkg/info/software-properties-common.prerm: 12: pyclean: Permission denied
dpkg: warning: subprocess old pre-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 12: pyclean: Permission denied
dpkg: error processing /var/cache/apt/archives/software-properties-common_0.81.13.3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 126
No apport report written because MaxReports is reached already
                                                              /var/lib/dpkg/info/software-properties-common.postinst: 7: pycompile: Permission denied
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 126
Preparing to replace software-properties-gtk 0.81.13.2 (using .../software-properties-gtk_0.81.13.3_all.deb) ...
/var/lib/dpkg/info/software-properties-gtk.prerm: 12: pyclean: Permission denied
dpkg: warning: subprocess old pre-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 12: pyclean: Permission denied
dpkg: error processing /var/cache/apt/archives/software-properties-gtk_0.81.13.3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 126
No apport report written because MaxReports is reached already
                                                              /var/lib/dpkg/info/software-properties-gtk.postinst: 12: pycompile: Permission denied
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 126
Errors were encountered while processing:
 /var/cache/apt/archives/python-software-properties_0.81.13.3_all.deb
 /var/cache/apt/archives/software-properties-common_0.81.13.3_all.deb
 /var/cache/apt/archives/software-properties-gtk_0.81.13.3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Wesley32 on 2012-02-14
bump

---

### Post by jh79 on 2012-02-21
I got the same problem after installing python 3.2.2 and setting it to be default. I changed it back to 2.7.2 and everything worked again!

Try the following in the terminal
cd /usr/bin/
sudo rm python
sudo ln -s python2.7 python

---

