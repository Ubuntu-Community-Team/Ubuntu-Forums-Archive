---
title: "Packages stopped updating"
date: 2024-03-01
forum: Installation &amp; Upgrades
---

### Post by olegev on 2024-03-01
A month ago I installed Ubuntu 22.04, enjoyed life, updated, but yesterday everything broke - I can&#8217;t update a single package.
What's happened? Can it be repaired?

```
oleg@oleg-maibook:~$ sudo apt update
[sudo] password for oleg: 
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) jammy InRelease                                                                          
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease [119 kB]                                                                 
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease                                                             
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]
Hit:6 [https://packages.microsoft.com/repos/edge](https://packages.microsoft.com/repos/edge) stable InRelease              
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-proposed InRelease [270 kB]      
Hit:8 [https://repo.protonvpn.com/debian](https://repo.protonvpn.com/debian) stable InRelease
Fetched 499 kB in 1s (430 kB/s)                         
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
26 packages can be upgraded. Run 'apt list --upgradable' to see them.
oleg@oleg-maibook:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  vlc-plugin-qt libvlc5 vlc-data libvlccore9 vlc imagemagick vlc-bin vlc-l10n
  libopenexr25 libpostproc55 libmagickcore-6.q16-6-extra vlc-plugin-samba
  libmagickwand-6.q16-6 libavcodec-extra58 vlc-plugin-notify libavutil56
  imagemagick-6.q16 libswscale5 libeditorconfig0 libmagickcore-6.q16-6
  vlc-plugin-access-extra vlc-plugin-skins2 libgsl27 vlc-plugin-video-splitter
  libswresample3 imagemagick-6-common vlc-plugin-video-output libavformat58
  libgslcblas0 libvlc-bin vlc-plugin-base vlc-plugin-visualization
  libavfilter7
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)
The following packages will be upgraded:
  binutils binutils-common binutils-x86-64-linux-gnu dnsmasq-base dpkg dpkg-dev less libbinutils libcpanel-json-xs-perl libctf-nobfd0 libctf0
  libde265-0 libdpkg-perl libssl3 libssl3:i386 libtiff5 libtiff5:i386 libuv1 libxml2 libxml2:i386 libxml2-dev libxml2-utils microsoft-edge-stable
  openssl update-notifier update-notifier-common
26 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
20 standard LTS security updates
Need to get 0 B/181 MB of archives.
After this operation, 296 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
dpkg: error processing archive /var/cache/apt/archives/dpkg_1.21.1ubuntu2.3_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
Errors were encountered while processing:
 /var/cache/apt/archives/dpkg_1.21.1ubuntu2.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ActionParsnip on 2024-03-01
Try:
```

sudo apt -f install
sudo dpkg --configure -a

```
May help

---

### Post by olegev on 2024-03-01
> **ActionParsnip said:**
> Try:
```

sudo apt -f install
sudo dpkg --configure -a

```
May help

Unfortunately this didn't help

```
oleg@oleg-maibook:~$ sudo apt -f install
[sudo] password for oleg: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
oleg@oleg-maibook:~$ sudo dpkg --configure -a
oleg@oleg-maibook:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  vlc-plugin-qt libvlc5 vlc-data libvlccore9 vlc imagemagick vlc-bin vlc-l10n
  libopenexr25 libpostproc55 libmagickcore-6.q16-6-extra vlc-plugin-samba
  libmagickwand-6.q16-6 libavcodec-extra58 vlc-plugin-notify libavutil56
  imagemagick-6.q16 libswscale5 libeditorconfig0 libmagickcore-6.q16-6
  vlc-plugin-access-extra vlc-plugin-skins2 libgsl27 vlc-plugin-video-splitter
  libswresample3 imagemagick-6-common vlc-plugin-video-output libavformat58
  libgslcblas0 libvlc-bin vlc-plugin-base vlc-plugin-visualization
  libavfilter7
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)
The following packages will be upgraded:
  binutils binutils-common binutils-x86-64-linux-gnu dnsmasq-base dpkg dpkg-dev less libbinutils libcpanel-json-xs-perl libctf-nobfd0 libctf0 libde265-0 libdpkg-perl
  libssl3 libssl3:i386 libtiff5 libtiff5:i386 libuv1 libxml2 libxml2:i386 libxml2-dev libxml2-utils microsoft-edge-stable openssl update-notifier
  update-notifier-common
26 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
20 standard LTS security updates
Need to get 181 MB of archives.
After this operation, 296 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [https://packages.microsoft.com/repos/edge](https://packages.microsoft.com/repos/edge) stable/main amd64 microsoft-edge-stable amd64 122.0.2365.63-1 [166 MB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-proposed/main amd64 dpkg amd64 1.21.1ubuntu2.3 [1,239 kB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-proposed/main amd64 update-notifier amd64 3.192.54.7 [62.4 kB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-proposed/main amd64 update-notifier-common all 3.192.54.7 [185 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libssl3 i386 3.0.2-0ubuntu1.15 [1,946 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libssl3 amd64 3.0.2-0ubuntu1.15 [1,905 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 less amd64 590-1ubuntu0.22.04.2 [143 kB]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libxml2-dev amd64 2.9.13+dfsg-1ubuntu0.4 [804 kB]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libxml2 i386 2.9.13+dfsg-1ubuntu0.4 [726 kB]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libxml2 amd64 2.9.13+dfsg-1ubuntu0.4 [763 kB]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 openssl amd64 3.0.2-0ubuntu1.15 [1,186 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libuv1 amd64 1.43.0-1ubuntu0.1 [92.7 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libctf-nobfd0 amd64 2.38-4ubuntu2.6 [108 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libctf0 amd64 2.38-4ubuntu2.6 [103 kB]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 binutils-x86-64-linux-gnu amd64 2.38-4ubuntu2.6 [2,326 kB]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 binutils-common amd64 2.38-4ubuntu2.6 [222 kB]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 binutils amd64 2.38-4ubuntu2.6 [3,200 B]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libbinutils amd64 2.38-4ubuntu2.6 [662 kB]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 dnsmasq-base amd64 2.90-0ubuntu0.22.04.1 [374 kB]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-proposed/main amd64 dpkg-dev all 1.21.1ubuntu2.3 [922 kB]
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-proposed/main amd64 libdpkg-perl all 1.21.1ubuntu2.3 [237 kB]
Get:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libcpanel-json-xs-perl amd64 4.27-1ubuntu0.1 [115 kB]
Get:23 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 libde265-0 amd64 1.0.8-1ubuntu0.2 [289 kB]
Get:24 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libtiff5 i386 4.3.0-6ubuntu0.8 [200 kB]
Get:25 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libtiff5 amd64 4.3.0-6ubuntu0.8 [185 kB]
Get:26 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libxml2-utils amd64 2.9.13+dfsg-1ubuntu0.4 [40.2 kB]
Fetched 181 MB in 24s (7,678 kB/s)                                                                                                                                     
Preconfiguring packages ...
dpkg: error processing archive /var/cache/apt/archives/dpkg_1.21.1ubuntu2.3_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
Errors were encountered while processing:
 /var/cache/apt/archives/dpkg_1.21.1ubuntu2.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by deadflowr on 2024-03-01
Turn off proposed updates.

Proposed updates are for testing/testers and should be considered unstable.

Packages in proposed tend to be more in flux than updates or security,
since those can and will be updated and changed or altogether removed because other testers file bugs and they upload new versions all the time.

---

### Post by olegev on 2024-03-01
> **deadflowr said:**
> Turn off proposed updates.

Proposed updates are for testing/testers and should be considered unstable.

Packages in proposed tend to be more in flux than updates or security,
since those can and will be updated and changed or altogether removed because other testers file bugs and they upload new versions all the time.

Which ones exactly proposed updates I have turn off?

---

### Post by ubfan1 on 2024-03-01
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-proposed InRelease [270 kB]
Software&Updates/Developer options can turn them off, or just edit the sources.list/sources.list.d directory files.

---

### Post by olegev on 2024-03-02
> **ubfan1 said:**
> Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-proposed InRelease [270 kB]
Software&Updates/Developer options can turn them off, or just edit the sources.list/sources.list.d directory files.

Ok, I turn off Software&Updates/Developer options, but the errors remain, and now I can't install any package  
```
oleg@oleg-maibook:~$ sudo apt update
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease                                                
Hit:3 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) jammy InRelease                                                
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease                                    
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-security InRelease              
Hit:6 [https://packages.microsoft.com/repos/edge](https://packages.microsoft.com/repos/edge) stable InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
21 packages can be upgraded. Run 'apt list --upgradable' to see them.
```
```
oleg@oleg-maibook:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
```
```
oleg@oleg-maibook:~$ sudo dpkg --configure -a
oleg@oleg-maibook:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  vlc-plugin-qt libvlc5 vlc-data libvlccore9 vlc imagemagick vlc-bin vlc-l10n
  libopenexr25 libpostproc55 libmagickcore-6.q16-6-extra vlc-plugin-samba
  libmagickwand-6.q16-6 libavcodec-extra58 vlc-plugin-notify libavutil56
  imagemagick-6.q16 libswscale5 libeditorconfig0 libmagickcore-6.q16-6
  vlc-plugin-access-extra vlc-plugin-skins2 libgsl27 vlc-plugin-video-splitter
  libswresample3 imagemagick-6-common vlc-plugin-video-output libavformat58
  libgslcblas0 libvlc-bin vlc-plugin-base vlc-plugin-visualization
  libavfilter7
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)
The following packages will be upgraded:
  binutils binutils-common binutils-x86-64-linux-gnu dnsmasq-base less libbinutils libcpanel-json-xs-perl libctf-nobfd0
  libctf0 libde265-0 libssl3 libssl3:i386 libtiff5 libtiff5:i386 libuv1 libxml2 libxml2:i386 libxml2-dev libxml2-utils
  microsoft-edge-stable openssl
21 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
20 standard LTS security updates
Need to get 0 B/178 MB of archives.
After this operation, 295 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/00-microsoft-edge-stable_122.0.2365.63-1_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/01-libssl3_3.0.2-0ubuntu1.15_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/02-libssl3_3.0.2-0ubuntu1.15_i386.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/03-less_590-1ubuntu0.22.04.2_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/04-
libxml2-dev_2.9.13+dfsg-1ubuntu0.4_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/05-
libxml2_2.9.13+dfsg-1ubuntu0.4_i386.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/06-
libxml2_2.9.13+dfsg-1ubuntu0.4_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/07-
openssl_3.0.2-0ubuntu1.15_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/08-
libuv1_1.43.0-1ubuntu0.1_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/09-
libctf-nobfd0_2.38-4ubuntu2.6_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/10-
libctf0_2.38-4ubuntu2.6_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/11-
binutils-x86-64-linux-gnu_2.38-4ubuntu2.6_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/12-
binutils-common_2.38-4ubuntu2.6_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/13-
binutils_2.38-4ubuntu2.6_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/14-
libbinutils_2.38-4ubuntu2.6_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/15-
dnsmasq-base_2.90-0ubuntu0.22.04.1_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/16-
libcpanel-json-xs-perl_4.27-1ubuntu0.1_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/17-
libde265-0_1.0.8-1ubuntu0.2_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/18-
libtiff5_4.3.0-6ubuntu0.8_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/19-
libtiff5_4.3.0-6ubuntu0.8_i386.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-lomDzU/20-
libxml2-utils_2.9.13+dfsg-1ubuntu0.4_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /tmp/apt-dpkg-install-lomDzU/00-microsoft-edge-stable_122.0.2365.63-1_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/01-libssl3_3.0.2-0ubuntu1.15_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/02-libssl3_3.0.2-0ubuntu1.15_i386.deb
 /tmp/apt-dpkg-install-lomDzU/03-less_590-1ubuntu0.22.04.2_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/04-libxml2-dev_2.9.13+dfsg-1ubuntu0.4_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/05-libxml2_2.9.13+dfsg-1ubuntu0.4_i386.deb
 /tmp/apt-dpkg-install-lomDzU/06-libxml2_2.9.13+dfsg-1ubuntu0.4_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/07-openssl_3.0.2-0ubuntu1.15_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/08-libuv1_1.43.0-1ubuntu0.1_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/09-libctf-nobfd0_2.38-4ubuntu2.6_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/10-libctf0_2.38-4ubuntu2.6_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/11-binutils-x86-64-linux-gnu_2.38-4ubuntu2.6_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/12-binutils-common_2.38-4ubuntu2.6_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/13-binutils_2.38-4ubuntu2.6_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/14-libbinutils_2.38-4ubuntu2.6_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/15-dnsmasq-base_2.90-0ubuntu0.22.04.1_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/16-libcpanel-json-xs-perl_4.27-1ubuntu0.1_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/17-libde265-0_1.0.8-1ubuntu0.2_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/18-libtiff5_4.3.0-6ubuntu0.8_amd64.deb
 /tmp/apt-dpkg-install-lomDzU/19-libtiff5_4.3.0-6ubuntu0.8_i386.deb
 /tmp/apt-dpkg-install-lomDzU/20-libxml2-utils_2.9.13+dfsg-1ubuntu0.4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by deadflowr on 2024-03-02
Hmm,
try cleaning it up 
```
sudo apt clean
sudo apt update
sudo dpkg --configure -a
sudo apt install -f
```

---

### Post by olegev on 2024-03-02
> **deadflowr said:**
> Hmm,
try cleaning it up 
```
sudo apt clean
sudo apt update
sudo dpkg --configure -a
sudo apt install -f
```

No, the same errors

```
oleg@oleg-maibook:~$ sudo apt clean
```
[sudo] password for oleg: 
```
oleg@oleg-maibook:~$ sudo apt update
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease [119 kB]                      
Hit:3 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) jammy InRelease                                                          
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease                                                        
Hit:5 [https://packages.microsoft.com/repos/edge](https://packages.microsoft.com/repos/edge) stable InRelease
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]
Fetched 229 kB in 1s (237 kB/s)    
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
21 packages can be upgraded. Run 'apt list --upgradable' to see them.
```
```
oleg@oleg-maibook:~$ sudo dpkg --configure -a
oleg@oleg-maibook:~$ sudo apt install -f
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
```
```
oleg@oleg-maibook:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  vlc-plugin-qt libvlc5 vlc-data libvlccore9 vlc imagemagick vlc-bin vlc-l10n
  libopenexr25 libpostproc55 libmagickcore-6.q16-6-extra vlc-plugin-samba
  libmagickwand-6.q16-6 libavcodec-extra58 vlc-plugin-notify libavutil56
  imagemagick-6.q16 libswscale5 libeditorconfig0 libmagickcore-6.q16-6
  vlc-plugin-access-extra vlc-plugin-skins2 libgsl27 vlc-plugin-video-splitter
  libswresample3 imagemagick-6-common vlc-plugin-video-output libavformat58
  libgslcblas0 libvlc-bin vlc-plugin-base vlc-plugin-visualization
  libavfilter7
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)
The following packages will be upgraded:
  binutils binutils-common binutils-x86-64-linux-gnu dnsmasq-base less libbinutils libcpanel-json-xs-perl libctf-nobfd0 libctf0
  libde265-0 libssl3 libssl3:i386 libtiff5 libtiff5:i386 libuv1 libxml2 libxml2:i386 libxml2-dev libxml2-utils microsoft-edge-stable
  openssl
21 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
20 standard LTS security updates
Need to get 178 MB of archives.
After this operation, 295 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libssl3 i386 3.0.2-0ubuntu1.15 [1,946 kB]
Get:2 [https://packages.microsoft.com/repos/edge](https://packages.microsoft.com/repos/edge) stable/main amd64 microsoft-edge-stable amd64 122.0.2365.63-1 [166 MB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libssl3 amd64 3.0.2-0ubuntu1.15 [1,905 kB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 less amd64 590-1ubuntu0.22.04.2 [143 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libxml2-dev amd64 2.9.13+dfsg-1ubuntu0.4 [804 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libxml2 i386 2.9.13+dfsg-1ubuntu0.4 [726 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libxml2 amd64 2.9.13+dfsg-1ubuntu0.4 [763 kB]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 openssl amd64 3.0.2-0ubuntu1.15 [1,186 kB]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libuv1 amd64 1.43.0-1ubuntu0.1 [92.7 kB]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libctf-nobfd0 amd64 2.38-4ubuntu2.6 [108 kB]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libctf0 amd64 2.38-4ubuntu2.6 [103 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 binutils-x86-64-linux-gnu amd64 2.38-4ubuntu2.6 [2,326 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 binutils-common amd64 2.38-4ubuntu2.6 [222 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 binutils amd64 2.38-4ubuntu2.6 [3,200 B]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libbinutils amd64 2.38-4ubuntu2.6 [662 kB]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 dnsmasq-base amd64 2.90-0ubuntu0.22.04.1 [374 kB]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libcpanel-json-xs-perl amd64 4.27-1ubuntu0.1 [115 kB]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 libde265-0 amd64 1.0.8-1ubuntu0.2 [289 kB]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libtiff5 amd64 4.3.0-6ubuntu0.8 [185 kB]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 libtiff5 i386 4.3.0-6ubuntu0.8 [200 kB]
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libxml2-utils amd64 2.9.13+dfsg-1ubuntu0.4 [40.2 kB]
Fetched 178 MB in 23s (7,599 kB/s)                                                                                                      
Preconfiguring packages ...
dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/00-microsoft-edge-stable_122.0.2365.63-1_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/01-libssl3_3.0.2-0ubuntu1.15_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/02-libssl3_3.0.2-0ubuntu1.15_i386.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/03-less_590-1ubuntu0.22.04.2_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/04-libxml2-dev_
2.9.13+dfsg-1ubuntu0.4_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/05-libxml2_2.9.
13+dfsg-1ubuntu0.4_i386.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/06-libxml2_2.9.
13+dfsg-1ubuntu0.4_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/07-openssl_3.0.
2-0ubuntu1.15_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/08-libuv1_1.43.
0-1ubuntu0.1_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/09-libctf-nobfd
0_2.38-4ubuntu2.6_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/10-libctf0_2.38
-4ubuntu2.6_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/11-binutils-x86
-64-linux-gnu_2.38-4ubuntu2.6_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/12-binutils-com
mon_2.38-4ubuntu2.6_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/13-binutils_2.3
8-4ubuntu2.6_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/14-libbinutils_
2.38-4ubuntu2.6_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/15-dnsmasq-base
_2.90-0ubuntu0.22.04.1_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/16-libcpanel-js
on-xs-perl_4.27-1ubuntu0.1_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/17-libde265-0_1
.0.8-1ubuntu0.2_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/18-libtiff5_4.3
.0-6ubuntu0.8_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/19-libtiff5_4.3
.0-6ubuntu0.8_i386.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              dpkg: error processing archive /tmp/apt-dpkg-install-Ag9Ju8/20-libxml2-util
s_2.9.13+dfsg-1ubuntu0.4_amd64.deb (--unpack):
 subprocess dpkg-split returned error exit status 7
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /tmp/apt-dpkg-install-Ag9Ju8/00-microsoft-edge-stable_122.0.2365.63-1_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/01-libssl3_3.0.2-0ubuntu1.15_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/02-libssl3_3.0.2-0ubuntu1.15_i386.deb
 /tmp/apt-dpkg-install-Ag9Ju8/03-less_590-1ubuntu0.22.04.2_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/04-libxml2-dev_2.9.13+dfsg-1ubuntu0.4_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/05-libxml2_2.9.13+dfsg-1ubuntu0.4_i386.deb
 /tmp/apt-dpkg-install-Ag9Ju8/06-libxml2_2.9.13+dfsg-1ubuntu0.4_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/07-openssl_3.0.2-0ubuntu1.15_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/08-libuv1_1.43.0-1ubuntu0.1_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/09-libctf-nobfd0_2.38-4ubuntu2.6_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/10-libctf0_2.38-4ubuntu2.6_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/11-binutils-x86-64-linux-gnu_2.38-4ubuntu2.6_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/12-binutils-common_2.38-4ubuntu2.6_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/13-binutils_2.38-4ubuntu2.6_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/14-libbinutils_2.38-4ubuntu2.6_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/15-dnsmasq-base_2.90-0ubuntu0.22.04.1_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/16-libcpanel-json-xs-perl_4.27-1ubuntu0.1_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/17-libde265-0_1.0.8-1ubuntu0.2_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/18-libtiff5_4.3.0-6ubuntu0.8_amd64.deb
 /tmp/apt-dpkg-install-Ag9Ju8/19-libtiff5_4.3.0-6ubuntu0.8_i386.deb
 /tmp/apt-dpkg-install-Ag9Ju8/20-libxml2-utils_2.9.13+dfsg-1ubuntu0.4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

