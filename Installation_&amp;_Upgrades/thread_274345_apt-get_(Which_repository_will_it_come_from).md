---
title: "apt-get (Which repository will it come from?)"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by onioneater36 on 2006-10-09
If you have a /etc/apt/sources.list file that looks like...

> ## UBUNTU DEFAULT
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

## UBUNTU GUIDE
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
#deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
#deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                               
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## [www.winehq.org](www.winehq.org)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

and you key in the following at a terminal window...

```
sudo apt-get install wine
```

...is there any way to know exactly which repository the package is going to come from?  (In other words, if the package is in more than 1 repository, who wins?).  The closest I am to answering my own question thru research is if I do a...

```
sudo aptitude -v show wine
```

which will show you the following at the command prompt...

> Package: wine
State: installed
Automatically installed: no
Version: 0.9.22~winehq0~ubuntu~6.06-1
Priority: optional
Section: otherosfs
Maintainer: Scott Ritchie <scott@open-vote.org>
Uncompressed Size: 42.1M
Architecture: i386
Compressed Size: 8976k
Filename: pool/main/w/wine/wine_0.9.22~winehq0~ubuntu~6.06-1_i386.deb
MD5sum: eb1bcc9e8b3be625ba60c0e56c8371dc
Archive: dapper, now
Depends: libstdc++6, libxxf86dga1, freeglut3, libartsc0 (>= 1.5.2-0), libasound2 (> 1.0.10), libaudio2, libaudiofile0 (>= 0.2.3-4),
         libc6 (>= 2.3.4-1), libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35), libgcc1 (>= 1:4.0.2), libgl1-mesa | libgl1,
         libglib2.0-0 (>= 2.10.0), libglu1-mesa | libglu1, libgphoto2-2 (>= 2.1.6-5.2ubuntu8), libgphoto2-port0 (>=
         2.1.6-5.2ubuntu8), libice6, libieee1284-3, libjpeg62, liblcms1 (>= 1.08-1), libldap2 (>= 2.1.17-1), libsane (>= 1.0.11-3),
         libsm6, libstdc++6 (>= 4.0.2-4), libusb-0.1-4 (>= 2:0.1.10a), libx11-6, libxext6, libxi6, libxml2 (>= 2.6.24), libxmu6,
         libxslt1.1 (>= 1.1.15), libxt6, libxxf86vm1, zlib1g (>= 1:1.2.1)
Suggests: msttcorefonts
Conflicts: binfmt-support (< 1.1.2), winesetuptk, wine-doc, wine-utils, libwine-alsa, libwine-arts, libwine-capi, libwine-jack,
           libwine-nas, libwine-print, libwine-twain, libwine-cil, xwine, libwine-gl
Replaces: winesetuptk, wine-doc, wine-utils, libwine-alsa, libwine-arts, libwine-capi, libwine-jack, libwine-nas, libwine-print,
          libwine-twain, libwine, libwine-dev, libwine-cil, xwine, libwine-gl
Description: Microsoft Windows Compatibility Layer (Binary Emulator and Library)
 While Wine is usually thought of as a Microsoft Windows emulator, the Wine developers would prefer that users thought of Wine as a
 Windows compatibility layer for Linux. Wine does not require MS Windows, but it can use native system dll files in place of its own if they are available.

 This package includes a program loader, which allows unmodified Windows binaries to run under compatible hardware.  This package
 also includes the library that implements the Wine project's free version of the Windows API, allowing successful running of
 programs ported directly from Windows.

Package: wine
State: installed
Automatically installed: no
Version: 0.9.9-0ubuntu2
Priority: optional
Section: universe/otherosfs
Maintainer: Scott Ritchie <scott@open-vote.org>
Uncompressed Size: 41.4M
Architecture: i386
Compressed Size: 8785k
Filename: pool/universe/w/wine/wine_0.9.9-0ubuntu2_i386.deb
MD5sum: 4546533378332b6a7a82f7c09f2ae755
Archive: dapper
Depends: libstdc++6, libxxf86dga1
Suggests: msttcorefonts
Conflicts: binfmt-support (< 1.1.2), winesetuptk, wine-doc, wine-utils, libwine-alsa, libwine-arts, libwine-capi, libwine-jack,
           libwine-nas, libwine-print, libwine-twain, libwine-cil, xwine, libwine-gl
Replaces: winesetuptk, wine-doc, wine-utils, libwine-alsa, libwine-arts, libwine-capi, libwine-jack, libwine-nas, libwine-print,
          libwine-twain, libwine, libwine-dev, libwine-cil, xwine, libwine-gl
Description: Microsoft Windows Compatibility Layer (Binary Emulator and Library)
 While Wine is usually thought of as a Microsoft Windows emulator, the Wine developers would prefer that users thought of Wine as a
 Windows compatibility layer for Linux. Wine does not require MS Windows, but it can use native system dll files in place of its own if they are available.

 This package includes a program loader, which allows unmodified Windows binaries to run under compatible hardware.  This package
 also includes the library that implements the Wine project's free version of the Windows API, allowing successful running of
 programs ported directly from Windows.


There are alot of hints in this information, but nothing that makes me 100% confident that I know which repository it is coming from.

Thanks in advance...

---

### Post by meng on 2006-10-09
I'm pretty sure it will come from the winehq repository (the last one on your list) because that's where the most recent version is located.

---

