---
title: "ubuntu 12.10 (64bits) unable to install i386 libs"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by odror on 2012-11-13
When trying to install steam (dpkg -i steam.deb)

I get the following errors> Selecting previously unselected package steam.
(Reading database ... 457010 files and directories currently installed.)
Unpacking steam (from ./steam.deb) ...
dpkg: dependency problems prevent configuration of steam:
 steam depends on libcairo2 (>= 1.6.0); however:
  Package libcairo2:i386 is not installed.
 steam depends on libgtk2.0-0 (>= 2.24.0); however:
 steam depends on libpango1.0-0 (>= 1.22.0); however:


When I try to install libcairo2:i386 ( apt-get install libcairo2:i386) > Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libatk-wrapper-java-jni : Depends: libgtk2.0-0 (>= 2.12.0) but it is not going to be installed
                           Depends: libatk-wrapper-java (>= 0.30.4-0ubuntu4) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

I have similar issues when installing wine > Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4.1-0ubuntu1)
E: Unable to correct problems, you have held broken packages.
Is there a workaround to fix this problem

Thanks

---

### Post by jerome1232 on 2012-11-13
Sounds like it's complaining about a package you've pinned to me, check for any held packages

```
apt-cache policy
```

Scroll through the output and look for a section called "Pinned packages" is anything there?

---

### Post by odror on 2012-11-13
> **jerome1232 said:**
> Sounds like it's complaining about a package you've pinned to me, check for any held packages

```
apt-cache policy
```

Scroll through the output and look for a section called "Pinned packages" is anything there?

I get the following :> Package files:
 100 /var/lib/dpkg/status
     release a=now
 500 [http://ppa.launchpad.net/upubuntu-com/themes/ubuntu/](http://ppa.launchpad.net/upubuntu-com/themes/ubuntu/) quantal/main i386 Packages
     release v=12.10,o=LP-PPA-upubuntu-com-themes,a=quantal,n=quantal,l=Ubuntu GTK3/GTK2 Themes & Icons,c=main
     origin ppa.launchpad.net
 500 [http://ppa.launchpad.net/upubuntu-com/themes/ubuntu/](http://ppa.launchpad.net/upubuntu-com/themes/ubuntu/) quantal/main amd64 Packages
     release v=12.10,o=LP-PPA-upubuntu-com-themes,a=quantal,n=quantal,l=Ubuntu GTK3/GTK2 Themes & Icons,c=main
     origin ppa.launchpad.net
 500 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) quantal/main i386 Packages
     release v=12.10,o=LP-PPA-tualatrix,a=quantal,n=quantal,l=Ubuntu Tweak Stable PPA,c=main
     origin ppa.launchpad.net
 500 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) quantal/main amd64 Packages
     release v=12.10,o=LP-PPA-tualatrix,a=quantal,n=quantal,l=Ubuntu Tweak Stable PPA,c=main
     origin ppa.launchpad.net
 500 [http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu/](http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu/) quantal/main i386 Packages
     release v=12.10,o=LP-PPA-nvbn-rm,a=quantal,n=quantal,l=PPA,c=main
     origin ppa.launchpad.net
 500 [http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu/](http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu/) quantal/main amd64 Packages
     release v=12.10,o=LP-PPA-nvbn-rm,a=quantal,n=quantal,l=PPA,c=main
     origin ppa.launchpad.net
 500 [http://ppa.launchpad.net/mythbuntu/0.26/ubuntu/](http://ppa.launchpad.net/mythbuntu/0.26/ubuntu/) quantal/main i386 Packages
     release v=12.10,o=LP-PPA-mythbuntu-0.26,a=quantal,n=quantal,l=0.26,c=main
     origin ppa.launchpad.net
 500 [http://ppa.launchpad.net/mythbuntu/0.26/ubuntu/](http://ppa.launchpad.net/mythbuntu/0.26/ubuntu/) quantal/main amd64 Packages
     release v=12.10,o=LP-PPA-mythbuntu-0.26,a=quantal,n=quantal,l=0.26,c=main
     origin ppa.launchpad.net
 500 [http://ppa.launchpad.net/markjtully/ppa/ubuntu/](http://ppa.launchpad.net/markjtully/ppa/ubuntu/) quantal/main i386 Packages
     release v=12.10,o=LP-PPA-markjtully,a=quantal,n=quantal,l=PPA for Teester,c=main
     origin ppa.launchpad.net
 500 [http://ppa.launchpad.net/markjtully/ppa/ubuntu/](http://ppa.launchpad.net/markjtully/ppa/ubuntu/) quantal/main amd64 Packages
     release v=12.10,o=LP-PPA-markjtully,a=quantal,n=quantal,l=PPA for Teester,c=main
     origin ppa.launchpad.net
 500 [http://ppa.launchpad.net/jconti/recent-notifications/ubuntu/](http://ppa.launchpad.net/jconti/recent-notifications/ubuntu/) quantal/main i386 Packages
     release v=12.10,o=LP-PPA-jconti-recent-notifications,a=quantal,n=quantal,l=Recent Notifications,c=main
     origin ppa.launchpad.net
 500 [http://ppa.launchpad.net/jconti/recent-notifications/ubuntu/](http://ppa.launchpad.net/jconti/recent-notifications/ubuntu/) quantal/main amd64 Packages
     release v=12.10,o=LP-PPA-jconti-recent-notifications,a=quantal,n=quantal,l=Recent Notifications,c=main
     origin ppa.launchpad.net
 500 [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages
     release v=1.0,o=Google, Inc.,a=stable,n=stable,l=Google,c=main
     origin dl.google.com
 500 [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages
     release v=1.0,o=Google, Inc.,a=stable,n=stable,l=Google,c=main
     origin dl.google.com
 500 [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) precise/main i386 Packages
     release o=Dropbox.com,a=precise,n=precise,l=Dropbox Ubuntu Repository,c=main
     origin linux.dropbox.com
 500 [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) precise/main amd64 Packages
     release o=Dropbox.com,a=precise,n=precise,l=Dropbox Ubuntu Repository,c=main
     origin linux.dropbox.com
 500 [http://ppa.launchpad.net/atareao/atareao/ubuntu/](http://ppa.launchpad.net/atareao/atareao/ubuntu/) quantal/main i386 Packages
     release v=12.10,o=LP-PPA-atareao-atareao,a=quantal,n=quantal,l=atareao-team,c=main
     origin ppa.launchpad.net
 500 [http://ppa.launchpad.net/atareao/atareao/ubuntu/](http://ppa.launchpad.net/atareao/atareao/ubuntu/) quantal/main amd64 Packages
     release v=12.10,o=LP-PPA-atareao-atareao,a=quantal,n=quantal,l=atareao-team,c=main
     origin ppa.launchpad.net
 500 [http://ppa.launchpad.net/alexmurray/indicator-sensors/ubuntu/](http://ppa.launchpad.net/alexmurray/indicator-sensors/ubuntu/) quantal/main i386 Packages
     release v=12.10,o=LP-PPA-alexmurray-indicator-sensors,a=quantal,n=quantal,l=PPA for indicator-sensors,c=main
     origin ppa.launchpad.net
 500 [http://ppa.launchpad.net/alexmurray/indicator-sensors/ubuntu/](http://ppa.launchpad.net/alexmurray/indicator-sensors/ubuntu/) quantal/main amd64 Packages
     release v=12.10,o=LP-PPA-alexmurray-indicator-sensors,a=quantal,n=quantal,l=PPA for indicator-sensors,c=main
     origin ppa.launchpad.net
 500 [http://repository.spotify.com/](http://repository.spotify.com/) stable/non-free i386 Packages
     release v=0.4,o=Spotify LTD,a=stable,n=stable,l=Spotify Public Repository,c=non-free
     origin repository.spotify.com
 500 [http://repository.spotify.com/](http://repository.spotify.com/) stable/non-free amd64 Packages
     release v=0.4,o=Spotify LTD,a=stable,n=stable,l=Spotify Public Repository,c=non-free
     origin repository.spotify.com
 500 [http://archive.canonical.com/](http://archive.canonical.com/) quantal/partner i386 Packages
     release v=12.10,o=Canonical,a=quantal,n=quantal,l=Partner archive,c=partner
     origin archive.canonical.com
 500 [http://archive.canonical.com/](http://archive.canonical.com/) quantal/partner amd64 Packages
     release v=12.10,o=Canonical,a=quantal,n=quantal,l=Partner archive,c=partner
     origin archive.canonical.com
 500 [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) quantal/main i386 Packages
     release v=12.10,o=LP-PPA-app-review-board,a=quantal,n=quantal,l=Application Review Board PPA,c=main
     origin extras.ubuntu.com
 500 [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) quantal/main amd64 Packages
     release v=12.10,o=LP-PPA-app-review-board,a=quantal,n=quantal,l=Application Review Board PPA,c=main
     origin extras.ubuntu.com
 500 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) quantal/partner i386 Packages
     release v=12.10,o=Canonical,a=quantal,n=quantal,l=Partner archive,c=partner
     origin archive.canonical.com
 500 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) quantal/partner amd64 Packages
     release v=12.10,o=Canonical,a=quantal,n=quantal,l=Partner archive,c=partner
     origin archive.canonical.com
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/universe Translation-en
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/restricted Translation-en
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/multiverse Translation-en
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/main Translation-en
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/multiverse i386 Packages
     release v=12.10,o=Ubuntu,a=quantal-security,n=quantal,l=Ubuntu,c=multiverse
     origin security.ubuntu.com
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/universe i386 Packages
     release v=12.10,o=Ubuntu,a=quantal-security,n=quantal,l=Ubuntu,c=universe
     origin security.ubuntu.com
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/restricted i386 Packages
     release v=12.10,o=Ubuntu,a=quantal-security,n=quantal,l=Ubuntu,c=restricted
     origin security.ubuntu.com
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/main i386 Packages
     release v=12.10,o=Ubuntu,a=quantal-security,n=quantal,l=Ubuntu,c=main
     origin security.ubuntu.com
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/multiverse amd64 Packages
     release v=12.10,o=Ubuntu,a=quantal-security,n=quantal,l=Ubuntu,c=multiverse
     origin security.ubuntu.com
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/universe amd64 Packages
     release v=12.10,o=Ubuntu,a=quantal-security,n=quantal,l=Ubuntu,c=universe
     origin security.ubuntu.com
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/restricted amd64 Packages
     release v=12.10,o=Ubuntu,a=quantal-security,n=quantal,l=Ubuntu,c=restricted
     origin security.ubuntu.com
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/main amd64 Packages
     release v=12.10,o=Ubuntu,a=quantal-security,n=quantal,l=Ubuntu,c=main
     origin security.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports/universe Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports/restricted Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports/multiverse Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports/main Translation-en
 100 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports/multiverse i386 Packages
     release v=12.10,o=Ubuntu,a=quantal-backports,n=quantal,l=Ubuntu,c=multiverse
     origin us.archive.ubuntu.com
 100 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports/universe i386 Packages
     release v=12.10,o=Ubuntu,a=quantal-backports,n=quantal,l=Ubuntu,c=universe
     origin us.archive.ubuntu.com
 100 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports/restricted i386 Packages
     release v=12.10,o=Ubuntu,a=quantal-backports,n=quantal,l=Ubuntu,c=restricted
     origin us.archive.ubuntu.com
 100 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports/main i386 Packages
     release v=12.10,o=Ubuntu,a=quantal-backports,n=quantal,l=Ubuntu,c=main
     origin us.archive.ubuntu.com
 100 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports/multiverse amd64 Packages
     release v=12.10,o=Ubuntu,a=quantal-backports,n=quantal,l=Ubuntu,c=multiverse
     origin us.archive.ubuntu.com
 100 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports/universe amd64 Packages
     release v=12.10,o=Ubuntu,a=quantal-backports,n=quantal,l=Ubuntu,c=universe
     origin us.archive.ubuntu.com
 100 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports/restricted amd64 Packages
     release v=12.10,o=Ubuntu,a=quantal-backports,n=quantal,l=Ubuntu,c=restricted
     origin us.archive.ubuntu.com
 100 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports/main amd64 Packages
     release v=12.10,o=Ubuntu,a=quantal-backports,n=quantal,l=Ubuntu,c=main
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/universe Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/restricted Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/multiverse Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/multiverse i386 Packages
     release v=12.10,o=Ubuntu,a=quantal-updates,n=quantal,l=Ubuntu,c=multiverse
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/universe i386 Packages
     release v=12.10,o=Ubuntu,a=quantal-updates,n=quantal,l=Ubuntu,c=universe
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/restricted i386 Packages
     release v=12.10,o=Ubuntu,a=quantal-updates,n=quantal,l=Ubuntu,c=restricted
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main i386 Packages
     release v=12.10,o=Ubuntu,a=quantal-updates,n=quantal,l=Ubuntu,c=main
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/multiverse amd64 Packages
     release v=12.10,o=Ubuntu,a=quantal-updates,n=quantal,l=Ubuntu,c=multiverse
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/universe amd64 Packages
     release v=12.10,o=Ubuntu,a=quantal-updates,n=quantal,l=Ubuntu,c=universe
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/restricted amd64 Packages
     release v=12.10,o=Ubuntu,a=quantal-updates,n=quantal,l=Ubuntu,c=restricted
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main amd64 Packages
     release v=12.10,o=Ubuntu,a=quantal-updates,n=quantal,l=Ubuntu,c=main
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/universe Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/restricted Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/multiverse Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/multiverse i386 Packages
     release v=12.10,o=Ubuntu,a=quantal,n=quantal,l=Ubuntu,c=multiverse
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/universe i386 Packages
     release v=12.10,o=Ubuntu,a=quantal,n=quantal,l=Ubuntu,c=universe
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/restricted i386 Packages
     release v=12.10,o=Ubuntu,a=quantal,n=quantal,l=Ubuntu,c=restricted
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main i386 Packages
     release v=12.10,o=Ubuntu,a=quantal,n=quantal,l=Ubuntu,c=main
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/multiverse amd64 Packages
     release v=12.10,o=Ubuntu,a=quantal,n=quantal,l=Ubuntu,c=multiverse
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/universe amd64 Packages
     release v=12.10,o=Ubuntu,a=quantal,n=quantal,l=Ubuntu,c=universe
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/restricted amd64 Packages
     release v=12.10,o=Ubuntu,a=quantal,n=quantal,l=Ubuntu,c=restricted
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
     release v=12.10,o=Ubuntu,a=quantal,n=quantal,l=Ubuntu,c=main
     origin us.archive.ubuntu.com
Pinned packages:

---

### Post by jerome1232 on 2012-11-13
There goes my idea, no pinned packages.

---

### Post by odror on 2012-11-13
> **jerome1232 said:**
> There goes my idea, no pinned packages.

I think that the issue is that the version of the 64bit libcairo2 does not match the 32 bit one. I do not know how to work around that. If I can install libecairo2:i386. I might be able to fix the problem. Any ideas?

---

