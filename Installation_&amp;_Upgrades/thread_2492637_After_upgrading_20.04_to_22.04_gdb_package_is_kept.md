---
title: "After upgrading 20.04 to 22.04 gdb package is kept back"
date: 2023-11-18
forum: Installation &amp; Upgrades
---

### Post by Chanester on 2023-11-18
I have just upgraded from 20.04 to 22.04 and (nearly) everything has gone OK, except for one package -gdb- that won't upgrade:

```

c@d:~$ sudo apt update
Hit:1 http://gb.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://security.ubuntu.com/ubuntu jammy-security InRelease                                                                   
Hit:3 http://gb.archive.ubuntu.com/ubuntu jammy-updates InRelease                                                                  
Hit:4 http://ppa.launchpad.net/helkaluin/webp-pixbuf-loader/ubuntu jammy InRelease                                                 
Hit:5 http://gb.archive.ubuntu.com/ubuntu jammy-backports InRelease                                                                
Hit:6 http://ppa.launchpad.net/jonaski/strawberry/ubuntu jammy InRelease                                                           
Hit:7 http://ppa.launchpad.net/libretro/stable/ubuntu jammy InRelease                                                       
Hit:8 http://ppa.launchpad.net/lutris-team/lutris/ubuntu focal InRelease                                                    
Hit:9 http://ppa.launchpad.net/musicbrainz-developers/stable/ubuntu jammy InRelease                                        
Hit:10 http://ppa.launchpad.net/obsproject/obs-studio/ubuntu jammy InRelease                                               
Hit:11 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu jammy InRelease                                             
Hit:12 http://ppa.launchpad.net/savoury1/dbgl/ubuntu jammy InRelease                                 
Hit:13 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu jammy InRelease                                 
Ign:14 https://www.scootersoftware.com bcompare4 InRelease                                          
Hit:15 https://www.scootersoftware.com bcompare4 Release
Hit:16 https://deb.opera.com/opera-stable stable InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.


c@d:~$ apt list --upgradable
Listing... Done
gdb/jammy-updates 12.1-0ubuntu1~22.04 amd64 [upgradable from: 9.2-0ubuntu1~20.04.1]
N: There are 2 additional versions. Please use the '-a' switch to see them.
c@d:~$ apt list --upgradable -a
Listing... Done
gdb/jammy-updates 12.1-0ubuntu1~22.04 amd64 [upgradable from: 9.2-0ubuntu1~20.04.1]
gdb/jammy 12.0.90-0ubuntu1 amd64
gdb/now 9.2-0ubuntu1~20.04.1 amd64 [installed,upgradable to: 12.1-0ubuntu1~22.04]
c@d:~$ sudo apt upgrade gdb
[sudo] password for c: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 libdebuginfod1 : Depends: libelf1 (= 0.186-1build1) but 0.189.46.g27a84961f7a0+20.04.20230811182447 is to be installed
                  Depends: libdw1 (= 0.186-1build1) but 0.189.46.g27a84961f7a0+20.04.20230811182447 is to be installed
                  Depends: libdebuginfod-common (>= 0.186-1build1) but it is not going to be installed
E: Broken packages

```


I've tried my usual tricks such as using aptitude:

```
c@d:~$ sudo aptitude upgrade gdb
Resolving dependencies...                
The following packages have been kept back:
  gdb 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

```
Not sure what to do / try next, any pointers appreciated.

---

### Post by ian-weisser on 2023-11-18
Please show us the complete output of "apt policy gdb"

---

### Post by Chanester on 2023-11-19
Here you go-

```

c@d:~$ apt policy gdb
gdb:
  Installed: 9.2-0ubuntu1~20.04.1
  Candidate: 12.1-0ubuntu1~22.04
  Version table:
     12.1-0ubuntu1~22.04 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages
     12.0.90-0ubuntu1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
 *** 9.2-0ubuntu1~20.04.1 100
        100 /var/lib/dpkg/status

```

---

