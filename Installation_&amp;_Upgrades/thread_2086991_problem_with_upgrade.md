---
title: "problem with upgrade"
date: 2012-11-22
forum: Installation &amp; Upgrades
---

### Post by mj125 on 2012-11-22
Hello 
when do I try to upgrade.  I get this error
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed:
  apt-utils debconf debconf-i18n dpkg libapt-inst1.5 libapt-pkg4.12 libbz2-1.0
  libdb5.1 libgcc1 liblocale-gettext-perl liblzma5 libselinux1 libstdc++6
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl perl-base
  tar tzdata zlib1g
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/6,771 kB of archives.
After this operation, 23.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
dpkg: regarding .../libgcc1_1%3a4.7.2-2ubuntu1_amd64.deb containing libgcc1:amd64, pre-dependency problem:
 libgcc1 pre-depends on multiarch-support
  multiarch-support is unpacked, but has never been configured.

dpkg: error processing /var/cache/apt/archives/libgcc1_1%3a4.7.2-2ubuntu1_amd64.deb (--unpack):
 pre-dependency problem - not installing libgcc1:amd64
Errors were encountered while processing:
 /var/cache/apt/archives/libgcc1_1%3a4.7.2-2ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I do this, but It's not helping.

sudo dpkg --configure -a sudo apt-get install -f
sudo gedit /var/lib/dpkg/status


then i do this:
sudo dpkg --configure -a
and i get this:
dpkg: dependency problems prevent configuration of libc6:amd64:
 libc6:amd64 depends on libgcc1; however:
  Package libgcc1 is not installed.
 libc6:amd64 depends on tzdata; however:
  Package tzdata is not installed.

dpkg: error processing libc6:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of multiarch-support:
 multiarch-support depends on libc6 (>= 2.3.6-2); however:
  Package libc6:amd64 is not configured yet.

dpkg: error processing multiarch-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6:amd64
 multiarch-support

---

### Post by mj125 on 2012-11-22
Hello
I try to install <package> and I get this error:
installArchives() failed: E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: No such file or directory 
E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: No such file or directory 
E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: No such file or directory 
E: Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: No such file or directory 
dpkg: regarding .../libgcc1_1%3a4.7.2-2ubuntu1_amd64.deb containing libgcc1:amd64, pre-dependency problem: 
 libgcc1 pre-depends on multiarch-support 
  multiarch-support is unpacked, but has never been configured. 

dpkg: error processing /var/cache/apt/archives/libgcc1_1%3a4.7.2-2ubuntu1_amd64.deb (--unpack): 
 pre-dependency problem - not installing libgcc1:amd64 
Errors were encountered while processing: 
 /var/cache/apt/archives/libgcc1_1%3a4.7.2-2ubuntu1_amd64.deb 
Error in function:  
dpkg: dependency problems prevent configuration of libc6:amd64: 
 libc6:amd64 depends on libgcc1; however: 
  Package libgcc1 is not installed. 
 libc6:amd64 depends on tzdata; however: 
  Package tzdata is not installed. 

dpkg: error processing libc6:amd64 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of multiarch-support: 
 multiarch-support depends on libc6 (>= 2.3.6-2); however: 
  Package libc6:amd64 is not configured yet. 

dpkg: error processing multiarch-support (--configure): 
 dependency problems - leaving unconfigured

---

### Post by zvacet on 2012-11-22
Try with 

```
sudo dpkg --configure -a
```

---

### Post by zvacet on 2012-11-22
```
sudo apt-get install tzdata  libgcc1
```

If that goes well try

```
sudo apt-get install libc6:amd64 multiarch-support
```

---

### Post by mj125 on 2012-11-22
I try and I get this:
dpkg: dependency problems prevent configuration of libc6:amd64:
 libc6:amd64 depends on libgcc1; however:
  Package libgcc1 is not installed.
 libc6:amd64 depends on tzdata; however:
  Package tzdata is not installed.

dpkg: error processing libc6:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of multiarch-support:
 multiarch-support depends on libc6 (>= 2.3.6-2); however:
  Package libc6:amd64 is not configured yet.

dpkg: error processing multiarch-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6:amd64
 multiarch-support

---

### Post by mj125 on 2012-11-22
I can't install any thing. it does'nt help me.

---

### Post by papibe on 2012-11-22
Threads merged.

---

