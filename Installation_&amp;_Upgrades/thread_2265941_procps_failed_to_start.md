---
title: "procps failed to start"
date: 2015-02-18
forum: Installation &amp; Upgrades
---

### Post by unix084 on 2015-02-18
After an apt-get update && apt-get upgrade on my VPS  (Ubuntu 12.04.5 LTS -  3.13.0-32-generic x86_64) I'm facing this:

```

Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release
Hit http://ppa.launchpad.net precise Release
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Hit http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Hit http://mirrors.digitalocean.com precise Release.gpg
Hit http://mirrors.digitalocean.com precise-updates Release.gpg
Hit http://mirrors.digitalocean.com precise-backports Release.gpg
Hit http://mirrors.digitalocean.com precise-security Release.gpg
Hit http://mirrors.digitalocean.com precise Release
Hit http://mirrors.digitalocean.com precise-updates Release
Hit http://mirrors.digitalocean.com precise-backports Release
Hit http://mirrors.digitalocean.com precise-security Release
Hit http://mirrors.digitalocean.com precise/main Sources
Hit http://mirrors.digitalocean.com precise/restricted Sources
Hit http://mirrors.digitalocean.com precise/universe Sources
Hit http://mirrors.digitalocean.com precise/multiverse Sources
Hit http://mirrors.digitalocean.com precise/main amd64 Packages
Hit http://mirrors.digitalocean.com precise/restricted amd64 Packages
Hit http://mirrors.digitalocean.com precise/universe amd64 Packages
Hit http://mirrors.digitalocean.com precise/multiverse amd64 Packages
Hit http://mirrors.digitalocean.com precise/main i386 Packages
Hit http://mirrors.digitalocean.com precise/restricted i386 Packages
Hit http://mirrors.digitalocean.com precise/universe i386 Packages
Hit http://mirrors.digitalocean.com precise/multiverse i386 Packages
Hit http://mirrors.digitalocean.com precise/main TranslationIndex
Hit http://mirrors.digitalocean.com precise/multiverse TranslationIndex
Hit http://mirrors.digitalocean.com precise/restricted TranslationIndex
Hit http://mirrors.digitalocean.com precise/universe TranslationIndex
Hit http://mirrors.digitalocean.com precise-updates/main Sources
Hit http://mirrors.digitalocean.com precise-updates/restricted Sources
Hit http://mirrors.digitalocean.com precise-updates/universe Sources
Hit http://mirrors.digitalocean.com precise-updates/multiverse Sources
Hit http://mirrors.digitalocean.com precise-updates/main amd64 Packages
Hit http://mirrors.digitalocean.com precise-updates/restricted amd64 Packages
Hit http://mirrors.digitalocean.com precise-updates/universe amd64 Packages
Hit http://mirrors.digitalocean.com precise-updates/multiverse amd64 Packages
Hit http://mirrors.digitalocean.com precise-updates/main i386 Packages
Hit http://mirrors.digitalocean.com precise-updates/restricted i386 Packages
Hit http://mirrors.digitalocean.com precise-updates/universe i386 Packages
Hit http://mirrors.digitalocean.com precise-updates/multiverse i386 Packages
Hit http://mirrors.digitalocean.com precise-updates/main TranslationIndex
Hit http://mirrors.digitalocean.com precise-updates/multiverse TranslationIndex
Hit http://mirrors.digitalocean.com precise-updates/restricted TranslationIndex
Hit http://mirrors.digitalocean.com precise-updates/universe TranslationIndex
Hit http://mirrors.digitalocean.com precise-backports/main Sources
Hit http://mirrors.digitalocean.com precise-backports/restricted Sources
Hit http://mirrors.digitalocean.com precise-backports/universe Sources
Hit http://mirrors.digitalocean.com precise-backports/multiverse Sources
Hit http://mirrors.digitalocean.com precise-backports/main amd64 Packages
Hit http://mirrors.digitalocean.com precise-backports/restricted amd64 Packages
Hit http://mirrors.digitalocean.com precise-backports/universe amd64 Packages
Hit http://mirrors.digitalocean.com precise-backports/multiverse amd64 Packages
Hit http://mirrors.digitalocean.com precise-backports/main i386 Packages
Hit http://mirrors.digitalocean.com precise-backports/restricted i386 Packages
Hit http://mirrors.digitalocean.com precise-backports/universe i386 Packages
Hit http://mirrors.digitalocean.com precise-backports/multiverse i386 Packages
Hit http://mirrors.digitalocean.com precise-backports/main TranslationIndex
Hit http://mirrors.digitalocean.com precise-backports/multiverse TranslationIndex
Hit http://mirrors.digitalocean.com precise-backports/restricted TranslationIndex
Hit http://mirrors.digitalocean.com precise-backports/universe TranslationIndex
Hit http://mirrors.digitalocean.com precise-security/main Sources
Hit http://mirrors.digitalocean.com precise-security/restricted Sources
Hit http://mirrors.digitalocean.com precise-security/universe Sources
Hit http://mirrors.digitalocean.com precise-security/multiverse Sources
Hit http://mirrors.digitalocean.com precise-security/main amd64 Packages
Hit http://mirrors.digitalocean.com precise-security/restricted amd64 Packages
Hit http://mirrors.digitalocean.com precise-security/universe amd64 Packages
Hit http://mirrors.digitalocean.com precise-security/multiverse amd64 Packages
Hit http://mirrors.digitalocean.com precise-security/main i386 Packages
Hit http://mirrors.digitalocean.com precise-security/restricted i386 Packages
Hit http://mirrors.digitalocean.com precise-security/universe i386 Packages
Hit http://mirrors.digitalocean.com precise-security/multiverse i386 Packages
Hit http://mirrors.digitalocean.com precise-security/main TranslationIndex
Hit http://mirrors.digitalocean.com precise-security/multiverse TranslationIndex
Hit http://mirrors.digitalocean.com precise-security/restricted TranslationIndex
Hit http://mirrors.digitalocean.com precise-security/universe TranslationIndex
Hit http://mirrors.digitalocean.com precise/main Translation-en
Hit http://mirrors.digitalocean.com precise/multiverse Translation-en
Hit http://mirrors.digitalocean.com precise/restricted Translation-en
Hit http://mirrors.digitalocean.com precise/universe Translation-en
Hit http://mirrors.digitalocean.com precise-updates/main Translation-en
Hit http://mirrors.digitalocean.com precise-updates/multiverse Translation-en
Hit http://mirrors.digitalocean.com precise-updates/restricted Translation-en
Hit http://mirrors.digitalocean.com precise-updates/universe Translation-en
Hit http://mirrors.digitalocean.com precise-backports/main Translation-en
Hit http://mirrors.digitalocean.com precise-backports/multiverse Translation-en
Hit http://mirrors.digitalocean.com precise-backports/restricted Translation-en
Hit http://mirrors.digitalocean.com precise-backports/universe Translation-en
Hit http://mirrors.digitalocean.com precise-security/main Translation-en
Hit http://mirrors.digitalocean.com precise-security/multiverse Translation-en
Hit http://mirrors.digitalocean.com precise-security/restricted Translation-en
Hit http://mirrors.digitalocean.com precise-security/universe Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up procps (1:3.2.8-11ubuntu6.4) ...
start: Job failed to start
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mountall:
 mountall depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing mountall (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 procps
 udev
 mountall
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I need some help here. Please be patient with me as I'm a newbie and in a learning process. Thank you!

---

