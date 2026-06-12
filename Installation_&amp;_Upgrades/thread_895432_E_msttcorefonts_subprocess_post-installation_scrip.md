---
title: "E: msttcorefonts: subprocess post-installation script returned error exit status 1"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by askhetan on 2008-08-20
this is what appears on my pc and has been bugging me eversince..
if i try to uninstall it wether using synaptic or by using terminal..the problem just doesnt go...please help..i cant play any media file on my pc

---

### Post by Earl_Maroon on 2008-11-04
I'm currently getting the same error running 8.10. Everything works, but I can't install that package. While synaptic is trying to configure it it says "error in package"...

---

### Post by Partyboi2 on 2008-11-04
> **Earl_Maroon said:**
> I'm currently getting the same error running 8.10. Everything works, but I can't install that package. While synaptic is trying to configure it it says "error in package"...
Can you open a terminal (Applications>Accessoires>Terminal)  and post the output to
```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by dubhear on 2008-11-11
sudo dpkg --configure -a

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts

-------------------------------------------------------------------
sudo apt-get -f install 

sudo: unable to resolve host a-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl librdf0 kdebase-runtime-data-common librasqal0 kdelibs5-data
  libgif4 libstreamanalyzer0 libstreams0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
------------------------------------------------------------------
I think we have same problem here so, now i decided to get it fixed.
any help?

---

### Post by Partyboi2 on 2008-11-11
> **dubhear said:**
> sudo dpkg --configure -a

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts

-------------------------------------------------------------------
sudo apt-get -f install 

sudo: unable to resolve host a-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl librdf0 kdebase-runtime-data-common librasqal0 kdelibs5-data
  libgif4 libstreamanalyzer0 libstreams0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
------------------------------------------------------------------
I think we have same problem here so, now i decided to get it fixed.
any help?
Try following [[COLOR=Blue]this[/COLOR]]("http://geek00l.blogspot.com/2007/11/ubuntu-msttcorefonts-problem-fixed.html")

---

