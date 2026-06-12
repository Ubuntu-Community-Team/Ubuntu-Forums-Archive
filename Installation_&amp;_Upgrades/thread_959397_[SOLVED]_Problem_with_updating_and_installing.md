---
title: "[SOLVED] Problem with updating and installing"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by Intlex on 2008-10-26
Hi, I have a problem with updating and installing new packages.
I searched the forum, and saw few threads with similar problem, but all of them were different then this. 
This Problem with all the packages. I tried to use things from other posts, but it didn't help.

When I try to update using "Update Manager"
I got this:

[IMG]http://img236.imageshack.us/img236/817/errorov1.jpg[/IMG]

Then I tried to fix it from the shell(with things from other posts), and update from there:
```

[COLOR=DarkGreen]intlex@home:~$ sudo apt-get autoclean 
[sudo] password for intlex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
intlex@home:~$ 
intlex@home:~$ 
intlex@home:~$ sudo dpkg --configure -a
intlex@home:~$ 
intlex@home:~$ 
intlex@home:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
intlex@home:~$
intlex@home:~$  
intlex@home:~$ sudo apt-get update
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US
Hit http://packages.medibuntu.org hardy Release.gpg
Hit http://archive.ubuntu.com hardy Release.gpg
Ign http://archive.ubuntu.com hardy/main Translation-en_US                     
Hit http://archive.canonical.com hardy Release                                 
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US               
Ign http://archive.ubuntu.com hardy/universe Translation-en_US                 
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy-updates Release.gpg
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy-security Release.gpg
Hit http://archive.canonical.com hardy/partner Packages              
Ign http://packages.medibuntu.org hardy/free Translation-en_US       
Ign http://archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_US        
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_US      
Hit http://archive.ubuntu.com hardy-backports Release.gpg                      
Ign http://archive.ubuntu.com hardy-backports/restricted Translation-en_US     
Hit http://archive.canonical.com hardy/partner Sources                         
Ign http://archive.ubuntu.com hardy-backports/main Translation-en_US           
Ign http://archive.ubuntu.com hardy-backports/multiverse Translation-en_US     
Ign http://archive.ubuntu.com hardy-backports/universe Translation-en_US
Hit http://archive.ubuntu.com hardy Release
Hit http://archive.ubuntu.com hardy-updates Release
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US  
Hit http://archive.ubuntu.com hardy-security Release
Hit http://archive.ubuntu.com hardy-backports Release                          
Hit http://archive.ubuntu.com hardy/main Packages                              
Hit http://archive.ubuntu.com hardy/restricted Packages                        
Hit http://archive.ubuntu.com hardy/main Sources
Hit http://archive.ubuntu.com hardy/restricted Sources
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/universe Sources
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com hardy/multiverse Sources
Hit http://archive.ubuntu.com hardy-updates/main Packages
Hit http://packages.medibuntu.org hardy Release
Hit http://archive.ubuntu.com hardy-updates/restricted Packages
Hit http://archive.ubuntu.com hardy-updates/main Sources                       
Hit http://archive.ubuntu.com hardy-updates/restricted Sources                 
Hit http://archive.ubuntu.com hardy-updates/universe Packages                  
Hit http://archive.ubuntu.com hardy-updates/universe Sources                   
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages                
Hit http://archive.ubuntu.com hardy-updates/multiverse Sources                 
Hit http://archive.ubuntu.com hardy-security/main Packages                     
Hit http://archive.ubuntu.com hardy-security/restricted Packages               
Hit http://archive.ubuntu.com hardy-security/main Sources                      
Hit http://archive.ubuntu.com hardy-security/restricted Sources
Hit http://archive.ubuntu.com hardy-security/universe Packages
Hit http://archive.ubuntu.com hardy-security/universe Sources
Hit http://archive.ubuntu.com hardy-security/multiverse Packages
Hit http://archive.ubuntu.com hardy-security/multiverse Sources
Hit http://archive.ubuntu.com hardy-backports/restricted Packages
Hit http://archive.ubuntu.com hardy-backports/main Packages
Hit http://archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://archive.ubuntu.com hardy-backports/universe Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Reading package lists... Done                            
intlex@home:~$ 
intlex@home:~$ 
intlex@home:~$ 
intlex@home:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libdns35 libisccc30 libisccfg30
The following packages will be upgraded:
  cpp-4.2 g++-4.2 gcc-4.2 gcc-4.2-base gstreamer0.10-tools libexif12 libffi4
  libgcc1 libglib2.0-0 libgomp1 libgstreamer0.10-0 liblwres30 libstdc++6
  libstdc++6-4.2-dev pciutils tzdata tzdata-java
17 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B/10.0MB of archives.
After this operation, 8192B disk space will be freed.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
dpkg-deb: subprocess tar killed by signal (Segmentation fault)
dpkg: error processing /var/cache/apt/archives/libstdc++6-4.2-dev_4.2.4-1ubuntu3_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: subprocess **tar** killed by signal (**Segmentation fault**)
dpkg: error processing /var/cache/apt/archives/g++-4.2_4.2.4-1ubuntu3_i386.deb (**--unpack**):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: subprocess **tar** killed by signal (**Segmentation fault**)
dpkg: error processing /var/cache/apt/archives/gcc-4.2_4.2.4-1ubuntu3_i386.deb (**--unpack**):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: subprocess** tar** killed by signal (**Segmentation fault**)
dpkg: error processing /var/cache/apt/archives/cpp-4.2_4.2.4-1ubuntu3_i386.deb (**--unpack**):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: subprocess **tar **killed by signal (**Segmentation fault**)
dpkg: error processing /var/cache/apt/archives/gcc-4.2-base_4.2.4-1ubuntu3_i386.deb (**--unpack**):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libstdc++6-4.2-dev_4.2.4-1ubuntu3_i386.deb
 /var/cache/apt/archives/g++-4.2_4.2.4-1ubuntu3_i386.deb
 /var/cache/apt/archives/gcc-4.2_4.2.4-1ubuntu3_i386.deb
 /var/cache/apt/archives/cpp-4.2_4.2.4-1ubuntu3_i386.deb
 /var/cache/apt/archives/gcc-4.2-base_4.2.4-1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
intlex@home:~$ 
intlex@home:~$ [/COLOR]

```In the error message I saw the words "*--unpack*" and "*tar*", so I thought may be a problem in tar.
And when  I tried to extract regular .tar.gz file i saw same error : **Segmentation fault**
```
[COLOR=DarkGreen]intlex@home:~/Desktop$ tar -xf GNS3-0.5-src.tar.gz 
Segmentation fault[/COLOR]
```Can someone help me to solve it, please ?
P.S. Sorry for my English.

---

### Post by francisc1701 on 2008-10-26
Yes, tar seems to crash. I have no idea why, though.

Try reinstalling tar:
```
# apt-get remove --purge tar
# apt-get install tar
```

Make friends with google. It can be great help because chances are someone else already encountered the problem you're facing and has a solution. So try googling for "tar segmentation fault" or "dpkg-deb: subprocess tar killed by signal (Segmentation fault)"

Sorry I can't be any more helpful.

---

### Post by Intlex on 2008-10-26
I did it, and it did solved the problem.
I think it wasn't good idea, because it seems to try using tar to install tar, and of course doesn't find it. Here is the log.  
```
[COLOR="DarkGreen"]intlex@home:~$ sudo apt-get remove --purge tar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  file-roller* tar* ubuntu-desktop* ubuntu-minimal*
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  tar
0 upgraded, 0 newly installed, 4 to remove and 23 not upgraded.
After this operation, 7463kB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] Yes, do as I say!
(Reading database ... 160975 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing file-roller ...
Purging configuration files for file-roller ...
Removing ubuntu-minimal ...
dpkg - warning, overriding problem because --force enabled:
 This is an essential package - it should not be removed.
Removing tar ...
Purging configuration files for tar ...
intlex@home:~$ 
intlex@home:~$ 
intlex@home:~$ 
intlex@home:~$ 
intlex@home:~$ 
intlex@home:~$ sudo apt-get install tar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ncompress
The following NEW packages will be installed:
  tar
0 upgraded, 1 newly installed, 0 to remove and 23 not upgraded.
Need to get 328kB of archives.
After this operation, 2154kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com hardy/main tar 1.19-3 [328kB]
Fetched 328kB in 1s (217kB/s)
dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/tar_1.19-3_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/tar_1.19-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
intlex@home:~$ [/COLOR]

```

Google is my good friend, I already searched there, and found only one similar problem, which was cosed by faulty memory, I scanned my memory with memtest86+, made 5 passes, and didn't find any problem.

Other ideas ?

---

### Post by Intlex on 2008-10-26
I downloaded and unpacked in windows source of tar from [http://www.gnu.org/software/tar/](http://www.gnu.org/software/tar/), booted back to ubuntu, compiled and installed it.
It solved the problem. 
Then I installed back all the packages that were removed before:
```
[COLOR="DarkGreen"]file-roller 
tar 
ubuntu-desktop 
ubuntu-minimal[/COLOR]
```

Now everything seems to be ok.

But now I have another question.
The package version of tar, which I installed from source was 1.20, what i installed after that from apt-get was 1.19-3.
Now I see
```
[COLOR="DarkGreen"]intlex@home:~$ tar --version
tar (GNU tar) 1.20[/COLOR]
```

**So does it mean tar is no more managed by apt ? It won't be updated by apt-get upgrade anymore ?**

---

### Post by francisc1701 on 2008-10-27
Yeah, I didn't think about the consequences of removing tar. Sorry. Never having done it myself I didn't know what would happen and, as I said, I didn't think either.](*,)

> **Intlex said:**
> I downloaded and unpacked in windows source of tar from [http://www.gnu.org/software/tar/](http://www.gnu.org/software/tar/), booted back to ubuntu, compiled and installed it.
It solved the problem. 
Then I installed back all the packages that were removed before:
```
[COLOR="DarkGreen"]file-roller 
tar 
ubuntu-desktop 
ubuntu-minimal[/COLOR]
```

Now everything seems to be ok.
I'm glad it works.

> **Intlex said:**
> But now I have another question.
The package version of tar, which I installed from source was 1.20, what i installed after that from apt-get was 1.19-3.
Now I see
```
[COLOR="DarkGreen"]intlex@home:~$ tar --version
tar (GNU tar) 1.20[/COLOR]
```

**So does it mean tar is no more managed by apt ? It won't be updated by apt-get upgrade anymore ?**
I don't know if apt-get upgrade will update it anymore. Maybe it will, once the version available via apt-get becomes newer than what you have.

---

