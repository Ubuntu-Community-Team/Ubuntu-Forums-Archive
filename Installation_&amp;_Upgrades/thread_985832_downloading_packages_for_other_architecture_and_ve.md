---
title: "downloading packages for other architecture and version"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by kulkarniniraj on 2008-11-18
hello
  I am having 2 computers one of which have ubuntu 7.10(Gutsy) for amd64
while other have ubuntu 8.04(Hardy) for i386 arch. I have internet connection  
 to pc having 7.10. Now it is not possible for me to give internet connection to other pc by any way. So i want to download the packages for hardy version using current computer (which has gutsy) . Can anyone tell me how can I do it ?

i know i have to use apt-get --downloadonly option to download package files without installing them and edit apt.conf configuration file but exactly how to do it , i  don't know. So please help me.

---

### Post by Partyboi2 on 2008-11-18
Try using "generate package download script" in synaptic
[https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)

---

### Post by kulkarniniraj on 2008-11-19
Thanks but that helped me partially. How can i change architecture in apt.conf?

---

### Post by kulkarniniraj on 2008-11-19
I have found many things regarding architecture on sample apt.conf (path given in man page). Now just tell me if a package downloaded for 7.10 will also apply to 8.04 (for same architecture)

---

### Post by Partyboi2 on 2008-11-19
> **kulkarniniraj said:**
> Thanks but that helped me partially. How can i change architecture in apt.conf?
You don't need to change architecture in apt.conf  to download the packages using the 'package download script. Right click on the script that was created and open it with a text editor you will see that the architecture is mentioned like so
```
#!/bin/sh
wget -c http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-dev_2.6.32.dfsg-4ubuntu1.1_[COLOR=Red]i386.deb[/COLOR]
wget -c http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.6.32.dfsg-4ubuntu1.1_[COLOR=Red]i386.deb[/COLOR]
wget -c http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.6.32.dfsg-4ubuntu1.1_[COLOR=Red]i386.deb[/COLOR]
wget -c http://au.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.6.32.dfsg-4ubuntu1.1_[COLOR=Red]i386.deb[/COLOR]
```

> I have found many things regarding architecture on sample apt.conf (path given in man page). Now just tell me if a package downloaded for 7.10 will also apply to 8.04 (for same architecture)
It will be a older version of the package and may have dependencies issues. So it may work and it may not.

---

