---
title: "libav* snow ball"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilna on 2009-08-25
Up to date (almost) Kubuntu Karmic. Let's upgrade:

```
$ sudo aptitude -P -V -v -W safe-upgrade
Reading package lists... Done                      
Building dependency tree                           
Reading state information... Done                  
Reading extended state information                 
Initializing package states... Done                
The following packages are BROKEN:                 
  libavcodec-unstripped-52 [4:0.5+svn20090609-2+unstripped2 -> 4:0.5+svn20090706-1ubuntu1+extra1]  
  libavdevice52 [4:0.5+svn20090609-1ubuntu3 -> 4:0.5+svn20090706-1ubuntu3]                         
  libavformat-unstripped-52 [4:0.5+svn20090609-2+unstripped2 -> 4:0.5+svn20090706-1ubuntu1+extra1]  
  libavutil-unstripped-49 [4:0.5+svn20090609-2+unstripped2 -> 4:0.5+svn20090706-1ubuntu1+extra1]    
  libk3b6-extracodecs [1.66.0~alpha2-0ubuntu5 -> 1.66.0~alpha2-0ubuntu6]  libpostproc-extra-51  libswscale-extra-0
The following partially installed packages will be configured:
  libpostproc-unstripped-51  libswscale-unstripped-0
5 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 213kB of archives. After unpacking 6312kB will be freed.
The following packages have unmet dependencies:
  libk3b6-extracodecs: Depends: libavcodec52 (>= 3:0.svn20090303-1) but it is not installable
                       Depends: libavformat52 (>= 3:0.svn20090303-1) but it is not installable
                       Depends: libavutil49 (>= 3:0.svn20090303-1) but it is not installable
  libavdevice52: Depends: libavcodec52 (>= 4:0.5+svn20090706) but it is not installable
                 Depends: libavcodec52 (< 4:0.5+svn20090706-99) but it is not installable
                 Depends: libavformat52 (>= 4:0.5+svn20090706) but it is not installable
                 Depends: libavformat52 (< 4:0.5+svn20090706-99) but it is not installable
                 Depends: libavutil49 (>= 4:0.5+svn20090706) but it is not installable
                 Depends: libavutil49 (< 4:0.5+svn20090706-99) but it is not installable
  libpostproc-extra-51: Depends: libavutil-extra-49 (>= 4:0.5+svn20090706) but it is not installable
                        Depends: libavutil-extra-49 (< 4:0.5+svn20090706-99) but it is not installable
  libavcodec-unstripped-52: Depends: libavcodec-extra-52 (= 4:0.5+svn20090706-1ubuntu1+extra1) but it is not installable
  libswscale-extra-0: Depends: libavutil-extra-49 (>= 4:0.5+svn20090706) but it is not installable
                      Depends: libavutil-extra-49 (< 4:0.5+svn20090706-99) but it is not installable
  libavformat-unstripped-52: Depends: libavformat-extra-52 (= 4:0.5+svn20090706-1ubuntu1+extra1) but it is not installable
  libavutil-unstripped-49: Depends: libavutil-extra-49 (= 4:0.5+svn20090706-1ubuntu1+extra1) but it is not installable
Unable to resolve dependencies for the upgrade (no solution found).The following packages have unmet dependencies:
  libpostproc-extra-51: Depends: libavutil-extra-49 (>= 4:0.5+svn20090706) but it is not installable
                        Depends: libavutil-extra-49 (< 4:0.5+svn20090706-99) but it is not installable
  libswscale-extra-0: Depends: libavutil-extra-49 (>= 4:0.5+svn20090706) but it is not installable
                      Depends: libavutil-extra-49 (< 4:0.5+svn20090706-99) but it is not installable
```

Or let's try to install libavutil-extra-49:

```
$ sudo aptitude install libavutil-extra-49
Reading package lists... Done                        
Building dependency tree                             
Reading state information... Done                    
Reading extended state information                   
Initializing package states... Done                  
The following NEW packages will be installed:        
  libavutil-extra-49                                 
The following partially installed packages will be configured:
  libpostproc-extra-51 libpostproc-unstripped-51 libswscale-extra-0 libswscale-unstripped-0 
0 packages upgraded, 1 newly installed, 0 to remove and 5 not upgraded.                     
Need to get 0B/68.0kB of archives. After unpacking 156kB will be used.                      
Writing extended state information... Done                                                  
(Reading database ... 221041 files and directories currently installed.)                    
Unpacking libavutil-extra-49 (from .../libavutil-extra-49_4%3a0.5+svn20090706-1ubuntu1+extra1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libavutil-extra-49_4%3a0.5+svn20090706-1ubuntu1+extra1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libavutil.so.49.15.0', which is also in package libavutil-unstripped-49                     
Errors were encountered while processing:                                                                                  
 /var/cache/apt/archives/libavutil-extra-49_4%3a0.5+svn20090706-1ubuntu1+extra1_amd64.deb                                  
E: Sub-process /usr/bin/dpkg returned an error code (1)                                                                    
A package failed to install.  Trying to recover:                                                                           
dpkg: dependency problems prevent configuration of libswscale-extra-0:                                                     
 libswscale-extra-0 depends on libavutil-extra-49 (>= 4:0.5+svn20090706); however:                                         
  Package libavutil-extra-49 is not installed.                                                                             
 libswscale-extra-0 depends on libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:                                      
  Package libavutil-extra-49 is not installed.                                                                             
dpkg: error processing libswscale-extra-0 (--configure):                                                                   
 dependency problems - leaving unconfigured                                                                                
dpkg: dependency problems prevent configuration of libswscale-unstripped-0:                                                
 libswscale-unstripped-0 depends on libswscale-extra-0 (= 4:0.5+svn20090706-1ubuntu1+extra1); however:
  Package libswscale-extra-0 is not configured yet.
dpkg: error processing libswscale-unstripped-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpostproc-extra-51:
 libpostproc-extra-51 depends on libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil-extra-49 is not installed.
 libpostproc-extra-51 depends on libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil-extra-49 is not installed.
dpkg: error processing libpostproc-extra-51 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpostproc-unstripped-51:
 libpostproc-unstripped-51 depends on libpostproc-extra-51 (= 4:0.5+svn20090706-1ubuntu1+extra1); however:
  Package libpostproc-extra-51 is not configured yet.
dpkg: error processing libpostproc-unstripped-51 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libswscale-extra-0
 libswscale-unstripped-0
 libpostproc-extra-51
 libpostproc-unstripped-51
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

```

How to cure?

---

### Post by taavikko on 2009-08-25
Waiting that the ffmpeg transition is completed.
Not much you can do at the moment. It should clear in a few days.
dpkg --force isn't such a good idea.

---

### Post by ilna on 2009-08-25
Thanks! I'm not in a hurry, just was interested in because of rather long unmet deps existence.

---

### Post by kernco on 2009-08-31
I have a similar problem.

Unpacking libavutil-extra-49 (from .../libavutil-extra-49_4%3a0.5+svn20090706-2ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libavutil-extra-49_4%3a0.5+svn20090706-2ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libavutil.so.49.15.0', which is also in package libavutil-unstripped-49

Same issue?  I see this thread is 6 days old, is the transition still not complete?

---

### Post by taavikko on 2009-09-01
> **kernco said:**
> I have a similar problem.

Unpacking libavutil-extra-49 (from .../libavutil-extra-49_4%3a0.5+svn20090706-2ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libavutil-extra-49_4%3a0.5+svn20090706-2ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libavutil.so.49.15.0', which is also in package libavutil-unstripped-49

Same issue?  I see this thread is 6 days old, is the transition still not complete?

Try to install the unstripped-version instead of -extra.
```
tta@dv5:~$ dpkg -l |grep -e unstripped -e extra
ii  libavcodec-extra-52                    4:0.5+svn20090706-2ubuntu1                 ffmpeg codec library
ii  libavcodec-unstripped-52               4:0.5+svn20090706-2ubuntu1                 ffmpeg utility library - transitional packag
ii  libavutil-extra-49                     4:0.5+svn20090706-2ubuntu1                 ffmpeg utility library
```

---

### Post by daflame on 2009-09-06
> **taavikko said:**
> Try to install the unstripped-version instead of -extra.
```
tta@dv5:~$ dpkg -l |grep -e unstripped -e extra
ii  libavcodec-extra-52                    4:0.5+svn20090706-2ubuntu1                 ffmpeg codec library
ii  libavcodec-unstripped-52               4:0.5+svn20090706-2ubuntu1                 ffmpeg utility library - transitional packag
ii  libavutil-extra-49                     4:0.5+svn20090706-2ubuntu1                 ffmpeg utility library
```

This gets even more convoluted because libk3b6-extracodecs updates are broken by not supporting unstripped versions right now.  Just wait and pray.

---

### Post by taavikko on 2009-09-06
> **daflame said:**
> This gets even more convoluted because libk3b6-extracodecs updates are broken by not supporting unstripped versions right now.  Just wait and pray.

Yes, but it's been reported: [https://bugs.edge.launchpad.net/ubuntu/+source/k3b/+bug/416890](https://bugs.edge.launchpad.net/ubuntu/+source/k3b/+bug/416890)

---

