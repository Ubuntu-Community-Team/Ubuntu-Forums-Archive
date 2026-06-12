---
title: "apt hangs while unpacking"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by tompc35 on 2010-11-16
My problem is that I am unable to do a routine upgrade of packages. When I try to perform an upgrade, the following occurs:

```

$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  hotot libmysqlclient16 libplymouth2 libxml2 libxml2-utils mysql-common 
  plymouth plymouth-label plymouth-theme-ubuntu-logo 
  plymouth-theme-ubuntu-text plymouth-x11 python-libxml2 tzdata tzdata-java 
14 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4,869kB of archives. After unpacking 24.6kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... 190607 files and directories currently installed.)
Preparing to replace tzdata-java 2010m-0ubuntu0.10.04 (using .../tzdata-java_2010o-0ubuntu0.10.04_all.deb) ...
Unpacking replacement tzdata-java ...

```And then it hangs right there forever. Every time I try (using either "dist-upgrade" or "upgrade" or "-f install" arguments), the process hangs in the same place. I have tried being patient by letting it run overnight, but no luck. In order to be able to try again, I have input the following commands:

```

$ sudo rm /var/lib/dpkg/lock 
$ sudo dpkg --configure -a
$ sudo rm /var/lock/aptitude 
$ sudo aptitude update

```If I try to install another package, I get the following message:

```

...
E: I wasn't able to locate file for the tzdata-java package. This might mean you need to manually fix this package.
E: I wasn't able to locate file for the tzdata-java package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

```I have tried searching the forums, with no success. Please let me know if you have any ideas. Thank you.

---

### Post by sikander3786 on 2010-11-17
Try,

```
sudo apt-get clean
```

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo aptitude dist-upgrade
```

---

### Post by tompc35 on 2010-11-17
Thanks for the suggestion. I have tried that combination of commands, but it hangs in the same unpacking step (after getting files):

```
$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  empathy empathy-common hotot libmysqlclient16 libplymouth2 libxml2 
  libxml2-utils mysql-common nautilus-sendto-empathy plymouth 
  plymouth-label plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text 
  plymouth-x11 python-libxml2 tzdata tzdata-java xserver-common 
  xserver-xorg-core 
19 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,908kB of archives. After unpacking 164kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main tzdata-java 2010o-0ubuntu0.10.04 [144kB]
Get:2 http://ppa.launchpad.net/jimmyxu/hotot/ubuntu/ lucid/main hotot 1:0.9.5~hg538-0ubuntu0ppa1~lucid1 [430kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main tzdata 2010o-0ubuntu0.10.04 [677kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth-label 0.8.2-2ubuntu2.1 [18.0kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth-x11 0.8.2-2ubuntu2.1 [26.3kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth 0.8.2-2ubuntu2.1 [124kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libplymouth2 0.8.2-2ubuntu2.1 [101kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libxml2 2.7.6.dfsg-1ubuntu1.1 [873kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth-theme-ubuntu-text 0.8.2-2ubuntu2.1 [21.1kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main nautilus-sendto-empathy 2.30.3-0ubuntu1 [659kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main empathy 2.30.3-0ubuntu1 [1,022kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main empathy-common 2.30.3-0ubuntu1 [720kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-common 5.1.41-3ubuntu12.7 [98.6kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libmysqlclient16 5.1.41-3ubuntu12.7 [1,986kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libxml2-utils 2.7.6.dfsg-1ubuntu1.1 [92.8kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth-theme-ubuntu-logo 0.8.2-2ubuntu2.1 [34.2kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main python-libxml2 2.7.6.dfsg-1ubuntu1.1 [243kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main xserver-common 2:1.7.6-2ubuntu7.4 [83.4kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main xserver-xorg-core 2:1.7.6-2ubuntu7.4 [2,553kB]
Fetched 9,908kB in 3s (2,950kB/s)      
Preconfiguring packages ...
(Reading database ... 190607 files and directories currently installed.)
Preparing to replace tzdata-java 2010m-0ubuntu0.10.04 (using .../tzdata-java_2010o-0ubuntu0.10.04_all.deb) ...
Unpacking replacement tzdata-java ...
```

---

### Post by sikander3786 on 2010-11-17
Try to remove the offensive package.

```
dpkg -r tzdata-java
```

and then,

```
sudo dpkg --configure -a
```

Please post the output as well.

---

### Post by tompc35 on 2010-11-17
Also, I forgot to mention that the previous step ('apt-get update && sudo apt-get upgrade') ends with an error about unmet dependencies.

I tried 'apt-get -f install' but that did not work either.

```

$ sudo apt-get update && sudo apt-get upgrade
Hit http://download.virtualbox.org lucid Release.gpg
Ign http://download.virtualbox.org/virtualbox/debian/ lucid/non-free Translation-en_US
Hit http://download.virtualbox.org lucid Release                               
Hit http://download.virtualbox.org lucid/non-free Packages                     
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/effie-jayx/turpial/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ lucid/partner Translation-en_US              
Hit http://packages.medibuntu.org lucid Release.gpg                            
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                                 
Ign http://ppa.launchpad.net/jimmyxu/hotot/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://archive.canonical.com lucid Release                                 
Hit http://packages.medibuntu.org lucid Release                                
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://us.archive.ubuntu.com lucid-updates Release                         
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://packages.medibuntu.org lucid/free Packages                          
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources           
Hit http://security.ubuntu.com lucid-security/restricted Sources     
Hit http://security.ubuntu.com lucid-security/universe Packages      
Hit http://security.ubuntu.com lucid-security/universe Sources       
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Hit http://us.archive.ubuntu.com lucid/restricted Packages                     
Hit http://us.archive.ubuntu.com lucid/main Sources                  
Hit http://us.archive.ubuntu.com lucid/restricted Sources                      
Hit http://us.archive.ubuntu.com lucid/universe Packages                       
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://packages.medibuntu.org lucid/non-free Packages            
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Hit http://security.ubuntu.com lucid-security/multiverse Sources     
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.

```

---

### Post by sikander3786 on 2010-11-17
Yes that is related.

I can't see the complete output. There should be something after these lines referring to some packages.

> You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.

Is any package named there?

---

### Post by tompc35 on 2010-11-17
OK, in response to your new post...

There were dependency problems while attempting to remove the package:

```

$ sudo dpkg -r tzdata-java
dpkg: dependency problems prevent removal of tzdata-java:
 openjdk-6-jre-headless depends on tzdata-java.
dpkg: error processing tzdata-java (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 tzdata-java

```

---

### Post by tompc35 on 2010-11-17
> 
Yes that is related.

I can't see the complete output. There should be something after these lines referring to some packages.

 	Quote:
 	 	 		 			 				You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f. 			 		 	 	 
Is any package named there?


I checked, that is the entire output. The next line is a command prompt.

---

### Post by sikander3786 on 2010-11-17
Ok. Time for some manual clean up. Follow with caution, keep a close eye and your mind on what you are doing and double check before deleting any files/text as advised.

Type,

```
gksu nautilus /var/lib/dpkg/info
```

Find tzdata-java, any files relating to it and delete them or move them to some other location whatever you prefer.

Now make a backup of your dpkg status file as you are going to edit it and might need to revert back to the original in case.

```
sudo cp /var/lib/dpgk/status /var/lib/dpkg/status.bak
```

Now edit the file

```
gksu gedit /var/lib/dpkg/status
```

Search for tzdata-java and delete any lines relating to it. There might be more than one so go keep on searching until the end of the file.

Now type

```
sudo apt-get update
```

And tell me that the error message is gone. :-)

**You are doing everything as root, the system might not ask you to double check or even single check if deleting something. Be cautious or you might mess up your system.**

---

### Post by tompc35 on 2010-11-17
> Type,

     Code:
     gksu nautilus /var/lib/dpkg/info 
Find tzdata-java, any files relating to it and delete them or move them to some other location whatever you prefer.OK, moved 'tzdata-java.list' and 'tzdata-java.md5sums' away from that folder.

> Now edit the file

     Code:
     gksu gedit /var/lib/dpkg/status 
Search for tzdata-java and delete any lines relating to it. There  might be more than one so go keep on searching until the end of the  file.OK, deleted these lines:

```

Package: tzdata-java
Status: deinstall reinstreq half-installed
Priority: optional
Section: java
Installed-Size: 1916
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: tzdata
Version: 2010m-0ubuntu0.10.04
Config-Version: 2010m-0ubuntu0.10.04
Depends: tzdata (= 2010m-0ubuntu0.10.04)
Description: time zone and daylight-saving time data for use by java runtimes
 This package contains data required for the implementation of
 standard local time for many representative locations around the
 globe. It is updated periodically to reflect changes made by
 political bodies to time zone boundaries, UTC offsets, and
 daylight-saving rules.
 .
 This package contains the data for use by Java runtimes.
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>


```And also deleted 'tzdata-java' from the list of depends here (did not delete the whole section):

```

Package: openjdk-6-jre-headless
Status: install ok installed
Priority: optional
Section: java
Installed-Size: 75440
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: openjdk-6
Version: 6b18-1.8.2-4ubuntu2
Replaces: openjdk-6-jdk (<< 6b18-1.8.2-4), openjdk-6-jre (<< 6b09dfsg-0ubuntu2), openjdk-6-jre-lib (<< 6b06-0ubuntu11)
Provides: java-runtime-headless, java2-runtime-headless, java5-runtime-headless, java6-runtime-headless
Depends: openjdk-6-jre-lib (>= 6b18-1.8.2-4ubuntu2), ca-certificates-java, tzdata-java, java-common (>= 0.28), libcups2, liblcms1, libjpeg62, libnss3-1d (>= 3.12.3), libc6 (>= 2.11), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), zlib1g (>= 1:1.1.4)
Recommends: icedtea-6-jre-cacao (= 6b18-1.8.2-4ubuntu2)

```I then ran
```
sudo apt-get update
``````
sudo apt-get upgrade
```... and now the error message is gone, but the upgrade hangs while unpacking the 'tzdata' package.

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  openjdk-6-jre-headless
The following packages will be upgraded:
  empathy empathy-common hotot libmysqlclient16 libplymouth2 libxml2
  libxml2-utils mysql-common nautilus-sendto-empathy plymouth plymouth-label
  plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text plymouth-x11
  python-libxml2 tzdata xserver-common xserver-xorg-core
18 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 9,086kB/9,764kB of archives.
After this operation, 164kB of additional disk space will be used.
Do you want to continue [Y/n]?  y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth-label 0.8.2-2ubuntu2.1 [18.0kB]
Get:2 http://ppa.launchpad.net/jimmyxu/hotot/ubuntu/ lucid/main hotot 1:0.9.5~hg538-0ubuntu0ppa1~lucid1 [430kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth-x11 0.8.2-2ubuntu2.1 [26.3kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth 0.8.2-2ubuntu2.1 [124kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libplymouth2 0.8.2-2ubuntu2.1 [101kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libxml2 2.7.6.dfsg-1ubuntu1.1 [873kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth-theme-ubuntu-text 0.8.2-2ubuntu2.1 [21.1kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main nautilus-sendto-empathy 2.30.3-0ubuntu1 [659kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main empathy 2.30.3-0ubuntu1 [1,022kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main empathy-common 2.30.3-0ubuntu1 [720kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-common 5.1.41-3ubuntu12.7 [98.6kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libmysqlclient16 5.1.41-3ubuntu12.7 [1,986kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libxml2-utils 2.7.6.dfsg-1ubuntu1.1 [92.8kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth-theme-ubuntu-logo 0.8.2-2ubuntu2.1 [34.2kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main python-libxml2 2.7.6.dfsg-1ubuntu1.1 [243kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main xserver-common 2:1.7.6-2ubuntu7.4 [83.4kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main xserver-xorg-core 2:1.7.6-2ubuntu7.4 [2,553kB]
Fetched 9,086kB in 3s (2,646kB/s)       
Preconfiguring packages ...
(Reading database ... 190140 files and directories currently installed.)
Preparing to replace tzdata 2010m-0ubuntu0.10.04 (using .../tzdata_2010o-0ubuntu0.10.04_all.deb) ...
Unpacking replacement tzdata ...

```Maybe I should repeat the above steps with tzdata? Or maybe there is a deeper problem related to unpacking?

---

### Post by sikander3786 on 2010-11-17
It shouldn't go this way...

Repeat the steps for tzdata as well.

---

### Post by tompc35 on 2010-11-17
Same problem. Definitely seems like something is wrong with the unpacking step, not the packages themselves. 

```

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libc6 libical0 openjdk-6-jre-headless python-dateutil python-tz
  ubuntu-minimal util-linux
The following packages will be upgraded:
  empathy empathy-common hotot libmysqlclient16 libplymouth2 libxml2
  libxml2-utils mysql-common nautilus-sendto-empathy plymouth plymouth-label
  plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text plymouth-x11
  python-libxml2 xserver-common xserver-xorg-core
17 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 9,086kB of archives.
After this operation, 164kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth-label 0.8.2-2ubuntu2.1 [18.0kB]
Get:2 http://ppa.launchpad.net/jimmyxu/hotot/ubuntu/ lucid/main hotot 1:0.9.5~hg538-0ubuntu0ppa1~lucid1 [430kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth-x11 0.8.2-2ubuntu2.1 [26.3kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth 0.8.2-2ubuntu2.1 [124kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libplymouth2 0.8.2-2ubuntu2.1 [101kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libxml2 2.7.6.dfsg-1ubuntu1.1 [873kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth-theme-ubuntu-text 0.8.2-2ubuntu2.1 [21.1kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main nautilus-sendto-empathy 2.30.3-0ubuntu1 [659kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main empathy 2.30.3-0ubuntu1 [1,022kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main empathy-common 2.30.3-0ubuntu1 [720kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-common 5.1.41-3ubuntu12.7 [98.6kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libmysqlclient16 5.1.41-3ubuntu12.7 [1,986kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libxml2-utils 2.7.6.dfsg-1ubuntu1.1 [92.8kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main plymouth-theme-ubuntu-logo 0.8.2-2ubuntu2.1 [34.2kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main python-libxml2 2.7.6.dfsg-1ubuntu1.1 [243kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main xserver-common 2:1.7.6-2ubuntu7.4 [83.4kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main xserver-xorg-core 2:1.7.6-2ubuntu7.4 [2,553kB]
Fetched 9,086kB in 3s (2,342kB/s)       
(Reading database ... 188301 files and directories currently installed.)
Preparing to replace plymouth-label 0.8.2-2ubuntu2 (using .../plymouth-label_0.8.2-2ubuntu2.1_amd64.deb) ...
Unpacking replacement plymouth-label ...

```

---

### Post by sikander3786 on 2010-11-17
Yes sounds like...

Is there enough free space on the partition?

```
df -h
```

---

### Post by tompc35 on 2010-11-17
Yes GB's of space on all partitions.

However, I did some more research and found this reported (and unfixed) bug:

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/624229](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/624229)

People there report similar problems when unpacking replacement packages, possibly related to external USB hard drives. I do have an external hard drive, and I am running a model that uses data on that hard drive. So when the model run finishes, I will try to see if my hard drive is causing the problem, then I will report the results back here. I am not doing anything out of the ordinary, so I am not sure why this problem would come up all of a sudden.

Thanks again for all your help, sikander3786

---

### Post by MightyMag on 2010-12-23
I'm having the exact same problem. Ubuntu 10.10 64-bit, clean install. Random stuff just hangs during unpacking process in apt. Reboot is the only thing that helps.

---

### Post by sikander3786 on 2010-12-24
> **MightyMag said:**
> I'm having the exact same problem. Ubuntu 10.10 64-bit, clean install. Random stuff just hangs during unpacking process in apt. Reboot is the only thing that helps.
Please post the output of these commands.

```
sudo apt-get clean
```

```
sudo apt-get update && sudo apt-get upgrade
```

```
df -h
```

---

### Post by Ikka3990 on 2010-12-25
I have been having the same problems after a kernel upgrade. Things seem to work fine for older kernels (up to 2.6.35-22). For now, I hope you can manage by logging into one of your older kernels during boot time.

---

### Post by niki+a on 2011-01-02
Started this post on what seems like the same problem here:

[http://ubuntuforums.org/showthread.php?p=10309719&posted=1#post10309719](http://ubuntuforums.org/showthread.php?p=10309719&posted=1#post10309719)

tried everything:

sudo dpkg --configure -a

sudo rm /var/cache/apt/archives/lock

sudo rm <other locks>

sudo apt-get clean

sudo apt-get update && sudo apt-get upgrade

sudo dpkg --remove --force-remove-reinstreq <package name>

then same steps... it clears apt history, but the problem is always the same, apt just hangs...

```

nikita@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             29G   17G   11G  61% /
none                  2.0G  380K  2.0G   1% /dev
none                  2.0G  4.8M  2.0G   1% /dev/shm
none                  2.0G  312K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda6              32G   31G  1.2G  97% /host
none                   29G   17G   11G  61% /var/lib/ureadahead/debugfs
/dev/sdc1             1.9T  505G  1.4T  28% /media/Elements
/dev/sda5             154G   80G   74G  52% /media/DATA
/dev/sda2              75G   42G   33G  56% /media/OS
/dev/sda7              25G  173M   23G   1% /media/home


```

Is it the fact that /dev/sda6 only has 1.2 G left? Should be plenty though, the programs I am trying to install hardly exceed 1 mb...

---

### Post by niki+a on 2011-01-02
I restarted my computer and everything worked fine.

```
sudo aptitude install <package name>
```

Worked like a charm. Note, I used:

```

sudo dpkg --configure -a

sudo rm /var/cache/apt/archives/lock

sudo rm <other locks>

sudo apt-get clean

sudo apt-get update && sudo apt-get upgrade

sudo dpkg --remove --force-remove-reinstreq <package name>

```

to do manual clean up. I think it can be considered clean when you run:

```

sudo apt-get update && sudo apt-get upgrade

```

and get no weirdness. 

Heh, Linux, as much as I love you, not quite there yet.

---

### Post by jpmeijers on 2011-01-05
I have the same problem with a fully updated Ubuntu 10.10 32bit. As was already mentioned, I only got this problem after I started using a external that is semi-permanently plugged in. The is enough space left on all partitions.

---

### Post by efd on 2011-01-11
I have this same problem.  Apparently this is a bug in dpkg, which apt calls to update the system.  dpkg does a filesystem sync after each and every file it unpacks to maximize safety, but if other i/o is happening on the system especially with large external drives, dpkg will hang as sync() syncs the entire filesystem and not just the file it's unpacking.  It's really really stupid and a lot of people are ticked about it because it doesn't actually make dpkg any safer.

Here's the Launchpad bug report.

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/624229](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/624229)

Basically, if you're using an external USB drive or doing any other i/o, stop/unmount it before running apt.

---

### Post by niki+a on 2011-02-17
> **efd said:**
> I have this same problem.  Apparently this is a bug in dpkg, which apt calls to update the system.  dpkg does a filesystem sync after each and every file it unpacks to maximize safety, but if other i/o is happening on the system especially with large external drives, dpkg will hang as sync() syncs the entire filesystem and not just the file it's unpacking.  It's really really stupid and a lot of people are ticked about it because it doesn't actually make dpkg any safer.

Here's the Launchpad bug report.

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/624229](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/624229)

Basically, if you're using an external USB drive or doing any other i/o, stop/unmount it before running apt.

 Thank you.

---

### Post by skralljt on 2011-02-22
I don't have an external drive.  Doesn't help me at all.  Wish I had stuck with my old ubuntu installation, which I've been upgrading from 6. something.  Full of useless config files and links pointing to nowhere but it worked fairly well.

---

### Post by mister_playboy on 2011-04-05
> **efd said:**
> I have this same problem.  Apparently this is a bug in dpkg, which apt calls to update the system.  dpkg does a filesystem sync after each and every file it unpacks to maximize safety, but if other i/o is happening on the system especially with large external drives, dpkg will hang as sync() syncs the entire filesystem and not just the file it's unpacking.  It's really really stupid and a lot of people are ticked about it because it doesn't actually make dpkg any safer.

Here's the Launchpad bug report.

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/624229](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/624229)

Basically, if you're using an external USB drive or doing any other i/o, stop/unmount it before running apt.

Thanks for this information.  After rebooting with the external HDDs disconnected, I was able to follow the other steps to fix dpkg successfully and now I can update again. :guitar:

---

### Post by smrtbeenr on 2011-04-06
I'm just doing a clean install using the 10.04 dvd and a totally blank internal HDD.  It just hangs there saying "running dpkg"  wtf, mate?

---

### Post by hzFVOW00pw on 2011-09-10
Same problem here. I was experiencing this problem while running a rsnapshot backup to an external USB hdd. After the backup I unmounted the hdd and run various commands from a terminal:

```
sudo -i
```

```
rm -f /var/cache/apt/archives/lock /var/lib/apt/lists/lock /var/lib/dpkg/lock /var/lib/dpkg/info/packagename*
```

And edited /var/lib/dpkg/status to remove the entry of <packagename>

```
apt-get clean
```
```
dpkg --configure -a
```
```
dpkg --remove --force-remove-reinstreq packagename
```
```
apt-get install packagename
```

This worked for me. I did not have to reboot or disconnect the external disk, only unmount it.

---

### Post by Ctulhu on 2011-12-20
I am suffering from a very similar problem: I installed a clean Kubuntu 11.10 64bit on a Dell Latitude E6500. Rebooted after install, ran the update manager Muon first thing, said apply all upgrades, and then at 57% ("Running dpkg") the progress bar freezes and that's it. No external drive attached, plenty of space on the hard drive, and this is the third clean install attempt. (On that same computer, Ubuntu 11.10 and Mint 11 worked just fine). Any ideas? I can't believe it's nearly 2012 and one can't just install Kubuntu on a decent but not bleeding-edge Dell notebook ...

---

### Post by ambrosa on 2011-12-23
> **Ctulhu said:**
> I am suffering from a very similar problem: I installed a clean Kubuntu 11.10 64bit on a Dell Latitude E6500. Rebooted after install, ran the update manager Muon first thing, said apply all upgrades, and then at 57% ("Running dpkg") the progress bar freezes and that's it. No external drive attached, plenty of space on the hard drive, and this is the third clean install attempt. (On that same computer, Ubuntu 11.10 and Mint 11 worked just fine). Any ideas? I can't believe it's nearly 2012 and one can't just install Kubuntu on a decent but not bleeding-edge Dell notebook ...

THE SAME !!
Today I started to install for the first time Kubuntu 11.10 64bit (I used for years Ubuntu) in my desktop system: Intel Core 2 Duo E6600, 6 GB RAM, Nvidia 9600GT. In this system run fine Ubuntu 64bit (since 09.x), Linux Mint, Fedora, Windows XP and Win7 64bit

After installation, the first thing I did was run Muon to upgrade system.
Muon run to 57% and then stop say "dpkg"
KDE Menù icons disappeared so I cannot start any sw (i.e. terminal).

After 30 minutes of total inactivity, I can only power-off the system.
I've retried a second time with the same result.

Terrible wrong !!!!

---

### Post by ambrosa on 2011-12-23
I've reinstalled for the third time Kubuntu 11.10 64bit
After the first login I DON'T run Muon. I open a terminal window and I run:

sudo apt-update
sudo apt-upgrade
well, downloaded and installed fine 293 packages

Then reboot, and again:
sudo apt-get dist-upgrade (to upgrade from kernel 3.0.0-12 to 3.0.0-14)

Reboot again and installed Nvidia current driver (280.13)

Kubuntu works fine.


I think that the problem above is a Muon bug.

---

### Post by Ctulhu on 2011-12-23
Agreed, I think it's a Muon bug as well: I installed Synaptic Package Manager to do all the updates and had no problems with that.

---

