---
title: "local mirror is available, but packages can't be found."
date: 2018-09-23
forum: Installation &amp; Upgrades
---

### Post by timothylegg on 2018-09-23
Hello,

I am preparing to install Ubuntu Desktop (AMD64) 16.04.4 onto a machine that lacks the conveniences of fast internet (data is modem speed)

I have a machine running Ubuntu Desktop 16.04 (AMD64) and have installed apt-mirror.

I have run the apt-mirror script and it created a huge directory tree across a couple hours.

I have installed nginx (I usually do Apache, but looked for an excuse to try something different), and I verified the paths are accessible to a web browser.

Satisfied with these successes, I decided to test it by modifying my /etc/apt/sources.list to localhost instead of the default domain name. I ran apt-get update and it mostly ran fine, but had a few 404 errors that I disregarded:

From apt-get update:
```

Get:1 http://localhost/ubuntu xenial InRelease [247 kB]
Get:2 http://localhost/ubuntu xenial-updates InRelease [109 kB]
Get:3 http://localhost/ubuntu xenial-backports InRelease [107 kB]
Get:4 http://localhost/ubuntu xenial-security InRelease [107 kB]
Ign:5 http://localhost/ubuntu xenial/main amd64 Packages     
Ign:6 http://localhost/ubuntu xenial/main i386 Packages
Ign:7 http://localhost/ubuntu xenial/main Translation-en
Ign:8 http://localhost/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:9 http://localhost/ubuntu xenial/main DEP-11 64x64 Icons
Ign:10 http://localhost/ubuntu xenial/restricted amd64 Packages
Ign:11 http://localhost/ubuntu xenial/restricted i386 Packages
Ign:12 http://localhost/ubuntu xenial/restricted Translation-en
Ign:13 http://localhost/ubuntu xenial/restricted amd64 DEP-11 Metadata
Ign:14 http://localhost/ubuntu xenial/universe amd64 Packages
Ign:15 http://localhost/ubuntu xenial/universe i386 Packages
Ign:16 http://localhost/ubuntu xenial/universe Translation-en
Ign:17 http://localhost/ubuntu xenial/universe amd64 DEP-11 Metadata
Ign:18 http://localhost/ubuntu xenial/universe DEP-11 64x64 Icons
Ign:19 http://localhost/ubuntu xenial/multiverse amd64 Packages
Ign:20 http://localhost/ubuntu xenial/multiverse i386 Packages
Ign:21 http://localhost/ubuntu xenial/multiverse Translation-en
Ign:22 http://localhost/ubuntu xenial/multiverse amd64 DEP-11 Metadata
Ign:23 http://localhost/ubuntu xenial/multiverse DEP-11 64x64 Icons
Get:5 http://localhost/ubuntu xenial/main amd64 Packages [1,201 kB]
Ign:6 http://localhost/ubuntu xenial/main i386 Packages         
Get:7 http://localhost/ubuntu xenial/main Translation-en [568 kB]        
Get:8 http://localhost/ubuntu xenial/main amd64 DEP-11 Metadata [733 kB] 
Get:9 http://localhost/ubuntu xenial/main DEP-11 64x64 Icons [409 kB]          
Get:10 http://localhost/ubuntu xenial/restricted amd64 Packages [8,344 B]      
Ign:11 http://localhost/ubuntu xenial/restricted i386 Packages                 
Get:12 http://localhost/ubuntu xenial/restricted Translation-en [2,908 B]
Get:13 http://localhost/ubuntu xenial/restricted amd64 DEP-11 Metadata [186 B] 
Get:14 http://localhost/ubuntu xenial/universe amd64 Packages [7,532 kB]       
Ign:15 http://localhost/ubuntu xenial/universe i386 Packages         
Get:16 http://localhost/ubuntu xenial/universe Translation-en [4,354 kB]
Get:17 http://localhost/ubuntu xenial/universe amd64 DEP-11 Metadata [3,410 kB]
Get:18 http://localhost/ubuntu xenial/universe DEP-11 64x64 Icons [7,448 kB]
Get:19 http://localhost/ubuntu xenial/multiverse amd64 Packages [144 kB]
Ign:20 http://localhost/ubuntu xenial/multiverse i386 Packages  
Get:21 http://localhost/ubuntu xenial/multiverse Translation-en [106 kB]
Get:22 http://localhost/ubuntu xenial/multiverse amd64 DEP-11 Metadata [63.8 kB]
Get:23 http://localhost/ubuntu xenial/multiverse DEP-11 64x64 Icons [230 kB]
Ign:6 http://localhost/ubuntu xenial/main i386 Packages            
Ign:24 http://localhost/ubuntu xenial-updates/main amd64 Packages
Ign:25 http://localhost/ubuntu xenial-updates/main i386 Packages
Ign:26 http://localhost/ubuntu xenial-updates/main Translation-en
Ign:27 http://localhost/ubuntu xenial-updates/main amd64 DEP-11 Metadata
Ign:28 http://localhost/ubuntu xenial-updates/main DEP-11 64x64 Icons
Ign:29 http://localhost/ubuntu xenial-updates/restricted amd64 Packages
Ign:30 http://localhost/ubuntu xenial-updates/restricted i386 Packages
Ign:31 http://localhost/ubuntu xenial-updates/restricted Translation-en
Ign:32 http://localhost/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata
Ign:33 http://localhost/ubuntu xenial-updates/universe amd64 Packages
Ign:34 http://localhost/ubuntu xenial-updates/universe i386 Packages
Ign:35 http://localhost/ubuntu xenial-updates/universe Translation-en
Ign:36 http://localhost/ubuntu xenial-updates/universe amd64 DEP-11 Metadata
Ign:37 http://localhost/ubuntu xenial-updates/universe DEP-11 64x64 Icons
Ign:38 http://localhost/ubuntu xenial-updates/multiverse amd64 Packages
Ign:39 http://localhost/ubuntu xenial-updates/multiverse i386 Packages
Ign:40 http://localhost/ubuntu xenial-updates/multiverse Translation-en
Ign:41 http://localhost/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata
Ign:42 http://localhost/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons
Ign:11 http://localhost/ubuntu xenial/restricted i386 Packages
Ign:43 http://localhost/ubuntu xenial-backports/main amd64 Packages
Ign:44 http://localhost/ubuntu xenial-backports/main i386 Packages
Ign:45 http://localhost/ubuntu xenial-backports/main Translation-en
Ign:46 http://localhost/ubuntu xenial-backports/main amd64 DEP-11 Metadata
Ign:47 http://localhost/ubuntu xenial-backports/main DEP-11 64x64 Icons
Ign:48 http://localhost/ubuntu xenial-backports/restricted amd64 DEP-11 Metadata
Ign:49 http://localhost/ubuntu xenial-backports/universe amd64 Packages
Ign:50 http://localhost/ubuntu xenial-backports/universe i386 Packages
Ign:51 http://localhost/ubuntu xenial-backports/universe Translation-en
Ign:52 http://localhost/ubuntu xenial-backports/universe amd64 DEP-11 Metadata
Ign:53 http://localhost/ubuntu xenial-backports/universe DEP-11 64x64 Icons
Ign:54 http://localhost/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata
Ign:55 http://localhost/ubuntu xenial-backports/multiverse DEP-11 64x64 Icons
Ign:56 http://localhost/ubuntu xenial-security/main amd64 Packages
Ign:57 http://localhost/ubuntu xenial-security/main i386 Packages
Ign:58 http://localhost/ubuntu xenial-security/main Translation-en
Ign:59 http://localhost/ubuntu xenial-security/main amd64 DEP-11 Metadata
Ign:60 http://localhost/ubuntu xenial-security/main DEP-11 64x64 Icons
Ign:61 http://localhost/ubuntu xenial-security/restricted amd64 Packages
Ign:62 http://localhost/ubuntu xenial-security/restricted i386 Packages
Ign:63 http://localhost/ubuntu xenial-security/restricted Translation-en
Ign:64 http://localhost/ubuntu xenial-security/restricted amd64 DEP-11 Metadata
Ign:65 http://localhost/ubuntu xenial-security/universe amd64 Packages
Ign:66 http://localhost/ubuntu xenial-security/universe i386 Packages
Ign:67 http://localhost/ubuntu xenial-security/universe Translation-en
Ign:68 http://localhost/ubuntu xenial-security/universe amd64 DEP-11 Metadata
Ign:69 http://localhost/ubuntu xenial-security/universe DEP-11 64x64 Icons
Ign:70 http://localhost/ubuntu xenial-security/multiverse amd64 Packages
Ign:71 http://localhost/ubuntu xenial-security/multiverse i386 Packages
Ign:72 http://localhost/ubuntu xenial-security/multiverse Translation-en
Ign:73 http://localhost/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata
Ign:74 http://localhost/ubuntu xenial-security/multiverse DEP-11 64x64 Icons
Ign:15 http://localhost/ubuntu xenial/universe i386 Packages
Ign:20 http://localhost/ubuntu xenial/multiverse i386 Packages
Err:6 http://localhost/ubuntu xenial/main i386 Packages
  404  Not Found
Get:24 http://localhost/ubuntu xenial-updates/main amd64 Packages [849 kB]
Ign:25 http://localhost/ubuntu xenial-updates/main i386 Packages
Get:26 http://localhost/ubuntu xenial-updates/main Translation-en [347 kB]
Ign:27 http://localhost/ubuntu xenial-updates/main amd64 DEP-11 Metadata
Get:28 http://localhost/ubuntu xenial-updates/main DEP-11 64x64 Icons [227 kB]
Get:29 http://localhost/ubuntu xenial-updates/restricted amd64 Packages [7,556 B]
Ign:30 http://localhost/ubuntu xenial-updates/restricted i386 Packages
Get:31 http://localhost/ubuntu xenial-updates/restricted Translation-en [2,272 B]
Get:32 http://localhost/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata [157 B]
Get:33 http://localhost/ubuntu xenial-updates/universe amd64 Packages [690 kB]
Ign:34 http://localhost/ubuntu xenial-updates/universe i386 Packages
Get:35 http://localhost/ubuntu xenial-updates/universe Translation-en [279 kB]
Ign:36 http://localhost/ubuntu xenial-updates/universe amd64 DEP-11 Metadata
Get:37 http://localhost/ubuntu xenial-updates/universe DEP-11 64x64 Icons [339 kB]
Get:38 http://localhost/ubuntu xenial-updates/multiverse amd64 Packages [16.4 kB]
Ign:39 http://localhost/ubuntu xenial-updates/multiverse i386 Packages
Get:40 http://localhost/ubuntu xenial-updates/multiverse Translation-en [8,344 B]
Ign:41 http://localhost/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata
Get:42 http://localhost/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons [14.3 kB]
Get:43 http://localhost/ubuntu xenial-backports/main amd64 Packages [6,756 B]
Ign:44 http://localhost/ubuntu xenial-backports/main i386 Packages
Get:45 http://localhost/ubuntu xenial-backports/main Translation-en [4,180 B]
Ign:46 http://localhost/ubuntu xenial-backports/main amd64 DEP-11 Metadata
Get:47 http://localhost/ubuntu xenial-backports/main DEP-11 64x64 Icons [29 B]
Get:48 http://localhost/ubuntu xenial-backports/restricted amd64 DEP-11 Metadata [194 B]
Get:49 http://localhost/ubuntu xenial-backports/universe amd64 Packages [7,568 B]
Ign:50 http://localhost/ubuntu xenial-backports/universe i386 Packages
Get:51 http://localhost/ubuntu xenial-backports/universe Translation-en [4,048 B]
Ign:52 http://localhost/ubuntu xenial-backports/universe amd64 DEP-11 Metadata
Get:53 http://localhost/ubuntu xenial-backports/universe DEP-11 64x64 Icons [1,789 B]
Ign:54 http://localhost/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata
Get:55 http://localhost/ubuntu xenial-backports/multiverse DEP-11 64x64 Icons [29 B]
Get:56 http://localhost/ubuntu xenial-security/main amd64 Packages [556 kB]
Ign:57 http://localhost/ubuntu xenial-security/main i386 Packages
Get:58 http://localhost/ubuntu xenial-security/main Translation-en [235 kB]
Ign:59 http://localhost/ubuntu xenial-security/main amd64 DEP-11 Metadata
Get:60 http://localhost/ubuntu xenial-security/main DEP-11 64x64 Icons [72.2 kB]
Get:61 http://localhost/ubuntu xenial-security/restricted amd64 Packages [7,204 B]
Ign:62 http://localhost/ubuntu xenial-security/restricted i386 Packages
Get:63 http://localhost/ubuntu xenial-security/restricted Translation-en [2,152 B]
Get:64 http://localhost/ubuntu xenial-security/restricted amd64 DEP-11 Metadata [200 B]
Get:65 http://localhost/ubuntu xenial-security/universe amd64 Packages [379 kB]
Ign:66 http://localhost/ubuntu xenial-security/universe i386 Packages
Get:67 http://localhost/ubuntu xenial-security/universe Translation-en [144 kB]
Ign:68 http://localhost/ubuntu xenial-security/universe amd64 DEP-11 Metadata
Get:69 http://localhost/ubuntu xenial-security/universe DEP-11 64x64 Icons [150 kB]
Get:70 http://localhost/ubuntu xenial-security/multiverse amd64 Packages [3,460 B]
Ign:71 http://localhost/ubuntu xenial-security/multiverse i386 Packages
Get:72 http://localhost/ubuntu xenial-security/multiverse Translation-en [1,744 B]
Ign:73 http://localhost/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata
Get:74 http://localhost/ubuntu xenial-security/multiverse DEP-11 64x64 Icons [29 B]
Ign:25 http://localhost/ubuntu xenial-updates/main i386 Packages
Get:27 http://localhost/ubuntu xenial-updates/main amd64 DEP-11 Metadata [502 kB]
Ign:30 http://localhost/ubuntu xenial-updates/restricted i386 Packages  
Ign:34 http://localhost/ubuntu xenial-updates/universe i386 Packages
Get:36 http://localhost/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [338 kB]
Ign:39 http://localhost/ubuntu xenial-updates/multiverse i386 Packages  
Get:41 http://localhost/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [6,397 B]
Ign:44 http://localhost/ubuntu xenial-backports/main i386 Packages        
Get:46 http://localhost/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,487 B]
Ign:50 http://localhost/ubuntu xenial-backports/universe i386 Packages
Get:52 http://localhost/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [5,373 B]
Get:54 http://localhost/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata [163 B]
Ign:57 http://localhost/ubuntu xenial-security/main i386 Packages         
Get:59 http://localhost/ubuntu xenial-security/main amd64 DEP-11 Metadata [91.2 kB]
Ign:62 http://localhost/ubuntu xenial-security/restricted i386 Packages   
Ign:66 http://localhost/ubuntu xenial-security/universe i386 Packages
Get:68 http://localhost/ubuntu xenial-security/universe amd64 DEP-11 Metadata [136 kB]
Ign:71 http://localhost/ubuntu xenial-security/multiverse i386 Packages
Get:73 http://localhost/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [158 B]
Err:25 http://localhost/ubuntu xenial-updates/main i386 Packages      
  404  Not Found
Ign:30 http://localhost/ubuntu xenial-updates/restricted i386 Packages
Ign:34 http://localhost/ubuntu xenial-updates/universe i386 Packages
Ign:39 http://localhost/ubuntu xenial-updates/multiverse i386 Packages
Err:44 http://localhost/ubuntu xenial-backports/main i386 Packages
  404  Not Found
Ign:50 http://localhost/ubuntu xenial-backports/universe i386 Packages
Err:57 http://localhost/ubuntu xenial-security/main i386 Packages
  404  Not Found
Ign:62 http://localhost/ubuntu xenial-security/restricted i386 Packages
Ign:66 http://localhost/ubuntu xenial-security/universe i386 Packages
Ign:71 http://localhost/ubuntu xenial-security/multiverse i386 Packages
Fetched 5,761 kB in 7s (730 kB/s)                                              
Reading package lists... Done
E: Failed to fetch http://localhost/ubuntu/dists/xenial/main/binary-i386/Packages  404  Not Found
E: Failed to fetch http://localhost/ubuntu/dists/xenial-updates/main/binary-i386/Packages  404  Not Found
E: Failed to fetch http://localhost/ubuntu/dists/xenial-backports/main/binary-i386/Packages  404  Not Found
E: Failed to fetch http://localhost/ubuntu/dists/xenial-security/main/binary-i386/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

But when I tested by installing a utility that I haven't installed yet, it wasn't found.

```

# apt-get install bmon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bmon

```

When I refresh the sources.list to the default domain name and update, it is able to find the package and I'm prompted to confirm installation.  So it leads me that the mirror.list file has something wrong, but I don't know what I'm missing.

```

############# config ##################
#
 set base_path    /var/spool/apt-mirror
#
 set mirror_path  $base_path/mirror
 set skel_path    $base_path/skel
 set var_path     $base_path/var
 set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads     20
set _tilde 0
#
############# end config ##############

deb http://archive.ubuntu.com/ubuntu xenial main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-proposed main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse

deb-src http://archive.ubuntu.com/ubuntu xenial main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse

clean http://archive.ubuntu.com/ubuntu

```

Just for completeness, here is my sources.list, even though it behaves correctly.

```

#deb cdrom:[Ubuntu 16.04.3 LTS _Xenial Xerus_ - Release amd64 (20170801)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

```

What is even more odd, is that the 'package' bmon doesn't seem in exist in reality.  It instead installs libconfuse-common and libconfuse0.  

I seek these out if both [http://localhost/ubuntu/pool/main/libc/](http://localhost/ubuntu/pool/main/libc/) and [http://us.archive.ubuntu.com/ubuntu/pool/main/libc/](http://us.archive.ubuntu.com/ubuntu/pool/main/libc/) and can't find this package either place, but I noticed that us.archive.ubuntu.com has files/directories present that don't exist on my mirror.  For example, my mirror does not have libcue but the archive.ubuntu.com does have libcue.  (Despite the /etc/apt/mirror.list using archive.ubuntu.com and /etc/apt/sources.list using us.archive.ubuntu.com, my comparison of the /ubuntu/pool/main/libc path in each location appeared identical.)

So what on earth is going on?  What does apt-mirror need from me to REALLY make a mirror, not a partial mirror?  I have limited time available to install Ubuntu on this remote machine and really need to make certain I can install it correctly the first time.

---

### Post by timothylegg on 2018-09-23
Bumping to top of page

---

### Post by timothylegg on 2018-09-28
A similar thread coincidentally posted near the same time as mine suggested a his problem was solved with this link:

[https://askubuntu.com/questions/771547/ubuntu-16-04-apt-get-update-doesnt-work-with-local-repository](https://askubuntu.com/questions/771547/ubuntu-16-04-apt-get-update-doesnt-work-with-local-repository)

As an experiment, I moved 50appstream outside /etc/ but that made no difference.  apt-get still can't find the package I wish to install.

Does anybody have any ideas?  I hope for help here...

---

### Post by wildmanne39 on 2018-09-28
Can you download 16.04 from another machine add create a bootable usb flash drive, then backup your important data and do a clean install? that would be the quickest and simplest way to go in my opinion.

---

### Post by deadflowr on 2018-09-28
Did you ever get around to fixing those 404 errors?
This askubuntu thread has a(mostly) similar problem:
[https://askubuntu.com/questions/898607/ubuntu-16-04-local-mirror-cannot-be-used-for-local-updates]("https://askubuntu.com/questions/898607/ubuntu-16-04-local-mirror-cannot-be-used-for-local-updates")

---

