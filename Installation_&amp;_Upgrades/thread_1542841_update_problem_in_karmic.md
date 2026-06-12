---
title: "update problem in karmic"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by mirinamulhaq on 2010-07-31
[SIZE=3]**i had recently some problem with my dual boot(windows 7 and ubuntu karmic),then i reinstalled ubuntu.now as i am trying to update the system through terminal i am always getting this error**[/SIZE]
inam@inam-laptop:~$ sudo apt-get update
Err [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
  Could not connect to archive.canonical.com:80 (91.189.88.33), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_IN              
  Unable to connect to archive.canonical.com http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
  Could not connect to ppa.launchpad.net:80 (91.189.90.217), connection timed out
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_IN                     
  Unable to connect to ppa.launchpad.net http:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg     
  Could not connect to archive.ubuntu.com:80 (91.189.88.31), connection timed out [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_IN
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_IN
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_IN
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_IN
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_IN
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_IN
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_IN
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_IN
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_IN
  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.31), connection timed out [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_IN.bz2)  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_IN.bz2)  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_IN.bz2)  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_IN.bz2)  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg](http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.88.33), connection timed out

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_IN.bz2](http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_IN.bz2)  Unable to connect to archive.canonical.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_IN.bz2)  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_IN.bz2)  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]

W: Failed to fetch [http://ppa.launchpad.net/c-korn/ppa/ubuntu/dists/karmic/Release.gpg](http://ppa.launchpad.net/c-korn/ppa/ubuntu/dists/karmic/Release.gpg)  Could not connect to ppa.launchpad.net:80 (91.189.90.217), connection timed out

W: Failed to fetch [http://ppa.launchpad.net/c-korn/ppa/ubuntu/dists/karmic/main/i18n/Translation-en_IN.bz2](http://ppa.launchpad.net/c-korn/ppa/ubuntu/dists/karmic/main/i18n/Translation-en_IN.bz2)  Unable to connect to ppa.launchpad.net http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
inam@inam-laptop:~$ 
[SIZE=3]**although my browser is working fine and i am able to open archive.ubuntu.com through my browser.**[/SIZE]
the out put of few other commands is as follows
inam@inam-laptop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
inam@inam-laptop:~$ sudo bash
[sudo] password for inam: 
root@inam-laptop:~# /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
root@inam-laptop:~# cat/etc/apt/sources.list
bash: cat/etc/apt/sources.list: No such file or directory
root@inam-laptop:~# gpg --list-keys
gpg: WARNING: unsafe ownership on configuration file `/home/inam/.gnupg/gpg.conf'
root@inam-laptop:~# 
**[SIZE=3][COLOR=Red]can any one help me in this matter[/COLOR][/SIZE]**

---

