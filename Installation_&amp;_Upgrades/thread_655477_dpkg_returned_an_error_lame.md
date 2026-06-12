---
title: "dpkg returned an error: lame"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by finneces on 2008-01-01
Hi everyone,

Every time I try to install a package, for example lame I get:
```
apt-get install lame 

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up dhcp3-server (3.0.5-3ubuntu4) ...
sed: -e expression #1, char 61: unknown option to `s'
dpkg: error processing dhcp3-server (--configure):
 subprocess post-installation script returned error exit status 1

```

Lame!
I even get that while trying to remove packages:
 ```
apt-get remove --purge firestarter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firestarter is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-16 libquicktime0 linux-headers-2.6.20-16-generic
  libjack0.100.0-0 emacs21-common linux-headers-2.6.20-16-server libgpod1
  emacs21-bin-common libstlport5.1 libslab0 rcs feisty-wallpapers
  feisty-session-splashes emacs21 libswfdec0.3 libflac++5c2 xaw3dg libgs-esp8
  libgdiplus
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up dhcp3-server (3.0.5-3ubuntu4) ...
sed: -e expression #1, char 61: unknown option to `s'
dpkg: error processing dhcp3-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dhcp3-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas?

Thanks!

---

### Post by mikesignguy on 2008-01-01
do what it says

apt-get autoremove

then try again

---

### Post by zvacet on 2008-01-01
```
sudo dpkg --configure -a
```

or

```
sudo apt-get -f install
```

---

### Post by finneces on 2008-01-02
I followed both of your instructions and I still get the problem:
```
dpkg --configure -a
Setting up dhcp3-server (3.0.5-3ubuntu4) ...
[COLOR="Red"]sed: -e expression #1, char 61: unknown option to `s'
dpkg: error processing dhcp3-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dhcp3-serve[/COLOR]r
```

```
apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up dhcp3-server (3.0.5-3ubuntu4) ...
[COLOR="Red"]sed: -e expression #1, char 61: unknown option to `s'
dpkg: error processing dhcp3-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dhcp3-server
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
```


```
apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-16 libquicktime0 linux-headers-2.6.20-16-generic
  libjack0.100.0-0 emacs21-common linux-headers-2.6.20-16-server libgpod1
  emacs21-bin-common libstlport5.1 libslab0 rcs feisty-wallpapers
  feisty-session-splashes emacs21 libswfdec0.3 libflac++5c2 xaw3dg libgs-esp8
  libgdiplus
The following packages will be REMOVED:
  emacs21 emacs21-bin-common emacs21-common feisty-session-splashes
  feisty-wallpapers libflac++5c2 libgdiplus libgpod1 libgs-esp8
  libjack0.100.0-0 libquicktime0 libslab0 libstlport5.1 libswfdec0.3
  linux-headers-2.6.20-16 linux-headers-2.6.20-16-generic
  linux-headers-2.6.20-16-server rcs xaw3dg
0 upgraded, 0 newly installed, 19 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 130MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 162851 files and directories currently installed.)
Removing emacs21 ...
emacs-remove emacs21
emacsen-common: Handling removal of emacsen flavor emacs21
emacsen-common: purging byte-compiled files for emacs21
remove/dictionaries-common: Purging byte-compiled files for flavour emacs21
Removing emacs21-bin-common ...
Removing emacs21-common ...
Removing feisty-session-splashes ...
Removing feisty-wallpapers ...
Removing libflac++5c2 ...
Removing libgdiplus ...
Removing libgpod1 ...
Removing libgs-esp8 ...
Removing libjack0.100.0-0 ...
Removing libquicktime0 ...
Removing libslab0 ...
Removing libstlport5.1 ...
Removing libswfdec0.3 ...
Removing linux-headers-2.6.20-16-generic ...
Removing linux-headers-2.6.20-16-server ...
Removing linux-headers-2.6.20-16 ...
Removing rcs ...
Removing xaw3dg ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up dhcp3-server (3.0.5-3ubuntu4) ...
[COLOR="Red"]sed: -e expression #1, char 61: unknown option to `s'
dpkg: error processing dhcp3-server (--configure):
 subprocess post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

```

Is it something to do with sed?  Although it gives this error, I am still able to install packages successfully, so maybe its not a big deal, but I fear it could be related to my other thread problem that Im having with my LAN, or could result in some other problem in the future...  Hmm.  Thanks!

---

### Post by zvacet on 2008-01-02
```
sudo apt-get install --reinstall dhcp3-server
```

---

