---
title: "Trouble installing libgtk2.0-dev in Crunchbang (Debian Squeeze)"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by damnated on 2011-10-30
I realise this is a pretty common issue, and I've searched a lot for this, but I could never find an error similar to mine, thus I was unable to get help.
This is what happens. I try to install libgtk2.0-dev. I get ```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgtk2.0-dev : Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
E: Broken packages

```
when trying to install libpango I get ```
The following packages have unmet dependencies:
 libpango1.0-dev : Depends: libxft-dev but it is not going to be installed
E: Broken packages

```
and when I try to get libxft-dev I find the root of the problem, which is ```
The following packages have unmet dependencies:
 libxft-dev : Depends: libxft2 (= 2.1.14-2) but 2.2.0-2.1 is to be installed
E: Broken packages
```
I have libxft2 version 2.2.0-2.1 already installed and it seems that my package should be downgraded, unfortunately a shitload of packages depend on libxft2 so I can't uninstall, install the older version and reinstall everything, plus there's no guarantee that those packages don't depend on the newer version of libxft2.

Is there any way around this? I tried installing with fix missing, but that did nothing for me.
My sources list ```
## CRUNCHBANG
## Compatible with Debian Squeeze, but use at your own risk.
deb http://packages.crunchbanglinux.org/statler statler main

## DEBIAN
deb http://ftp.de.debian.org/debian/ squeeze main contrib non-free
# deb-src http://ftp.de.debian.org/debian/ squeeze main contrib non-free

## DEBIAN SECURITY
deb http://security.debian.org/ squeeze/updates main
# deb-src http://security.debian.org/ squeeze/updates main

## DEBIAN BACKPORTS
deb http://backports.debian.org/debian-backports squeeze-backports main contrib non-free

## GOOGLE CHROME
## see /etc/apt/sources.list.d directory
deb http://download.skype.com/linux/repos/debian/ stable non-free
deb http://deb.gionn.net/ squeeze-backports main

```

---

