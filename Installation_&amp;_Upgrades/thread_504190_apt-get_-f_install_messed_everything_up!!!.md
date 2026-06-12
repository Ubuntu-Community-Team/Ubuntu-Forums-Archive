---
title: "apt-get -f install messed everything up!!!"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by kamilczauz on 2007-07-18
i tried installing deluge bittorrent client on my DAPPER dist, but it needed a new version of libc6, so i downloaded the deb package and installed libc6 using dpkg -i.... then all hell went loose...

apt-get gave me an error that i must do apt-get -f install to make everything work... so i did, 

it said it was going to remove the following packages:

build-essential g++ g++-4.0 libatk1.0-dev libc6-dev libc6-i686 libcairo2-dev libexpat1-dev libfontconfig1-dev  libfreetype6-dev libglib2.0-dev libgtk2.0-dev libpango1.0-dev libpng12-dev libstdc++6-4.0-dev libxft-dev python-notify  ubuntu-base ubuntu-minimal zlib1g-dev

me, not paying attention... allowed it to remove the packages and now i cant install any of them,,, apt gives me all kinds of weird errors...

this is what happens when i try to remove libc6
```
root@Server:~# apt-get -f remove libc6
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>= 2.0.2) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
  openoffice.org-l10n-en-us: Depends: openoffice.org-common (>= 2.0.2) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
  openoffice.org-l10n-en-za: Depends: openoffice.org-common (>= 2.0.2) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
E: Broken packages

```

---

