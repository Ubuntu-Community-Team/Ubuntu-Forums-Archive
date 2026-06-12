---
title: "sudo apt-get update problem!"
date: 2017-04-10
forum: Installation &amp; Upgrades
---

### Post by naderjemel on 2017-04-10
Every time when I try to run the command [HTML]sudo apt-get update[/HTML] I get this 

```
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:3 [http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu](http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu) xenial InRelease
Hit:4 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) xenial InRelease                     
Ign:5 [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) wily InRelease                           
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Hit:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:9 [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) xenial InRelease         
Get:10 [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) wily Release [6,596 B]                  
Get:11 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) xenial InRelease [20.1 kB]     
Ign:13 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial InRelease
Get:8 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Ign:15 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial InRelease         
Get:16 [https://apt.dockerproject.org/repo](https://apt.dockerproject.org/repo) ubuntu-xenial InRelease [47.8 kB]    
Hit:18 [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) xenial InRelease       
Ign:19 [https://mega.nz/linux/MEGAsync/xUbuntu_16.04](https://mega.nz/linux/MEGAsync/xUbuntu_16.04) ./ InRelease               
Ign:20 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial Release
Ign:21 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial Release           
Get:22 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [247 kB]
Ign:23 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 Packages
Get:12 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB] 
Get:24 [https://apt.dockerproject.org/repo](https://apt.dockerproject.org/repo) ubuntu-xenial/testing amd64 Packages [7,225 B]
Get:25 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages [237 kB]
Get:26 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Translation-en [105 kB]
Get:27 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [54.2 kB]
Get:28 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [42.4 kB]
Get:29 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages [108 kB]
Ign:30 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main i386 Packages
Get:31 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe i386 Packages [95.7 kB]
Get:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Translation-en [55.5 kB]
Get:33 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [32.2 kB]
Get:34 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Get:35 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) xenial/stable amd64 Packages [1,479 B]
Ign:36 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main all Packages
Ign:37 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en_US
Get:38 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [510 kB]
Ign:39 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en
Get:40 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [499 kB]
Get:41 [https://mega.nz/linux/MEGAsync/xUbuntu_16.04](https://mega.nz/linux/MEGAsync/xUbuntu_16.04) ./ Release [988 B]         
Get:42 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en [206 kB]
Get:43 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [288 kB]
Get:44 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [188 kB]
Get:45 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [452 kB]
Get:47 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [438 kB]
Get:48 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [172 kB]
Get:49 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [160 kB]
Ign:50 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Get:51 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [188 kB]
Get:52 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]
Get:53 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Ign:54 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:55 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main amd64 Packages
Ign:56 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main i386 Packages
Ign:57 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main all Packages 
Ign:58 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main Translation-en_US
Ign:59 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main Translation-en
Ign:60 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:61 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:23 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 Packages
Ign:30 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main i386 Packages
Ign:36 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main all Packages
Ign:37 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en_US
Ign:39 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en
Ign:50 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:54 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:55 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main amd64 Packages
Ign:56 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main i386 Packages
Ign:57 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main all Packages
Ign:58 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main Translation-en_US
Ign:59 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main Translation-en
Ign:60 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:61 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:23 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 Packages
Ign:30 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main i386 Packages
Ign:36 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main all Packages
Ign:37 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en_US
Ign:39 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en
Ign:50 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:54 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:55 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main amd64 Packages
Ign:56 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main i386 Packages
Ign:57 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main all Packages
Ign:58 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main Translation-en_US
Ign:59 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main Translation-en
Ign:60 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:61 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:23 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 Packages
Ign:30 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main i386 Packages
Ign:36 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main all Packages
Ign:37 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en_US
Ign:39 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en
Ign:50 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:54 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:55 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main amd64 Packages
Ign:56 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main i386 Packages
Ign:57 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main all Packages 
Ign:58 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main Translation-en_US
Ign:59 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main Translation-en
Ign:60 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:61 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:23 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 Packages
Ign:30 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main i386 Packages
Ign:36 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main all Packages
Ign:37 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en_US
Ign:39 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en
Ign:50 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:54 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:55 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main amd64 Packages
Ign:56 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main i386 Packages
Ign:57 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main all Packages 
Ign:58 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main Translation-en_US
Ign:59 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main Translation-en
Ign:60 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:61 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main DEP-11 64x64 Icons
Err:23 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 Packages
  404  Not Found
Ign:30 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main i386 Packages
Ign:36 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main all Packages
Ign:37 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en_US
Ign:39 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en
Ign:50 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:54 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Err:55 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main amd64 Packages
  404  Not Found
Ign:56 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main i386 Packages
Ign:57 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main all Packages 
Ign:58 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main Translation-en_US
Ign:59 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main Translation-en
Ign:60 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:61 [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) xenial/main DEP-11 64x64 Icons
Err:6 [http://screenshots.getdeb.net](http://screenshots.getdeb.net) xenial-getdeb InRelease                    
  Cannot initiate the connection to screenshots.getdeb.net:80 (2400:cb00:2048:1::681c:187d). - connect (101: Network is unreachable) [IP: 2400:cb00:2048:1::681c:187d 80]
Fetched 391 kB in 4min 0s (1,623 B/s)                    
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/tualatrix/next/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/xenial-getdeb/InRelease](http://archive.getdeb.net/ubuntu/dists/xenial-getdeb/InRelease)  Cannot initiate the connection to screenshots.getdeb.net:80 (2400:cb00:2048:1::681c:187d). - connect (101: Network is unreachable) [IP: 2400:cb00:2048:1::681c:187d 80]
E: Failed to fetch [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
E: Failed to fetch [http://ppa.launchpad.net/tualatrix/next/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/tualatrix/next/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
W: Some index files failed to download. They have been ignored, or old ones used instead.

```

is there any solutioN

---

### Post by Bashing-om on 2017-04-10
naderjemel; Hello ;

Bad URL ???
[http://screenshots.getdeb.net/dists/](http://screenshots.getdeb.net/dists/)

Not supported in xenial:
[http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu/dists/](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu/dists/)
[http://ppa.launchpad.net/tualatrix/next/ubuntu/dists/](http://ppa.launchpad.net/tualatrix/next/ubuntu/dists/)

Disable these PPAs .

[INDENT][INDENT]not much else to say
[/INDENT][/INDENT]

---

