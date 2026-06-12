---
title: "Updating ubuntu 16.04, later to 18.04 packages errors"
date: 2023-06-24
forum: Installation &amp; Upgrades
---

### Post by dadata on 2023-06-24
Hello all,
Greetings,
I have not updated my ubuntu 16.04 Desktop for some times. Whenever, I try, the package is broken. The goal is to upgrade to 18.04 to latest
This is how I did:
```
sudo apt-get update
```I dont if I should post the whole output or  just errors. or put into text and attach it.

```
W: Some index files failed to download. They have been ignored, or old ones used instead.
E: The package lists or status file could not be parsed or opened.

```

Thank you in advance for your help

---

### Post by guiverc on 2023-06-24
You may have problems, as Ubuntu 16.04 LTS had two *supported* upgrade paths, being to Ubuntu 16.10, or to Ubuntu 18.04 LTS, however those paths closed when [16.10 reached EOL]("https://fridge.ubuntu.com/2017/07/20/ubuntu-16-10-yakkety-yak-end-of-life-reached-on-july-20-2017/") and [18.04 reached EOSS]("https://fridge.ubuntu.com/2023/06/17/extended-security-maintenance-for-ubuntu-18-04-lts-began-on-may-31-2023/").

If you `sudo apt update` do you get any warnings, any missing lines etc... this is where I'd look first.  Read all messages (*you only provided a warning & summary error*), and contrast with your actual sources as to problems. We're limited with what you provide.

Possibly helpful link is [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) however 16.04 is still *supported* via ESM, thus that link won't be that helpful (*not all applies; as ESM impacts the status*)..   Worse is [18.04's EOSS]("https://fridge.ubuntu.com/2023/06/17/extended-security-maintenance-for-ubuntu-18-04-lts-began-on-may-31-2023/").

I only *somewhat recently *performed a *release-upgrade* of a 16.04 system to 18.04, then 20.04, however I made sure to do it before 18.04 reached EOSS as its more complex after that point.  FYI: I was going to achieve the upgrade via a *non-destructive re-install* of a later Desktop release, as I knew that would be faster, and would allow me to jump straight to 22.04 LTS (*which release-upgrades would not achieve except through multiple upgrades*).  My *release-upgrade* was ~flawless, thus I didn't do the *upgrade via re-install*.

It's been *years* since a did *upgrade via re-installs* from 16.04 or a Unity 7 default desktop (*default is now GNOME3*), thus I can't recall what the *potential difficulties *or *pitfalls* could be; but I'd start by reading the release notes (*everything significant discovered in QA goes there!*).

---

### Post by dadata on 2023-06-24
Thank you very much for your reply.
This is output.

```
Get:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease [1,825 B]         
Get:2 [http://repo.mysql.com/apt/ubuntu](http://repo.mysql.com/apt/ubuntu) xenial InRelease [22.2 kB]              
Hit:3 [http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu](http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu) xenial InRelease     
Ign:4 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg InRelease            
Hit:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Get:6 [http://cran.rstudio.com/bin/linux/ubuntu](http://cran.rstudio.com/bin/linux/ubuntu) xenial/ InRelease [3,607 B]     
Hit:7 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial InRelease                     
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [99.8 kB]    
Get:10 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-updates InRelease [99.8 kB]  
Ign:11 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg Release             
Hit:12 [http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu](http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu) xenial InRelease 
Get:13 [http://cran.mirror.ac.za//bin/linux/ubuntu](http://cran.mirror.ac.za//bin/linux/ubuntu) xenial/ InRelease [3,607 B]  
Ign:14 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main amd64 Packages.diff/Index
Hit:16 [http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu](http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu) xenial InRelease
Ign:17 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main i386 Packages.diff/Index
Get:18 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-backports InRelease [97.4 kB]
Ign:19 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main all Packages   
Ign:20 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial InRelease   
Ign:21 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main Translation-en_ZA
Ign:22 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial InRelease 
Ign:23 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main Translation-en
Ign:24 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main amd64 DEP-11 Metadata
Hit:25 [http://ppa.launchpad.net/marutter/c2d4u3.5/ubuntu](http://ppa.launchpad.net/marutter/c2d4u3.5/ubuntu) xenial InRelease      
Ign:26 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main DEP-11 64x64 Icons
Hit:27 [http://ppa.launchpad.net/noobslab/apps/ubuntu](http://ppa.launchpad.net/noobslab/apps/ubuntu) xenial InRelease          
Ign:28 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main amd64 Packages 
Ign:29 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main i386 Packages  
Hit:30 [http://ppa.launchpad.net/octave/stable/ubuntu](http://ppa.launchpad.net/octave/stable/ubuntu) xenial InRelease          
Ign:19 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main all Packages
Ign:21 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main Translation-en_ZA
Hit:31 [http://ppa.launchpad.net/persepolis/ppa/ubuntu](http://ppa.launchpad.net/persepolis/ppa/ubuntu) xenial InRelease         
Ign:23 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main Translation-en 
Hit:32 [http://ppa.launchpad.net/texworks/stable/ubuntu](http://ppa.launchpad.net/texworks/stable/ubuntu) xenial InRelease        
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Ign:24 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main amd64 DEP-11 Metadata
Get:33 [https://cloud.r-project.org/bin/linux/ubuntu](https://cloud.r-project.org/bin/linux/ubuntu) xenial-cran35/ InRelease [3,625 B]
Ign:34 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic InRelease                      
Ign:26 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main DEP-11 64x64 Icons
Hit:35 [http://ppa.launchpad.net/videolan/master-daily/ubuntu](http://ppa.launchpad.net/videolan/master-daily/ubuntu) xenial InRelease
Ign:36 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  InRelease
Ign:37 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ InRelease                  
Get:38 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease [4,502 B]                   
Get:39 [https://desktop-download.mendeley.com/download/apt](https://desktop-download.mendeley.com/download/apt) stable InRelease [2,456 B]
Hit:40 [https://packages.microsoft.com/repos/vscode](https://packages.microsoft.com/repos/vscode) stable InRelease            
Ign:28 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main amd64 Packages 
Ign:29 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main i386 Packages  
Ign:19 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main all Packages   
Ign:21 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main Translation-en_ZA
Ign:41 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial InRelease                      
Hit:42 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial InRelease       
Ign:43 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial Release     
Ign:44 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial Release   
Ign:45 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Release
Ign:46 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Release                    
Ign:23 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main Translation-en 
Get:9 [https://debian.neo4j.org:443/repo](https://debian.neo4j.org:443/repo) stable/ InRelease [134 B]              
Ign:24 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main amd64 DEP-11 Metadata
Err:9 [https://debian.neo4j.org:443/repo](https://debian.neo4j.org:443/repo) stable/ InRelease                      
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:15 [https://cran.wustl.edu/bin/linux/ubuntu](https://cran.wustl.edu/bin/linux/ubuntu) xenial/ InRelease [3,607 B]     
Ign:26 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main DEP-11 64x64 Icons
Err:6 [http://cran.rstudio.com/bin/linux/ubuntu](http://cran.rstudio.com/bin/linux/ubuntu) xenial/ InRelease               
  The following signatures were invalid: KEYEXPIRED 1602869253  KEYEXPIRED 1602869253  KEYEXPIRED 1602869253
Ign:48 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main amd64 Packages.diff/Index
Err:2 [http://repo.mysql.com/apt/ubuntu](http://repo.mysql.com/apt/ubuntu) xenial InRelease                        
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 467B942D3A79BD29
Ign:28 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main amd64 Packages 
Ign:29 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main i386 Packages  
Ign:49 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main i386 Packages.diff/Index
Get:47 [https://packages.gitlab.com/gitlab/gitlab-ee/ubuntu](https://packages.gitlab.com/gitlab/gitlab-ee/ubuntu) xenial InRelease [23.3 kB]
Ign:50 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic Release                        
Ign:51 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Packages.diff/Index
Ign:19 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main all Packages   
Err:13 [http://cran.mirror.ac.za//bin/linux/ubuntu](http://cran.mirror.ac.za//bin/linux/ubuntu) xenial/ InRelease            
  The following signatures were invalid: KEYEXPIRED 1602869253  KEYEXPIRED 1602869253  KEYEXPIRED 1602869253
Ign:52 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Packages.diff/Index        
Ign:53 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main all Packages
Ign:21 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main Translation-en_ZA
Ign:23 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main Translation-en 
Ign:54 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main Translation-en_ZA
Ign:24 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main amd64 DEP-11 Metadata
Get:55 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [326 kB]
Ign:56 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial Release                        
Ign:26 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main DEP-11 64x64 Icons
Get:57 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [93.8 kB]
Ign:58 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main Translation-en.diff/Index
Ign:59 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Translation-en_ZA
0% [30 InRelease gpgv 0 B] [55 Components-amd64 49.7 kB/326 kB 15%] [57 ComponeSplitting up /var/lib/apt/lists/ppa.launchpad.net_octave_stable_ubuntu_dists_xeniErr:30 [http://ppa.launchpad.net/octave/stable/ubuntu](http://ppa.launchpad.net/octave/stable/ubuntu) xenial InRelease          
  Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)
Ign:28 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main amd64 Packages 
Err:33 [https://cloud.r-project.org/bin/linux/ubuntu](https://cloud.r-project.org/bin/linux/ubuntu) xenial-cran35/ InRelease   
  The following signatures were invalid: KEYEXPIRED 1602869253  KEYEXPIRED 1602869253  KEYEXPIRED 1602869253
Ign:60 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Translation-en_ZA          
Err:38 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease                             
  The following signatures were invalid: KEYEXPIRED 1624268195  KEYEXPIRED 1624268195  KEYEXPIRED 1624268195
Ign:61 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:29 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main i386 Packages  
0% [42 InRelease gpgv 0 B] [55 Components-amd64 237 kB/326 kB 73%] [57 ComponenSplitting up /var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_xErr:42 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial InRelease       
  Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)
Err:15 [https://cran.wustl.edu/bin/linux/ubuntu](https://cran.wustl.edu/bin/linux/ubuntu) xenial/ InRelease               
  The following signatures were invalid: KEYEXPIRED 1602869253  KEYEXPIRED 1602869253  KEYEXPIRED 1602869253
Err:47 [https://packages.gitlab.com/gitlab/gitlab-ee/ubuntu](https://packages.gitlab.com/gitlab/gitlab-ee/ubuntu) xenial InRelease    
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F01618A51312F3F
Ign:19 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main all Packages   
Ign:62 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main DEP-11 64x64 Icons
Get:63 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [281 kB]
Get:64 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [130 kB]
Ign:65 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe amd64 Packages.diff/Index
Ign:21 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main Translation-en_ZA
Ign:66 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Translation-en
Ign:23 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main Translation-en 
Ign:67 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main amd64 Packages.diff/Index
Get:68 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5,964 B]
Ign:24 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main amd64 DEP-11 Metadata
Get:69 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Ign:70 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main i386 Packages.diff/Index
Ign:71 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Translation-en             
Get:72 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:73 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [6,596 B]
Ign:26 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main DEP-11 64x64 Icons
Ign:74 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main all Packages
Ign:28 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main amd64 Packages 
Ign:75 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe i386 Packages         
Ign:76 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Packages
Ign:29 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main i386 Packages
Ign:77 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main Translation-en_ZA
Ign:19 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main all Packages   
Ign:21 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main Translation-en_ZA
Ign:78 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main Translation-en.diff/Index
Ign:79 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Packages                   
Ign:80 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe all Packages          
Ign:59 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Translation-en_ZA
Ign:81 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:23 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main Translation-en 
Ign:24 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main amd64 DEP-11 Metadata
Ign:82 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:26 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main DEP-11 64x64 Icons
Ign:83 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main amd64 Packages
Err:28 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main amd64 Packages 
  404  Not Found [IP: 87.238.57.227 80]
Ign:66 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Translation-en
Ign:84 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe Translation-en_ZA     
Ign:60 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Translation-en_ZA       
Ign:29 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) xenial-pgdg/main i386 Packages
Ign:85 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main i386 Packages
Ign:86 [http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu](http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:76 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Packages
Ign:87 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe Translation-en        
Ign:88 [http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu](http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:71 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Translation-en             
Ign:53 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main all Packages
Ign:54 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main Translation-en_ZA
Ign:59 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Translation-en_ZA
Ign:89 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe amd64 DEP-11 Metadata 
Ign:90 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main Translation-en
Ign:79 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Packages                   
Ign:61 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:66 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Translation-en
Ign:62 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:91 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe DEP-11 64x64 Icons    
Ign:92 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main amd64 Packages
Ign:60 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Translation-en_ZA          
Ign:93 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main i386 Packages
Ign:76 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Packages
Ign:74 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main all Packages
Ign:94 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe amd64 Packages.diff/Index
Ign:77 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main Translation-en_ZA
Ign:71 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Translation-en             
Ign:59 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Translation-en_ZA
Ign:95 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main Translation-en
Ign:96 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe i386 Packages.diff/Index
Ign:81 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:82 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:66 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Translation-en
Ign:83 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main amd64 Packages
Ign:79 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Packages                   
Ign:97 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe all Packages          
Ign:85 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main i386 Packages
Ign:86 [http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu](http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:76 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Packages
Ign:88 [http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu](http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:98 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe Translation-en_ZA     
Ign:60 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Translation-en_ZA          
Ign:53 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main all Packages
Ign:59 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Translation-en_ZA
Ign:54 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main Translation-en_ZA
Ign:99 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe Translation-en        
Ign:90 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main Translation-en
Ign:71 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Translation-en             
Ign:61 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:66 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Translation-en
Ign:62 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:100 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe amd64 DEP-11 Metadata
Ign:92 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main amd64 Packages
Ign:79 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Packages
Ign:93 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main i386 Packages
Ign:76 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Packages
Ign:74 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main all Packages
Ign:101 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe DEP-11 64x64 Icons
Ign:77 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main Translation-en_ZA
Ign:59 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Translation-en_ZA
Ign:60 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Translation-en_ZA
Ign:95 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main Translation-en
Ign:102 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe amd64 Packages
Ign:81 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:82 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:66 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Translation-en
Ign:71 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Translation-en
Ign:83 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main amd64 Packages
Ign:75 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe i386 Packages
Ign:85 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main i386 Packages
Err:76 [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04)  Packages
  server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
Ign:86 [http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu](http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:80 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe all Packages
Err:88 [http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu](http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu) xenial/main DEP-11 64x64 Icons
  404  Not Found [IP: 185.125.190.52 80]
Ign:79 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Packages
Ign:53 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main all Packages
Ign:54 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main Translation-en_ZA
Ign:84 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe Translation-en_ZA
Ign:90 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main Translation-en
Ign:60 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Translation-en_ZA
Ign:61 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:87 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe Translation-en
Ign:62 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:92 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main amd64 Packages
Ign:71 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Translation-en
Ign:93 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main i386 Packages
Ign:89 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe amd64 DEP-11 Metadata
Ign:74 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main all Packages
Ign:77 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main Translation-en_ZA
Err:79 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ Packages
  server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
Ign:95 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main Translation-en
Ign:91 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe DEP-11 64x64 Icons
Ign:81 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:82 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:83 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main amd64 Packages
Ign:103 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe amd64 Packages
Ign:85 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main i386 Packages
Ign:53 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main all Packages
Ign:104 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe i386 Packages
Ign:54 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main Translation-en_ZA
Ign:90 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main Translation-en
Ign:61 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:97 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe all Packages
Ign:62 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:92 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main amd64 Packages
Ign:93 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main i386 Packages
Ign:98 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe Translation-en_ZA
Ign:74 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main all Packages
Ign:77 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main Translation-en_ZA
Ign:99 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe Translation-en
Ign:95 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main Translation-en
Ign:81 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:82 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:100 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe amd64 DEP-11 Metadata
Ign:83 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main amd64 Packages
Ign:85 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main i386 Packages
Ign:53 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main all Packages
Ign:101 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe DEP-11 64x64 Icons
Ign:54 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main Translation-en_ZA
Ign:90 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main Translation-en
Ign:102 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe amd64 Packages
Ign:61 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:62 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:92 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main amd64 Packages
Ign:75 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe i386 Packages
Ign:93 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main i386 Packages
Ign:74 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main all Packages
Ign:77 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main Translation-en_ZA
Ign:80 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe all Packages
Ign:95 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main Translation-en
Ign:81 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:84 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe Translation-en_ZA
Ign:82 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main DEP-11 64x64 Icons
Err:83 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main amd64 Packages
  403  Forbidden [IP: 185.125.190.52 80]
Ign:85 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main i386 Packages
Ign:87 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe Translation-en
Ign:90 [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) xenial/main Translation-en
Err:92 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main amd64 Packages
  403  Forbidden [IP: 185.125.190.52 80]
Ign:89 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe amd64 DEP-11 Metadata
Ign:93 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main i386 Packages
Ign:95 [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu) xenial/main Translation-en
Ign:91 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe DEP-11 64x64 Icons
Ign:103 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe amd64 Packages
Ign:104 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe i386 Packages
Ign:97 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe all Packages
Ign:98 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe Translation-en_ZA
Ign:99 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe Translation-en
Ign:100 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe amd64 DEP-11 Metadata
Ign:101 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe DEP-11 64x64 Icons
Ign:102 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe amd64 Packages
Ign:75 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe i386 Packages
Ign:80 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe all Packages
Ign:84 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe Translation-en_ZA
Ign:87 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe Translation-en
Ign:89 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe amd64 DEP-11 Metadata
Ign:91 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe DEP-11 64x64 Icons
Ign:103 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe amd64 Packages
Ign:104 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe i386 Packages
Ign:97 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe all Packages
Ign:98 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe Translation-en_ZA
Ign:99 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe Translation-en
Ign:100 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe amd64 DEP-11 Metadata
Ign:101 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe DEP-11 64x64 Icons
Ign:102 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe amd64 Packages
Ign:75 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe i386 Packages
Ign:80 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe all Packages
Ign:84 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe Translation-en_ZA
Ign:87 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe Translation-en
Ign:89 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe amd64 DEP-11 Metadata
Ign:91 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe DEP-11 64x64 Icons
Ign:103 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe amd64 Packages
Ign:104 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe i386 Packages
Ign:97 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe all Packages
Ign:98 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe Translation-en_ZA
Ign:99 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe Translation-en
Ign:100 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe amd64 DEP-11 Metadata
Ign:101 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe DEP-11 64x64 Icons
Ign:102 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe amd64 Packages
Err:75 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe i386 Packages
  server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
Ign:80 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe all Packages
Ign:84 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe Translation-en_ZA
Ign:87 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe Translation-en
Ign:89 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe amd64 DEP-11 Metadata
Ign:91 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) bionic/universe DEP-11 64x64 Icons
Ign:103 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe amd64 Packages
Ign:104 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe i386 Packages
Ign:97 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe all Packages
Ign:98 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe Translation-en_ZA
Ign:99 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe Translation-en
Ign:100 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe amd64 DEP-11 Metadata
Ign:101 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe DEP-11 64x64 Icons
Err:103 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe amd64 Packages
  server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
Ign:104 [https://repos.codelite.org/ubuntu](https://repos.codelite.org/ubuntu) xenial/universe i386 Packages
Fetched 1,226 kB in 1min 50s (11.0 kB/s)
Reading package lists... Done
W: The repository 'http://apt.postgresql.org/pub/repos/apt xenial-pgdg Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4EB27DB2A3B88B8B
W: The repository 'http://dl.google.com/linux/chrome/deb stable InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04  Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'https://download.sublimetext.com apt/stable/ Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://cran.rstudio.com/bin/linux/ubuntu](http://cran.rstudio.com/bin/linux/ubuntu) xenial/ InRelease: The following signatures were invalid: KEYEXPIRED 1602869253  KEYEXPIRED 1602869253  KEYEXPIRED 1602869253
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://repo.mysql.com/apt/ubuntu](http://repo.mysql.com/apt/ubuntu) xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 467B942D3A79BD29
W: The repository 'https://repos.codelite.org/ubuntu bionic Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://cran.mirror.ac.za//bin/linux/ubuntu](http://cran.mirror.ac.za//bin/linux/ubuntu) xenial/ InRelease: The following signatures were invalid: KEYEXPIRED 1602869253  KEYEXPIRED 1602869253  KEYEXPIRED 1602869253
W: The repository 'https://repos.codelite.org/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net/octave/stable/ubuntu](http://ppa.launchpad.net/octave/stable/ubuntu) xenial InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://cloud.r-project.org/bin/linux/ubuntu](https://cloud.r-project.org/bin/linux/ubuntu) xenial-cran35/ InRelease: The following signatures were invalid: KEYEXPIRED 1602869253  KEYEXPIRED 1602869253  KEYEXPIRED 1602869253
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease: The following signatures were invalid: KEYEXPIRED 1624268195  KEYEXPIRED 1624268195  KEYEXPIRED 1624268195
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://cran.wustl.edu/bin/linux/ubuntu](https://cran.wustl.edu/bin/linux/ubuntu) xenial/ InRelease: The following signatures were invalid: KEYEXPIRED 1602869253  KEYEXPIRED 1602869253  KEYEXPIRED 1602869253
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://packages.gitlab.com/gitlab/gitlab-ee/ubuntu](https://packages.gitlab.com/gitlab/gitlab-ee/ubuntu) xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F01618A51312F3F
W: Failed to fetch [http://cran.rstudio.com/bin/linux/ubuntu/xenial/InRelease](http://cran.rstudio.com/bin/linux/ubuntu/xenial/InRelease)  The following signatures were invalid: KEYEXPIRED 1602869253  KEYEXPIRED 1602869253  KEYEXPIRED 1602869253
W: Failed to fetch [http://cran.wustl.edu/bin/linux/ubuntu/xenial/InRelease](http://cran.wustl.edu/bin/linux/ubuntu/xenial/InRelease)  The following signatures were invalid: KEYEXPIRED 1602869253  KEYEXPIRED 1602869253  KEYEXPIRED 1602869253
W: Failed to fetch [http://cran.mirror.ac.za//bin/linux/ubuntu/xenial/InRelease](http://cran.mirror.ac.za//bin/linux/ubuntu/xenial/InRelease)  The following signatures were invalid: KEYEXPIRED 1602869253  KEYEXPIRED 1602869253  KEYEXPIRED 1602869253
W: Failed to fetch [https://cloud.r-project.org/bin/linux/ubuntu/xenial-cran35/InRelease](https://cloud.r-project.org/bin/linux/ubuntu/xenial-cran35/InRelease)  The following signatures were invalid: KEYEXPIRED 1602869253  KEYEXPIRED 1602869253  KEYEXPIRED 1602869253
W: Failed to fetch [https://packages.gitlab.com/gitlab/gitlab-ee/ubuntu/dists/xenial/InRelease](https://packages.gitlab.com/gitlab/gitlab-ee/ubuntu/dists/xenial/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F01618A51312F3F
W: Failed to fetch [http://repo.mysql.com/apt/ubuntu/dists/xenial/InRelease](http://repo.mysql.com/apt/ubuntu/dists/xenial/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 467B942D3A79BD29
E: Failed to fetch [http://debian.neo4j.org/repo/stable/InRelease](http://debian.neo4j.org/repo/stable/InRelease)  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
W: Failed to fetch [http://ppa.launchpad.net/octave/stable/ubuntu/dists/xenial/InRelease](http://ppa.launchpad.net/octave/stable/ubuntu/dists/xenial/InRelease)  Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)
W: Failed to fetch [https://repo.skype.com/deb/dists/stable/InRelease](https://repo.skype.com/deb/dists/stable/InRelease)  The following signatures were invalid: KEYEXPIRED 1624268195  KEYEXPIRED 1624268195  KEYEXPIRED 1624268195
W: Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/xenial/InRelease](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/xenial/InRelease)  Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)
E: Failed to fetch [http://apt.postgresql.org/pub/repos/apt/dists/xenial-pgdg/main/binary-amd64/Packages](http://apt.postgresql.org/pub/repos/apt/dists/xenial-pgdg/main/binary-amd64/Packages)  404  Not Found [IP: 87.238.57.227 80]
E: Failed to fetch [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu/dists/xenial/main/binary-amd64/Packages)  403  Forbidden [IP: 185.125.190.52 80]
E: Failed to fetch [http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu/dists/xenial/main/dep11/icons-64x64.tar](http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu/dists/xenial/main/dep11/icons-64x64.tar)  404  Not Found [IP: 185.125.190.52 80]
E: Failed to fetch [https://repos.codelite.org/ubuntu/dists/bionic/universe/binary-i386/Packages](https://repos.codelite.org/ubuntu/dists/bionic/universe/binary-i386/Packages)  server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
E: Failed to fetch [https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04/Packages](https://download.opensuse.org/repositories/home:/kamilprusko/xUbuntu_16.04/Packages)  server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
E: Failed to fetch [https://download.sublimetext.com/apt/stable/Packages](https://download.sublimetext.com/apt/stable/Packages)  server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
E: Failed to fetch [http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/jonathonf/texlive-2017/ubuntu/dists/xenial/main/binary-amd64/Packages)  403  Forbidden [IP: 185.125.190.52 80]
E: Failed to fetch [https://repos.codelite.org/ubuntu/dists/xenial/universe/binary-amd64/Packages](https://repos.codelite.org/ubuntu/dists/xenial/universe/binary-amd64/Packages)  server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
W: Some index files failed to download. They have been ignored, or old ones used instead.
E: The package lists or status file could not be parsed or opened.

```

---

### Post by guiverc on 2023-06-24
You have loads of 3rd party sources, and your system feels *unmaintained* to me given what I see, so I'd likely backup your system, **clean** install then restore data from backups (*reinstalling the apps you need as required*).

As stated in prior comment, I *somewhat *recently (*earlier this year*) performed a *xenial* (16.04) upgrade to *bionic *(18.04), which I'd planned to instead perform a *upgrade via re-install* myself as this is faster/easier & allowed me to *jump* to 22.04 quickly, but I noted loads of people having issues with the 16.04 to 18.04 upgrade due to *expired certificates* which made me try the slower/normal *release-upgrade*, where I had no issues at all. Of course my (*geo*) location in the world varies thus have different certificate expiry dates which can impact ease, but attempts have been made to minimize this with *release-upgrades*. You've got the added difficulty of leaving it too late (*though [meta]("https://changelogs.ubuntu.com/meta-release") still shows bionic supported due to ESM*).

Your alternative is the ***unclean*** (or *upgrade via re-install*) I already mentioned, which is just re-use of existing partition(s) without format, the lack of format triggers the *repair installation* type of install for desktop installers (`ubiquity` and `calamares`; `ubuntu-desktop-installer` can do it too now though I've had some mixed results with it & ease varies on release; I find it easier with *flavors* as they have 'universe' enabled by default). How well this will go will depend on what package(s) you have installed, and given the *unmaintained feel* I get looking at the error message, I suspect you'll do better with a ***clean ***install then restore of data given you may not be able to assess consequences for your installed/used package(s) considering the *'jump'* you'll be making via re-install of a later release (*this can have issues on a program/package basis if data integrity matters to you & is system (not release) specific*).

If you're not capable of resolving the issues in your paste, I'd more strongly suggest you backup data & re-install to achieve your aim.  By delaying you've only made it more complex.

---

