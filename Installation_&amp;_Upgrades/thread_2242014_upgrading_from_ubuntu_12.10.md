---
title: "upgrading from ubuntu 12.10"
date: 2014-08-30
forum: Installation &amp; Upgrades
---

### Post by hema3 on 2014-08-30
Hi, I am trying to upgrade from my ubuntu 12.10 as it is no longer supported.
I dont want to install newly from cd by copying iso image, when i tried to upgrade using update manger, i get the messge, "FAILED TO DOWNLOAD FROM REPOSITORY CHECK YOUR INTERNET CONNECTION"
When i tried to run sudo apt-get update in terminal, i get the following error:

```
hema@hema-desktop:~$ sudo apt-get update
[sudo] password for hema: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg           
Hit [http://dl.google.com](http://dl.google.com) stable Release               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal InRelease 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security Release.gpg
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Sources    
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe Translation-en
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```


can anyone help pls??? Thanks in advance

---

### Post by claracc on 2014-08-30
You receive the not found error since the ubuntu 12.10 reached its end of life support long time ago, repositories are removed from the server and are not found. 

To install a supported release as 14.04 through upgradings you have a lot of steps to do: 12.10--> 13.04 -->13.10 -->14.04, all of them unsupported except the last one, so the probability of failing is very high.

What I would do is to backup my home folder and make a fresh install of ubuntu 12.04 or 14.04 which are now supported for various years.

---

### Post by QIII on 2014-08-30
Hello!

As stated, 12.10 is EOL and the upgrade path would take you through a series of EOL releases.  That is a recipe for failure.  

Your best course of action would be to do a fresh installation of 14.04.  *Back up all of your important files in case you encounter problems.*

You can preserve your /home by selecting "Something else" when the installer gets to the point of creating partitions -- provided you have a separate /home partition. 

For that, please see oldfred's post #2 [here]("http://ubuntuforums.org/showthread.php?t=2135931").  This should still be appropriate.

Cheers!

---

