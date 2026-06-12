---
title: "apt-get update is not working"
date: 2013-09-02
forum: Installation &amp; Upgrades
---

### Post by khalil2 on 2013-09-02
Hello Ubuntu Community,

Lets see if you guys can  figure out this problem. I have been working with Linux for 5 years, and  with those five years, I have never had a problem with the Ubuntu apt  program. It usually works like a charm and is an instant way to get  updates and software on the fly. But it seems that my computer cannot  get it's proper updates.
 
I am running Ubuntu 12.04 3.8.0-29-generic #42~precise1-Ubuntu x86_64
I am intel dual core processor.

I  installed 12.04 on my laptop which has similar specs to my tower, but  there were no problems when I installed the Ubuntu on it. 
 
So when I attempt to do 
```
sudo apt-get update
```
I get the following:

```

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe amd64 Packages
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe amd64 Packages
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex
 Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources [6239 kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages [1640 kB]
 Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages [6167 kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages [6180 kB]
 Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en [726 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en                                             
 100% [5 Translation-en bzip2 0 B] [Waiting for headers]                                         3422 kB/s 0s
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
 You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                                             
 Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources [504 kB]                                       
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [888 kB]                                 
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en                                     
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en                                       
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en                                   
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en                                     
 Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages [406 kB]                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en                                          
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en                                    
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en                                      
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en [4133 kB]                                   
 Fetched 726 kB in 25s (29.0 kB/s)                                                                           
W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources  Hash Sum mismatch
 
W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages  Hash Sum mismatch
 
W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_main_source_Sources  Hash Sum mismatch
 
W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages  Hash Sum mismatch
 
W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.
 
```

I remember seeing during the installation process and I  was worried about it then. The first time I tried installing Ubuntu  12.04.3, the installer crashed and it said that it could not send off a  report due to the software being 3rd party and that I should delete the  3rd party software. After that, I wiped my hard drive again, did a  installation and after some time, it was complete... but I still got  those errors when it installing, but no crash.
 
Also, ever time I try to install a program, I get this
```

~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
 requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
 
The following packages have unmet dependencies:
 apache2 : Depends: apache2-mpm-worker (= 2.2.22-1ubuntu1.4) but it is not going to be installed or
                    apache2-mpm-prefork (= 2.2.22-1ubuntu1.4) but it is not going to be installed or
                     apache2-mpm-event (= 2.2.22-1ubuntu1.4) but it is not going to be installed or
                    apache2-mpm-itk (= 2.2.22-1ubuntu1.4) but it is not going to be installed
           Depends: apache2.2-common (= 2.2.22-1ubuntu1.4) but it is not going to be installed
 E: Unable to correct problems, you have held broken packages.

```

This happens with all programs I try to install, so now my ability to install software is broken too.

Lastly, I have tried almost everything I could find. Such as:
 
```

sudo apt-get clean
cd /var/lib/apt/lists/partial
sudo rm *
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade

```

same result.


```

sudo apt-get clean
 mv /var/lib/apt /var/lib/apt.old
mv /var/cache/apt /var/cache/apt.old
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade

```

Also results in failure.


I even tried these links

[http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies)
[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)


I thought that would have been my last stop and I would be done with the problem. But alace, I am still with it.


Can anyone else help me to figure out what is wrong with my system?

---

### Post by julio_che on 2013-09-07
Try this:

sudo rm -fv /var/lib/apt/lists/*
sudo apt-get update

---

### Post by ibjsb4 on 2013-09-08
Your links seem to cover everything.  The only thing I didn't see, was any reference to a router.  Are you using a router?  Bypass it.

---

