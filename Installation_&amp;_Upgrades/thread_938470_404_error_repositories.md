---
title: "404 error repositories"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by NewNerd99 on 2008-10-04
Whenever I use the sudo apt get cmd I always encounter a 404/ E: error.

I am behind a proxy however synaptics package manager and add/remove programs are working.

I ran the aptitude cmd and got a window I'm not familiar with,upgradeable packages, installed packages, not installed packages, virtual packages etc.

Any help or directions on using aptitude cmd would be appreciated.

WARNING: The following packages cannot be authenticated!
  gcc-3.3-base libstdc++5
Install these packages without verification [y/N]? y
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe gcc-3.3-base 1:3.3.6-15ubuntu6
  404 Not Found [IP: 91.189.88.31 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe libstdc++5 1:3.3.6-15ubuntu6
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/gcc-3.3-base_3.3.6-15ubuntu6_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/gcc-3.3-base_3.3.6-15ubuntu6_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu6_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu6_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
chris@chris-laptop:~$

---

### Post by Sef on 2008-10-05
What version of Ubuntu are you using?

---

### Post by NewNerd99 on 2008-10-05
Apologies.
 8.04 and title amended

---

### Post by NewNerd99 on 2008-10-08
While trying to get my Broadcom wireless card working a post instructed me to download:
sudo apt-get install build-essential

This is what I get on the terminal

chris@chris-laptop:~$      sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 libstdc++6-4.2-dev libtimedate-perl patch
Suggested packages:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  libstdc++6-4.2-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.2 libstdc++6-4.2-dev libtimedate-perl
  patch
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 4664kB of archives.
After this operation, 17.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libstdc++6-4.2-dev g++-4.2 g++ libtimedate-perl patch dpkg-dev
  build-essential
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main libstdc++6-4.2-dev 4.2.3-2ubuntu7
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main g++-4.2 4.2.3-2ubuntu7
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main g++ 4:4.2.3-1ubuntu6
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main libtimedate-perl 1.1600-9
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main patch 2.5.9-4
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main dpkg-dev 1.14.16.6ubuntu4
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main build-essential 11.3ubuntu1
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/libstdc++6-4.2-dev_4.2.3-2ubuntu7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/libstdc++6-4.2-dev_4.2.3-2ubuntu7_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/g++-4.2_4.2.3-2ubuntu7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/g++-4.2_4.2.3-2ubuntu7_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.2.3-1ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.2.3-1ubuntu6_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/timedate/libtimedate-perl_1.1600-9_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/timedate/libtimedate-perl_1.1600-9_all.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.5.9-4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.5.9-4_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.14.16.6ubuntu4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.14.16.6ubuntu4_all.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
chris@chris-laptop:~$ 

Main, universe, multiverse and restricted are enabled.
proposed and backports are NOT enabled. i dont seem to be able to use terminal to get essentials?

Chris

---

### Post by NewNerd99 on 2008-10-09
would the final line :

E:.......

Be part of the problem?
Its looking for my disc drive

---

### Post by PocketDog on 2008-10-09
I had those a while back.

```
sudo apt-get update
```
fixed it

---

### Post by NewNerd99 on 2008-10-09
Thanks Pocket....No good

really becoming frustrating. Is there an area in software sources that needs to have my proxy settings?

chris@chris-laptop:~$ sudo apt-get update
[sudo] password for chris: 
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                               
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_AU              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_AU                
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy Release                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_AU           
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_AU             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                     
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                    
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_AU
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources     
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages    
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
chris@chris-laptop:~$

---

### Post by rishabh on 2008-10-09
I assume your internet works fine otherwise? You can browse the web, etc?
Try changing your download server:
System > Administration > Software Sources.
Change the "Download from:" dropdown box to some other server.

---

### Post by NewNerd99 on 2008-10-10
Yes, add/remove and synaptics package manager both work fine.

have used Main and Australia for downloads with the same result.

Will be PC-less for the next 4 days....will check back then and try the next option (if there is one) and bump it back up.

Thanks 
Chris

---

### Post by NewNerd99 on 2009-06-15
Well back to my old place of work and back to the same old problem......obviously its a firewall problem and I will head off to see the geeks this morning to see if there is anything that can be done.

Whatever it is its also preventing me accessing Facebook, Yahoo Mail and Hotmail. I have worked around the hotmail using thunderbird to import gmail and hotmail but haven't cracked the Yahoo or Facebook issues.

---

### Post by NewNerd99 on 2009-06-15
Solution was simple (in hindsight!) in the synaptics package manager both the http and ftp proxy boxes had to be filled in and have the authentication filled in to get out from behind the proxy.

---

