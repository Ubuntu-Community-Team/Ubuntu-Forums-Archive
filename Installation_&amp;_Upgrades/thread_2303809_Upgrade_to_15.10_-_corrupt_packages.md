---
title: "Upgrade to 15.10 - corrupt packages"
date: 2015-11-21
forum: Installation &amp; Upgrades
---

### Post by stef7 on 2015-11-21
I tried to upgrade my NUC which had xubuntu 15.04 installed to 15.10 using 'do_upgrade_release'.

I do not believe the issues I'm having are 'x'-ubuntu specific.

Prior attempts to upgrade the 15.04 installation (ie non-release upgrades), failed due to corrupt
packages on download servers resulting in 'Hash Sum mismatch' messages. I tried many
mirrors incl the 'Main server' and waiting for weeks for bad packages to be fixed. Eventually 
'fumbled' my way through to get an updated system.

Following the 'do_release_upgrade' I seem to have an upgraded system, but some packages were 
again not upgraded do to similar issues. Now my apt system seems to be messed up - see output below.

I've been using ubuntu for 12 yrs - but this really seems a shambles. I've tried all sorts incl downloading
the packages directly from mirrors and installing with dpkg. How can apparently so many corrupt packages
make it to the download servers??? Or am I doing something fundamentally wrong???

Any tips on repairing this system are welcome!!!


```
root@sam:~/pkgs# apt-get upgrade
Hit http://archive.ubuntu.com wily/main amd64 Packages                  
Hit http://archive.ubuntu.com wily/main i386 Packages                   
Hit http://archive.ubuntu.com wily/main Translation-en_GB                 
Hit http://archive.ubuntu.com wily/main Translation-en                    
Get:5 http://archive.ubuntu.com wily-updates/main Sources [22.7 kB]
Get:6 http://archive.ubuntu.com wily-updates/main amd64 Packages [58.7 kB]                           
Get:7 http://security.ubuntu.com wily-security/main i386 Packages [39.8 kB]                          
Get:8 http://archive.ubuntu.com wily-updates/main i386 Packages [57.4 kB]                                   
Hit http://security.ubuntu.com wily-security/main Translation-en                                                      
Hit http://archive.ubuntu.com wily-updates/main Translation-en                     
Get:9 http://archive.ubuntu.com wily-security/main Sources [15.6 kB]                                
Get:10 http://archive.ubuntu.com wily-security/main amd64 Packages [40.5 kB]
Get:11 http://archive.ubuntu.com wily-security/main i386 Packages [39.8 kB]
Hit http://archive.ubuntu.com wily-security/main Translation-en
Fetched 508 kB in 3s (148 kB/s)                   
Reading package lists... Done



root@sam:~/pkgs# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 aptitude : Depends: aptitude-common (= 0.6.11-1ubuntu3) but 0.7.3-1ubuntu1 is installed
            Depends: libcwidget3 but it is not installable
            Depends: libsigc++-2.0-0c2a (>= 2.2.0) but it is not installable
            Depends: libxapian22 but it is not installable
 dpkg : Breaks: software-center (< 13.10-0ubuntu9~) but 13.10-0ubuntu6.1 is installed
 gparted : Depends: libatkmm-1.6-1v5 (>= 2.22.1) but it is not installed
           Depends: libglibmm-2.4-1v5 (>= 2.44.0) but it is not installed
           Depends: libgtkmm-2.4-1v5 (>= 1:2.24.0) but it is not installed
           Depends: libpangomm-1.4-1v5 (>= 2.36.0) but it is not installed
 libapt-pkg4.16 : Breaks: aptitude (< 0.7-1ubuntu1.1)
                  Breaks: aptitude:i386 (< 0.7-1ubuntu1.1)
                  Breaks: libapt-pkg-perl (< 0.1.29build4) but 0.1.29build2 is installed
 libatkmm-1.6-1 : Depends: libsigc++-2.0-0c2a (>= 2.2.0) but it is not installable
 libglibmm-2.4-1c2a : Depends: libsigc++-2.0-0c2a (>= 2.2.0) but it is not installable
 libgtkmm-2.4-1c2a : Depends: libcairomm-1.0-1 (>= 1.6.4) but it is not installable
                     Depends: libpangomm-1.4-1 (>= 2.27.1) but it is not installable
                     Depends: libsigc++-2.0-0c2a (>= 2.2.0) but it is not installable
 libvlc5 : Depends: libvlccore8 (= 2.2.0-1) but it is not installable
 vlc : Depends: libvlccore8 (>= 2.2.0~pre1) but it is not installable
       Recommends: vlc-plugin-notify (= 2.2.0-1) but it is not installable
 vlc-nox : Depends: libvlccore8 (>= 2.2.0~pre1) but it is not installable
 vlc-plugin-samba : Depends: libvlccore8 (>= 2.2.0~pre1) but it is not installable
E: Unmet dependencies. Try using -f.


root@sam:~/pkgs# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libboost-iostreams1.55.0 libqt4-declarative libqt4-network libqt4-script libqt4-sql libqt4-sql-mysql libqt4-xml libqt4-xmlpatterns libqtcore4 libqtdbus4 libqtgui4
  libupnp6 vlc-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aptitude libapt-pkg-perl libatkmm-1.6-1v5 libcairomm-1.0-1v5 libglibmm-2.4-1v5 libgtkmm-2.4-1v5 libpangomm-1.4-1v5 software-center
Suggested packages:
  debtags tasksel
The following packages will be REMOVED
  libatkmm-1.6-1 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a libvlc5 vlc vlc-nox vlc-plugin-samba
The following NEW packages will be installed
  libatkmm-1.6-1v5 libcairomm-1.0-1v5 libglibmm-2.4-1v5 libgtkmm-2.4-1v5 libpangomm-1.4-1v5
The following packages will be upgraded:
  aptitude libapt-pkg-perl software-center
3 to upgrade, 5 to newly install, 7 to remove and 765 not to upgrade.
12 not fully installed or removed.
Need to get 671 kB/3,006 kB of archives.
After this operation, 17.1 MB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu/ wily/main libgtkmm-2.4-1v5 amd64 1:2.24.4-2 [671 kB]
Fetched 671 kB in 1s (616 kB/s)           
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gtkmm2.4/libgtkmm-2.4-1v5_2.24.4-2_amd64.deb  Hash Sum mismatch


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by ian-weisser on 2015-11-21
I don't see errors indicating *corrupt* packages. I see lots of errors indicating *missing* packages, perhaps due to network problems.

Take the error message one problem at a time.

For example, let's look at the very first error: aptitude.


> **stef7 said:**
> ```

 aptitude : Depends: aptitude-common (= 0.6.11-1ubuntu3) but 0.7.3-1ubuntu1 is installed
            Depends: libcwidget3 but it is not installable
            Depends: libsigc++-2.0-0c2a (>= 2.2.0) but it is not installable
            Depends: libxapian22 but it is not installable
[...]
 libapt-pkg4.16 : Breaks: aptitude (< 0.7-1ubuntu1.1)
                  Breaks: aptitude:i386 (< 0.7-1ubuntu1.1)
                  Breaks: libapt-pkg-perl (< 0.1.29build4) but 0.1.29build2 is installed
[...]

```

Looks like a simple pinned or missing package. Easy to fix.
Did you, for some reason, pin aptitide to a specific version in the past? If so, remove the pin.
Otherwise, simply...
1) Remove the old vivid version of aptitude
2) Autoremove the older dependencies
3) Install the wily version of aptitude + dependencies
4) Autoclean your package cache

I suspect problems like this occur when some repositories are unavailable to your NUC...so it's forced to work with what it has.

One easy way around such flaky network connections is to use apt's --download-only flag. The package will be stored in your package cache. Once *all* packages are properly downloaded, run the install without --download-only to install from those cached packages.

---

### Post by stef7 on 2015-11-22
Thanks a lot @ian-weisser - that helped me get rid of the dependency issues.

Small but important correction: point 1. should be remove aptitude, not apt.

There were no pinned packages.

However I still maintain there are corrupt package issues:

For instance:

```
root@sam:/tmp# apt-get update
Hit http://archive.ubuntu.com wily InRelease
Hit http://archive.ubuntu.com wily-security InRelease
Get:1 http://archive.ubuntu.com wily-updates InRelease [64.4 kB]
Get:2 http://archive.ubuntu.com wily-security/main amd64 Packages [40.5 kB]
Get:3 http://archive.ubuntu.com wily-updates/main Sources [22.7 kB]
Get:4 http://archive.ubuntu.com wily-updates/restricted Sources [3,741 B]
Get:5 http://archive.ubuntu.com wily-updates/main amd64 Packages [58.6 kB]
Get:6 http://archive.ubuntu.com wily-updates/restricted amd64 Packages [13.3 kB]
Get:7 http://archive.ubuntu.com wily-updates/main i386 Packages [57.4 kB]
Get:8 http://archive.ubuntu.com wily-updates/restricted i386 Packages [13.4 kB]                                                                                             
Hit http://archive.ubuntu.com wily/main Sources                                                                                                                             
Hit http://archive.ubuntu.com wily/restricted Sources                                                                                                                       
Hit http://archive.ubuntu.com wily/main amd64 Packages                                                                                                                      
Hit http://archive.ubuntu.com wily/restricted amd64 Packages                                                                                                                
Hit http://archive.ubuntu.com wily/main i386 Packages                                                                                                                       
Hit http://archive.ubuntu.com wily/restricted i386 Packages                                                                                                                 
Hit http://archive.ubuntu.com wily/main Translation-en_GB                                                                                                                   
Hit http://archive.ubuntu.com wily/main Translation-en                                                                                                                      
Hit http://archive.ubuntu.com wily/restricted Translation-en_GB                                                                                                             
Hit http://archive.ubuntu.com wily/restricted Translation-en                                                                                                                
Hit http://archive.ubuntu.com wily-security/main Sources                                                                                                                    
Hit http://archive.ubuntu.com wily-security/restricted Sources                                                                                                              
Hit http://archive.ubuntu.com wily-security/restricted amd64 Packages                                                                                                       
Hit http://archive.ubuntu.com wily-security/main i386 Packages                                                                                                              
Hit http://archive.ubuntu.com wily-security/restricted i386 Packages                                                                                                        
Hit http://archive.ubuntu.com wily-security/main Translation-en                                                                                                             
Hit http://archive.ubuntu.com wily-security/restricted Translation-en                                                                                                       
Hit http://archive.ubuntu.com wily-updates/main Translation-en                                                                                                              
Hit http://archive.ubuntu.com wily-updates/restricted Translation-en                                                                                                        
Err http://archive.ubuntu.com wily-updates/main amd64 Packages                                                                                                              
  404  Not Found [IP: 91.189.91.24 80]
Fetched 274 kB in 13s (20.5 kB/s)                                                                                                                                           
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.24 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.




root@sam:/tmp# ping -c1 91.189.91.24
PING 91.189.91.24 (91.189.91.24) 56(84) bytes of data.
64 bytes from 91.189.91.24: icmp_seq=1 ttl=49 time=130 ms




root@sam:/tmp# wget http://archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-amd64/Packages.gz
--2015-11-22 15:52:58--  http://archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-amd64/Packages.gz
Resolving archive.ubuntu.com (archive.ubuntu.com)... 91.189.91.23, 91.189.88.153, 91.189.91.13, ...
Connecting to archive.ubuntu.com (archive.ubuntu.com)|91.189.91.23|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 73499 (72K) [application/x-gzip]
Saving to: &#8216;Packages.gz&#8217;


Packages.gz                               100%[==========================================================================================>]  71.78K   131KB/s   in 0.5s   


2015-11-22 15:52:59 (131 KB/s) - &#8216;Packages.gz&#8217; saved [73499/73499]


root@sam:/tmp# file Packages.gz
Packages.gz: gzip compressed data, from Unix




root@sam:/tmp# gzip -d Packages.gz 


gzip: Packages.gz: **invalid compressed data--crc error**


gzip: Packages.gz: **invalid compressed data--length error**



```
So the package index for wily-updates/main amd64 is unavailable??


Another example:


```
root@sam:/tmp# apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libatkmm-1.6-1v5 libcairomm-1.0-1v5 libglibmm-2.4-1v5 libgtkmm-2.4-1v5 libpangomm-1.4-1v5 libparted-fs-resize0
Suggested packages:
  xfsprogs reiserfsprogs reiser4progs jfsutils mtools dmraid gpart libparted-dev
The following NEW packages will be installed
  gparted libatkmm-1.6-1v5 libcairomm-1.0-1v5 libglibmm-2.4-1v5 libgtkmm-2.4-1v5 libpangomm-1.4-1v5 libparted-fs-resize0
0 to upgrade, 7 to newly install, 0 to remove and 755 not to upgrade.
Need to get 1,724 kB of archives.
After this operation, 10.0 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu/ wily/main libparted-fs-resize0 amd64 3.2-7ubuntu1 [46.7 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ wily/main libglibmm-2.4-1v5 amd64 2.45.41.is.2.44.0-0ubuntu2 [450 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ wily/main libatkmm-1.6-1v5 amd64 2.22.7-3 [59.0 kB]                                                                                 
Get:4 http://archive.ubuntu.com/ubuntu/ wily/main libcairomm-1.0-1v5 amd64 1.11.2-0ubuntu3~gcc5 [40.6 kB]                                                                   
Get:5 http://archive.ubuntu.com/ubuntu/ wily/main libpangomm-1.4-1v5 amd64 2.36.0-2 [41.5 kB]                                                                               
Get:6 http://archive.ubuntu.com/ubuntu/ wily/main libgtkmm-2.4-1v5 amd64 1:2.24.4-2 [671 kB]                                                                                
Get:7 http://archive.ubuntu.com/ubuntu/ wily/main gparted amd64 0.19.0-3build1 [416 kB]                                                                                     
Fetched 1,724 kB in 41s (41.7 kB/s)                                                                                                                                         
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glibmm2.4/libglibmm-2.4-1v5_2.45.41.is.2.44.0-0ubuntu2_amd64.deb  Hash Sum mismatch


E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/atkmm1.6/libatkmm-1.6-1v5_2.22.7-3_amd64.deb  Hash Sum mismatch


E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/cairomm/libcairomm-1.0-1v5_1.11.2-0ubuntu3~gcc5_amd64.deb  Hash Sum mismatch


E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gtkmm2.4/libgtkmm-2.4-1v5_2.24.4-2_amd64.deb  Hash Sum mismatch


E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gparted/gparted_0.19.0-3build1_amd64.deb  Hash Sum mismatch


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@sam:/tmp# 
root@sam:/tmp# 
root@sam:/tmp# 
root@sam:/tmp# wget http://archive.ubuntu.com/ubuntu/pool/main/g/glibmm2.4/libglibmm-2.4-1v5_2.45.41.is.2.44.0-0ubuntu2_amd64.deb
--2015-11-22 15:57:40--  http://archive.ubuntu.com/ubuntu/pool/main/g/glibmm2.4/libglibmm-2.4-1v5_2.45.41.is.2.44.0-0ubuntu2_amd64.deb
Resolving archive.ubuntu.com (archive.ubuntu.com)... 91.189.88.153, 91.189.91.13, 91.189.88.149, ...
Connecting to archive.ubuntu.com (archive.ubuntu.com)|91.189.88.153|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 449570 (439K) [application/x-debian-package]
Saving to: &#8216;libglibmm-2.4-1v5_2.45.41.is.2.44.0-0ubuntu2_amd64.deb&#8217;


libglibmm-2.4-1v5_2.45.41.is.2.44.0-0ubuntu 100%[==========================================================================================>] 439.03K   118KB/s   in 3.7s   


2015-11-22 15:57:44 (118 KB/s) - &#8216;libglibmm-2.4-1v5_2.45.41.is.2.44.0-0ubuntu2_amd64.deb&#8217; saved [449570/449570]


root@sam:/tmp# 
root@sam:/tmp# 
root@sam:/tmp# dpkg -i ./libglibmm-2.4-1v5_2.45.41.is.2.44.0-0ubuntu2_amd64.deb 
Selecting previously unselected package libglibmm-2.4-1v5:amd64.
(Reading database ... 263929 files and directories currently installed.)
Preparing to unpack .../libglibmm-2.4-1v5_2.45.41.is.2.44.0-0ubuntu2_amd64.deb ...
Unpacking libglibmm-2.4-1v5:amd64 (2.45.41.is.2.44.0-0ubuntu2) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: **compressed data is corrupt**
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive ./libglibmm-2.4-1v5_2.45.41.is.2.44.0-0ubuntu2_amd64.deb (--install):
 cannot copy extracted data for './usr/lib/x86_64-linux-gnu/libgiomm-2.4.so.1.3.0' to '/usr/lib/x86_64-linux-gnu/libgiomm-2.4.so.1.3.0.dpkg-new': unexpected end of file or stream
Errors were encountered while processing:
 ./libglibmm-2.4-1v5_2.45.41.is.2.44.0-0ubuntu2_amd64.deb

```

---

### Post by stef7 on 2015-12-28
FINALLY this has been fixed.

---

