---
title: "sudo apt-get install apache 2 doesn't work"
date: 2019-06-26
forum: Installation &amp; Upgrades
---

### Post by gianmarcogg03 on 2019-06-26
Everytime I want to install a package with sudo apt-get install <name> I get an error saying that it can't find the package. How can I fix this? I'm new to Ubuntu.

---

### Post by TheFu on 2019-06-26
You need to know the correct name of the package.
BTW, you also need to have a patched system or dependency issues are likely to cause failure.
```
sudo apt update && sudo apt upgrade
```

Lastly, if you have a supported version of Ubuntu, probably better to use **sudo apt install {package}** rather than apt-get for most uses.

If you show the exact command being used, perhaps someone could help?

---

### Post by gianmarcogg03 on 2019-06-26
> **TheFu said:**
> You need to know the correct name of the package.
BTW, you also need to have a patched system or dependency issues are likely to cause failure.
```
sudo apt update && sudo apt upgrade
```

Lastly, if you have a supported version of Ubuntu, probably better to use **sudo apt install {package}** rather than apt-get for most uses.

If you show the exact command being used, perhaps someone could help?

I tried update and upgrade and then the install command but I got the same error, by the way the command was "sudo apt-get install apache2" or "sudo apt install apache2" (both of them give me that error).

---

### Post by Impavidus on 2019-06-26
Which release of Ubuntu are you running? Could you post the complete output of```
sudo apt update
```If apt cannot find some packages, maybe your sources are incorrectly configured. Also show us the contents of /etc/apt/sources.list:```
cat /etc/atp/sources.list
```

---

### Post by oldos2er on 2019-06-26
> **gianmarcogg03 said:**
> I tried update and upgrade and then the install command but I got the same error, by the way the command was "sudo apt-get install apache2" or "sudo apt install apache2" (both of them give me that error).

[s]There's no package named "apache2."[/s] If you're running 19.04, see [https://packages.ubuntu.com/disco/apache2]("https://packages.ubuntu.com/disco/apache2")

Edit: Thanks for the info everyone, there *is* an apache2 package for 19.04

---

### Post by TheFu on 2019-06-26
> **oldos2er said:**
> There's no package named "apache2." If you're running 19.04, see [https://packages.ubuntu.com/disco/apache2](https://packages.ubuntu.com/disco/apache2)

What happened to it? The link shows it in all the supported releases.  On a 16.04.6 install:

```
$ sudo apt-cache search apache2
apache2 - Apache HTTP Server
apache2-bin - Apache HTTP Server (modules and other binary files)
apache2-data - Apache HTTP Server (common files)
apache2-dbg - Apache debugging symbols
apache2-dev - Apache HTTP Server (development headers)
apache2-doc - Apache HTTP Server (on-site documentation)
apache2-utils - Apache HTTP Server (utility programs for web servers)

```
Attempting to install it shows the expected output before I say N.
```
The following NEW packages will be installed:
  apache2 apache2-bin apache2-data apache2-utils libapr1 libaprutil1
  libaprutil1-dbd-sqlite3 libaprutil1-ldap

```

Looks like something in the /etc/apt/sources.list isn't right or it could be a conflict with a PPA in sources.list.d/

I don't have anything newer than 16.04, so can't test newer releases.

---

### Post by The Cog on 2019-06-26
EDIT: Pre-empted by TheFu - I was interrupted while typing my response.

It looks as though there is an apache2 package:
```
~$ apt search apache2
Sorting... Done
Full Text Search... Done
apache2/disco 2.4.38-2ubuntu2 amd64
  Apache HTTP Server

apache2-bin/disco 2.4.38-2ubuntu2 amd64
  Apache HTTP Server (modules and other binary files)

apache2-data/disco,disco 2.4.38-2ubuntu2 all
  Apache HTTP Server (common files)

~$ sudo apt install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  apache2-bin apache2-data apache2-utils libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap
Suggested packages:
  apache2-doc apache2-suexec-pristine | apache2-suexec-custom
The following NEW packages will be installed
  apache2 apache2-bin apache2-data apache2-utils libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap
0 to upgrade, 8 to newly install, 0 to remove and 5 not to upgrade.
Need to get 1,698 kB of archives.
After this operation, 7,314 kB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```
Above was on Ubuntu 19.04 (Xubuntu actually, but I doubt it makes a difference).

---

### Post by gianmarcogg03 on 2019-06-26
I'm using Ubuntu 17.04. This is the output of the update command:
```
Ign:1 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty InReleaseIgn:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security InRelease                           
Ign:3 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates InRelease                                         
Ign:4 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports InRelease                                       
Err:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security Release                                            
  404  Not Found [IP: 91.189.88.31 80]
Ign:6 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty Release                           
Ign:7 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates Release                   
Trovato:8 [http://ppa.launchpad.net/gophers/archive/ubuntu](http://ppa.launchpad.net/gophers/archive/ubuntu) zesty InRelease         
Ign:9 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports Release
Ign:10 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main i386 Packages
Ign:11 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main amd64 Packages
Ign:12 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main all Packages
Ign:13 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-it_IT
Ign:14 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-en
Ign:15 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-it
Ign:16 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main all DEP-11 Metadata
Ign:17 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main amd64 DEP-11 Metadata
Ign:18 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main DEP-11 64x64 Icons
Ign:19 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted i386 Packages
Ign:20 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted all Packages
Ign:21 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted amd64 Packages
Ign:22 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted Translation-it_IT
Ign:23 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted Translation-it          
Ign:24 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted Translation-en          
Ign:25 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted amd64 DEP-11 Metadata
Ign:26 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted all DEP-11 Metadata
Ign:27 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted DEP-11 64x64 Icons
Ign:28 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe all Packages
Ign:29 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe amd64 Packages
Ign:30 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe i386 Packages
Ign:31 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe Translation-it_IT
Ign:32 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe Translation-en
Ign:33 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe Translation-it
Ign:34 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe amd64 DEP-11 Metadata
Ign:35 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe all DEP-11 Metadata
Ign:36 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Ign:37 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe DEP-11 64x64 Icons
Ign:38 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse all Packages
Ign:39 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse amd64 Packages
Ign:40 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse i386 Packages
Trovato:41 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release
Ign:42 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse Translation-en
Ign:43 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse Translation-it_IT
Ign:44 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse Translation-it
Ign:45 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse all DEP-11 Metadata
Ign:46 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse amd64 DEP-11 Metadata
Ign:47 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse DEP-11 64x64 Icons
Ign:49 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main amd64 Packages
Ign:50 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main i386 Packages
Ign:51 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main all Packages
Ign:52 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-it_IT
Ign:53 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-en
Ign:54 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-it
Ign:55 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main amd64 DEP-11 Metadata
Ign:56 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main all DEP-11 Metadata
Ign:57 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main DEP-11 64x64 Icons
Ign:58 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted i386 Packages
Ign:59 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted all Packages
Ign:60 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted amd64 Packages
Ign:61 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted Translation-en
Ign:62 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted Translation-it
Ign:63 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted Translation-it_IT
Ign:64 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted all DEP-11 Metadata
Ign:65 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted amd64 DEP-11 Metadata
Ign:66 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted DEP-11 64x64 Icons
Ign:67 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe i386 Packages
Ign:68 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 Packages
Ign:69 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe all Packages
Ign:70 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe Translation-it
Ign:71 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe Translation-en
Ign:72 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe Translation-it_IT
Ign:73 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe all DEP-11 Metadata
Ign:74 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 DEP-11 Metadata
Ign:75 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe DEP-11 64x64 Icons
Ign:76 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse all Packages
Ign:77 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse i386 Packages
Ign:78 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse amd64 Packages
Ign:79 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse Translation-it
Ign:80 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse Translation-it_IT
Ign:81 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse Translation-en
Ign:82 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse all DEP-11 Metadata
Ign:83 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse amd64 DEP-11 Metadata
Ign:84 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse DEP-11 64x64 Icons
Ign:85 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main amd64 Packages
Ign:86 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main all Packages
Ign:87 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main i386 Packages
Ign:88 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-en
Ign:89 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-it_IT
Ign:90 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-it
Ign:91 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main amd64 DEP-11 Metadata
Ign:92 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main all DEP-11 Metadata
Ign:93 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main DEP-11 64x64 Icons
Ign:94 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted i386 Packages
Ign:95 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted all Packages
Ign:96 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted amd64 Packages
Ign:97 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted Translation-it
Ign:98 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted Translation-it_IT
Ign:99 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted Translation-en
Ign:100 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted amd64 DEP-11 Metadata
Ign:101 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted all DEP-11 Metadata
Ign:102 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted DEP-11 64x64 Icons
Ign:103 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe all Packages
Ign:104 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe amd64 Packages
Ign:105 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe i386 Packages
Ign:106 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe Translation-it_IT
Ign:107 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe Translation-en
Ign:108 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe Translation-it
Ign:109 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe all DEP-11 Metadata
Ign:110 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe amd64 DEP-11 Metadata
Ign:111 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe DEP-11 64x64 Icons
Ign:112 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse amd64 Packages
Ign:113 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse all Packages
Ign:114 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse i386 Packages
Ign:115 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse Translation-it_IT
Ign:116 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse Translation-it
Ign:117 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse Translation-en
Ign:118 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse amd64 DEP-11 Metadata
Ign:119 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse all DEP-11 Metadata
Ign:120 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse DEP-11 64x64 Icons
Ign:10 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main i386 Packages
Ign:11 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main amd64 Packages
Ign:12 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main all Packages
Ign:13 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-it_IT
Ign:14 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-en
Ign:15 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-it
Ign:16 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main all DEP-11 Metadata
Ign:17 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main amd64 DEP-11 Metadata
Ign:18 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main DEP-11 64x64 Icons
Ign:19 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted i386 Packages
Ign:20 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted all Packages
Ign:21 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted amd64 Packages
Ign:22 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted Translation-it_IT
Ign:23 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted Translation-it
Ign:24 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted Translation-en
Ign:25 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted amd64 DEP-11 Metadata
Ign:26 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted all DEP-11 Metadata
Ign:27 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted DEP-11 64x64 Icons
Ign:28 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe all Packages
Ign:29 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe amd64 Packages
Ign:30 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe i386 Packages
Ign:31 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe Translation-it_IT
Ign:32 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe Translation-en
Ign:33 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe Translation-it
Ign:34 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe amd64 DEP-11 Metadata
Ign:35 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe all DEP-11 Metadata
Ign:37 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe DEP-11 64x64 Icons
Ign:38 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse all Packages
Ign:39 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse amd64 Packages
Ign:40 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse i386 Packages
Ign:42 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse Translation-en
Ign:43 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse Translation-it_IT
Ign:44 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse Translation-it
Ign:45 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse all DEP-11 Metadata
Ign:46 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse amd64 DEP-11 Metadata
Ign:47 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse DEP-11 64x64 Icons
Ign:49 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main amd64 Packages
Ign:50 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main i386 Packages
Ign:51 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main all Packages
Ign:52 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-it_IT
Ign:53 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-en
Ign:54 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-it
Ign:55 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main amd64 DEP-11 Metadata
Ign:56 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main all DEP-11 Metadata
Ign:57 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main DEP-11 64x64 Icons
Ign:58 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted i386 Packages
Ign:59 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted all Packages
Ign:60 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted amd64 Packages
Ign:61 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted Translation-en
Ign:62 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted Translation-it
Ign:63 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted Translation-it_IT
Ign:64 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted all DEP-11 Metadata
Ign:65 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted amd64 DEP-11 Metadata
Ign:66 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted DEP-11 64x64 Icons
Ign:67 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe i386 Packages
Ign:68 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 Packages
Ign:69 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe all Packages
Ign:70 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe Translation-it
Ign:71 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe Translation-en
Ign:72 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe Translation-it_IT
Ign:73 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe all DEP-11 Metadata
Ign:74 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 DEP-11 Metadata
Ign:75 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe DEP-11 64x64 Icons
Ign:76 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse all Packages
Ign:77 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse i386 Packages
Ign:78 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse amd64 Packages
Ign:79 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse Translation-it
Ign:80 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse Translation-it_IT
Ign:81 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse Translation-en
Ign:82 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse all DEP-11 Metadata
Ign:83 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse amd64 DEP-11 Metadata
Ign:84 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse DEP-11 64x64 Icons
Ign:85 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main amd64 Packages
Ign:86 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main all Packages
Ign:87 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main i386 Packages
Ign:88 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-en
Ign:89 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-it_IT
Ign:90 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-it
Ign:91 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main amd64 DEP-11 Metadata
Ign:92 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main all DEP-11 Metadata
Ign:93 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main DEP-11 64x64 Icons
Ign:94 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted i386 Packages
Ign:95 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted all Packages
Ign:96 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted amd64 Packages
Ign:97 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted Translation-it
Ign:98 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted Translation-it_IT
Ign:99 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted Translation-en
Ign:100 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted amd64 DEP-11 Metadata
Ign:101 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted all DEP-11 Metadata
Ign:102 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted DEP-11 64x64 Icons
Ign:103 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe all Packages
Ign:104 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe amd64 Packages
Ign:105 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe i386 Packages
Ign:106 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe Translation-it_IT
Ign:107 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe Translation-en
Ign:108 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe Translation-it
Ign:109 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe all DEP-11 Metadata
Ign:110 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe amd64 DEP-11 Metadata
Ign:111 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe DEP-11 64x64 Icons
Ign:112 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse amd64 Packages
Ign:113 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse all Packages
Ign:114 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse i386 Packages
Ign:115 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse Translation-it_IT
Ign:116 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse Translation-it
Ign:117 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse Translation-en
Ign:118 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse amd64 DEP-11 Metadata
Ign:119 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse all DEP-11 Metadata
Ign:120 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse DEP-11 64x64 Icons
Ign:10 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main i386 Packages
Ign:11 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main amd64 Packages
Ign:12 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main all Packages
Ign:13 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-it_IT
Ign:14 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-en
Ign:15 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-it
Ign:16 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main all DEP-11 Metadata
Ign:17 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main amd64 DEP-11 Metadata
Ign:18 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main DEP-11 64x64 Icons
Ign:19 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted i386 Packages
Ign:20 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted all Packages
Ign:21 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted amd64 Packages
Ign:22 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted Translation-it_IT
Ign:23 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted Translation-it
Ign:24 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted Translation-en
Ign:25 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted amd64 DEP-11 Metadata
Ign:26 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted all DEP-11 Metadata
Ign:27 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted DEP-11 64x64 Icons
Ign:28 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe all Packages
Ign:29 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe amd64 Packages
Ign:30 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe i386 Packages
Ign:31 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe Translation-it_IT
Ign:32 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe Translation-en
Ign:33 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe Translation-it
Ign:34 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe amd64 DEP-11 Metadata
Ign:35 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe all DEP-11 Metadata
Ign:37 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe DEP-11 64x64 Icons
Ign:38 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse all Packages
Ign:39 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse amd64 Packages
Ign:40 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse i386 Packages
Ign:42 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse Translation-en
Ign:43 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse Translation-it_IT
Ign:44 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse Translation-it
Ign:45 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse all DEP-11 Metadata
Ign:46 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse amd64 DEP-11 Metadata
Ign:47 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse DEP-11 64x64 Icons
Ign:49 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main amd64 Packages
Ign:50 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main i386 Packages
Ign:51 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main all Packages
Ign:52 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-it_IT
Ign:53 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-en
Ign:54 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-it
Ign:55 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main amd64 DEP-11 Metadata
Ign:56 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main all DEP-11 Metadata
Ign:57 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main DEP-11 64x64 Icons
Ign:58 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted i386 Packages
Ign:59 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted all Packages
Ign:60 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted amd64 Packages
Ign:61 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted Translation-en
Ign:62 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted Translation-it
Ign:63 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted Translation-it_IT
Ign:64 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted all DEP-11 Metadata
Ign:65 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted amd64 DEP-11 Metadata
Ign:66 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted DEP-11 64x64 Icons
Ign:67 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe i386 Packages
Ign:68 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 Packages
Ign:69 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe all Packages
Ign:70 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe Translation-it
Ign:71 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe Translation-en
Ign:72 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe Translation-it_IT
Ign:73 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe all DEP-11 Metadata
Ign:74 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 DEP-11 Metadata
Ign:75 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe DEP-11 64x64 Icons
Ign:76 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse all Packages
Ign:77 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse i386 Packages
Ign:78 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse amd64 Packages
Ign:79 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse Translation-it
Ign:80 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse Translation-it_IT
Ign:81 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse Translation-en
Ign:82 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse all DEP-11 Metadata
Ign:83 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse amd64 DEP-11 Metadata
Ign:84 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse DEP-11 64x64 Icons
Ign:85 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main amd64 Packages
Ign:86 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main all Packages
Ign:87 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main i386 Packages
Ign:88 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-en
Ign:89 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-it_IT
Ign:90 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-it
Ign:91 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main amd64 DEP-11 Metadata
Ign:92 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main all DEP-11 Metadata
Ign:93 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main DEP-11 64x64 Icons
Ign:94 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted i386 Packages
Ign:95 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted all Packages
Ign:96 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted amd64 Packages
Ign:97 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted Translation-it
Ign:98 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted Translation-it_IT
Ign:99 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted Translation-en
Ign:100 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted amd64 DEP-11 Metadata
Ign:101 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted all DEP-11 Metadata
Ign:102 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted DEP-11 64x64 Icons
Ign:103 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe all Packages
Ign:104 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe amd64 Packages
Ign:105 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe i386 Packages
Ign:106 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe Translation-it_IT
Ign:107 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe Translation-en
Ign:108 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe Translation-it
Ign:109 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe all DEP-11 Metadata
Ign:110 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe amd64 DEP-11 Metadata
Ign:111 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe DEP-11 64x64 Icons
Ign:112 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse amd64 Packages
Ign:113 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse all Packages
Ign:114 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse i386 Packages
Ign:115 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse Translation-it_IT
Ign:116 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse Translation-it
Ign:117 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse Translation-en
Ign:118 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse amd64 DEP-11 Metadata
Ign:119 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse all DEP-11 Metadata
Ign:120 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse DEP-11 64x64 Icons
Ign:10 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main i386 Packages
Ign:11 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main amd64 Packages
Ign:12 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main all Packages
Ign:13 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-it_IT
Ign:14 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-en
Ign:15 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-it
Ign:16 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main all DEP-11 Metadata
Ign:17 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main amd64 DEP-11 Metadata
Ign:18 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main DEP-11 64x64 Icons
Ign:19 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted i386 Packages
Ign:20 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted all Packages
Ign:21 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted amd64 Packages
Ign:22 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted Translation-it_IT
Ign:23 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted Translation-it
Ign:24 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted Translation-en
Ign:25 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted amd64 DEP-11 Metadata
Ign:26 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted all DEP-11 Metadata
Ign:27 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted DEP-11 64x64 Icons
Ign:28 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe all Packages
Ign:29 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe amd64 Packages
Ign:30 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe i386 Packages
Ign:31 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe Translation-it_IT
Ign:32 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe Translation-en
Ign:33 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe Translation-it
Ign:34 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe amd64 DEP-11 Metadata
Ign:35 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe all DEP-11 Metadata
Ign:37 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe DEP-11 64x64 Icons
Ign:38 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse all Packages
Ign:39 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse amd64 Packages
Ign:40 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse i386 Packages
Ign:42 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse Translation-en
Ign:43 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse Translation-it_IT
Ign:44 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse Translation-it
Ign:45 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse all DEP-11 Metadata
Ign:46 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse amd64 DEP-11 Metadata
Ign:47 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse DEP-11 64x64 Icons
Ign:49 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main amd64 Packages
Ign:50 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main i386 Packages
Ign:51 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main all Packages
Ign:52 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-it_IT
Ign:53 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-en
Ign:54 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-it
Ign:55 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main amd64 DEP-11 Metadata
Ign:56 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main all DEP-11 Metadata
Ign:57 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main DEP-11 64x64 Icons
Ign:58 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted i386 Packages
Ign:59 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted all Packages
Ign:60 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted amd64 Packages
Ign:61 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted Translation-en
Ign:62 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted Translation-it
Ign:63 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted Translation-it_IT
Ign:64 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted all DEP-11 Metadata
Ign:65 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted amd64 DEP-11 Metadata
Ign:66 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted DEP-11 64x64 Icons
Ign:67 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe i386 Packages
Ign:68 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 Packages
Ign:69 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe all Packages
Ign:70 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe Translation-it
Ign:71 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe Translation-en
Ign:72 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe Translation-it_IT
Ign:73 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe all DEP-11 Metadata
Ign:74 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 DEP-11 Metadata
Ign:75 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe DEP-11 64x64 Icons
Ign:76 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse all Packages
Ign:77 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse i386 Packages
Ign:78 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse amd64 Packages
Ign:79 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse Translation-it
Ign:80 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse Translation-it_IT
Ign:81 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse Translation-en
Ign:82 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse all DEP-11 Metadata
Ign:83 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse amd64 DEP-11 Metadata
Ign:84 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse DEP-11 64x64 Icons
Ign:85 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main amd64 Packages
Ign:86 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main all Packages
Ign:87 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main i386 Packages
Ign:88 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-en
Ign:89 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-it_IT
Ign:90 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-it
Ign:91 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main amd64 DEP-11 Metadata
Ign:92 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main all DEP-11 Metadata
Ign:93 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main DEP-11 64x64 Icons
Ign:94 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted i386 Packages
Ign:95 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted all Packages
Ign:96 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted amd64 Packages
Ign:97 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted Translation-it
Ign:98 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted Translation-it_IT
Ign:99 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted Translation-en
Ign:100 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted amd64 DEP-11 Metadata
Ign:101 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted all DEP-11 Metadata
Ign:102 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted DEP-11 64x64 Icons
Ign:103 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe all Packages
Ign:104 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe amd64 Packages
Ign:105 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe i386 Packages
Ign:106 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe Translation-it_IT
Ign:107 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe Translation-en
Ign:108 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe Translation-it
Ign:109 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe all DEP-11 Metadata
Ign:110 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe amd64 DEP-11 Metadata
Ign:111 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe DEP-11 64x64 Icons
Ign:112 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse amd64 Packages
Ign:113 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse all Packages
Ign:114 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse i386 Packages
Ign:115 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse Translation-it_IT
Ign:116 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse Translation-it
Ign:117 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse Translation-en
Ign:118 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse amd64 DEP-11 Metadata
Ign:119 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse all DEP-11 Metadata
Ign:120 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse DEP-11 64x64 Icons
Ign:10 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main i386 Packages
Ign:11 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main amd64 Packages
Ign:12 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main all Packages
Ign:13 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-it_IT
Ign:14 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-en
Ign:15 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-it
Ign:16 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main all DEP-11 Metadata
Ign:17 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main amd64 DEP-11 Metadata
Ign:18 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main DEP-11 64x64 Icons
Ign:19 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted i386 Packages
Ign:20 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted all Packages
Ign:21 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted amd64 Packages
Ign:22 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted Translation-it_IT
Ign:23 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted Translation-it
Ign:24 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted Translation-en
Ign:25 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted amd64 DEP-11 Metadata
Ign:26 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted all DEP-11 Metadata
Ign:27 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted DEP-11 64x64 Icons
Ign:28 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe all Packages
Ign:29 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe amd64 Packages
Ign:30 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe i386 Packages
Ign:31 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe Translation-it_IT
Ign:32 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe Translation-en
Ign:33 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe Translation-it
Ign:34 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe amd64 DEP-11 Metadata
Ign:35 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe all DEP-11 Metadata
Ign:37 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/universe DEP-11 64x64 Icons
Ign:38 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse all Packages
Ign:39 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse amd64 Packages
Ign:40 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse i386 Packages
Ign:42 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse Translation-en
Ign:43 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse Translation-it_IT
Ign:44 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse Translation-it
Ign:45 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse all DEP-11 Metadata
Ign:46 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse amd64 DEP-11 Metadata
Ign:47 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/multiverse DEP-11 64x64 Icons
Ign:49 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main amd64 Packages
Ign:50 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main i386 Packages
Ign:51 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main all Packages
Ign:52 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-it_IT
Ign:53 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-en
Ign:54 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-it
Ign:55 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main amd64 DEP-11 Metadata
Ign:56 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main all DEP-11 Metadata
Ign:57 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main DEP-11 64x64 Icons
Ign:58 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted i386 Packages
Ign:59 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted all Packages
Ign:60 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted amd64 Packages
Ign:61 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted Translation-en
Ign:62 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted Translation-it
Ign:63 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted Translation-it_IT
Ign:64 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted all DEP-11 Metadata
Ign:65 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted amd64 DEP-11 Metadata
Ign:66 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted DEP-11 64x64 Icons
Ign:67 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe i386 Packages
Ign:68 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 Packages
Ign:69 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe all Packages
Ign:70 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe Translation-it
Ign:71 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe Translation-en
Ign:72 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe Translation-it_IT
Ign:73 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe all DEP-11 Metadata
Ign:74 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 DEP-11 Metadata
Ign:75 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/universe DEP-11 64x64 Icons
Ign:76 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse all Packages
Ign:77 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse i386 Packages
Ign:78 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse amd64 Packages
Ign:79 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse Translation-it
Ign:80 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse Translation-it_IT
Ign:81 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse Translation-en
Ign:82 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse all DEP-11 Metadata
Ign:83 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse amd64 DEP-11 Metadata
Ign:84 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/multiverse DEP-11 64x64 Icons
Ign:85 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main amd64 Packages
Ign:86 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main all Packages
Ign:87 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main i386 Packages
Ign:88 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-en
Ign:89 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-it_IT
Ign:90 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-it
Ign:91 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main amd64 DEP-11 Metadata
Ign:92 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main all DEP-11 Metadata
Ign:93 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main DEP-11 64x64 Icons
Ign:94 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted i386 Packages
Ign:95 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted all Packages
Ign:96 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted amd64 Packages
Ign:97 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted Translation-it
Ign:98 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted Translation-it_IT
Ign:99 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted Translation-en
Ign:100 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted amd64 DEP-11 Metadata
Ign:101 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted all DEP-11 Metadata
Ign:102 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted DEP-11 64x64 Icons
Ign:103 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe all Packages
Ign:104 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe amd64 Packages
Ign:105 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe i386 Packages
Ign:106 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe Translation-it_IT
Ign:107 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe Translation-en
Ign:108 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe Translation-it
Ign:109 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe all DEP-11 Metadata
Ign:110 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe amd64 DEP-11 Metadata
Ign:111 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/universe DEP-11 64x64 Icons
Ign:112 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse amd64 Packages
Ign:113 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse all Packages
Ign:114 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse i386 Packages
Ign:115 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse Translation-it_IT
Ign:116 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse Translation-it
Ign:117 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse Translation-en
Ign:118 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse amd64 DEP-11 Metadata
Ign:119 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse all DEP-11 Metadata
Ign:120 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/multiverse DEP-11 64x64 Icons
Err:10 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main i386 Packages
  404  Not Found [IP: 90.147.160.70 80]
Ign:11 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main amd64 Packages
Ign:12 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main all Packages
Ign:13 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-it_IT
Ign:14 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-en
Ign:15 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main Translation-it
Ign:16 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main all DEP-11 Metadata
Ign:17 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main amd64 DEP-11 Metadata
Ign:18 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/main DEP-11 64x64 Icons
Ign:19 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted i386 Packages
Ign:20 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty/restricted all Packages
Err:49 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main amd64 Packages
  404  Not Found [IP: 90.147.160.70 80]
Ign:50 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main i386 Packages
Ign:51 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main all Packages
Ign:52 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-it_IT
Ign:53 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-en
Ign:54 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main Translation-it
Ign:55 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main amd64 DEP-11 Metadata
Ign:56 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main all DEP-11 Metadata
Ign:57 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/main DEP-11 64x64 Icons
Ign:58 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted i386 Packages
Ign:59 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-updates/restricted all Packages
Err:85 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main amd64 Packages
  404  Not Found [IP: 90.147.160.70 80]
Ign:86 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main all Packages
Ign:87 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main i386 Packages
Ign:88 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-en
Ign:89 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-it_IT
Ign:90 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main Translation-it
Ign:91 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main amd64 DEP-11 Metadata
Ign:92 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main all DEP-11 Metadata
Ign:93 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/main DEP-11 64x64 Icons
Ign:94 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted i386 Packages
Ign:95 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) zesty-backports/restricted all Packages
Lettura elenco dei pacchetti... Fatto
E: The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://it.archive.ubuntu.com/ubuntu zesty Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://it.archive.ubuntu.com/ubuntu zesty-updates Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://it.archive.ubuntu.com/ubuntu zesty-backports Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by deadflowr on 2019-06-26
Well there you go.
Install a supported release.

---

### Post by gianmarcogg03 on 2019-06-26
> **deadflowr said:**
> Well there you go.
Install a supported release.

OK, which one?

---

### Post by deadflowr on 2019-06-26
Either 16.04 or 18.04 will do.
both are LTS (long term-supported) releases.
16.04 will be supported until 2021.
18.04 will be supported until 2023.
And both also have the option for further support through Ubuntu Advantage.

If you need some newer features then go with 18.04.

---

### Post by rsteinmetz70112 on 2019-06-26
I would do 18.04 since the newest LTS and you don't appear to upgrade frequently.

---

### Post by TheFu on 2019-06-26
> **gianmarcogg03 said:**
> OK, which one?

It is an important thing to stay on supported releases.  17.04 has been dead since Dec, 2017.  Any attempted patching you've tried since then has done ZERO. Nothing. Nada.  There are a number of remote access root exploits for that kernel.

For people like you and me, we need to be on **supported LTS** releases always and ignore the intermediate, non-LTS, releases.

---

