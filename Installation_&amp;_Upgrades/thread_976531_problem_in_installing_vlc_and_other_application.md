---
title: "problem in installing vlc and other application"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by arunprasad13 on 2008-11-09
hi..i encounter problem when i try to install any application.
i got the following error when i tried to install vlc


arun@arun-desktop:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  x11proto-xext-dev libdevhelp-1-0 x11proto-kb-dev libgbf-1-0 libapr0 anjuta-common libxdmcp-dev libpng12-dev libsvn0 xtrans-dev x11proto-core-dev
  devhelp-common libxext-dev libjpeg62-dev zlib1g-dev libgbf-1-common x11proto-input-dev libfreetype6-dev libgdk-pixbuf2 libxau-dev liborbit0 libx11-dev
  x-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libvlc0 vlc-nox
Suggested packages:
  mozilla-plugin-vlc
Recommended packages:
  videolan-doc
The following NEW packages will be installed:
  libvlc0 vlc vlc-nox
0 upgraded, 3 newly installed, 0 to remove and 204 not upgraded.
Need to get 6787kB of archives.
After unpacking 18.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libvlc0 vlc-nox vlc
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe libvlc0 0.8.6.release-0ubuntu1~edgy1
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe vlc-nox 0.8.6.release-0ubuntu1~edgy1
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe vlc 0.8.6.release-0ubuntu1~edgy1
  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc0_0.8.6.release-0ubuntu1~edgy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc0_0.8.6.release-0ubuntu1~edgy1_i386.deb)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_0.8.6.release-0ubuntu1~edgy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_0.8.6.release-0ubuntu1~edgy1_i386.deb)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_0.8.6.release-0ubuntu1~edgy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_0.8.6.release-0ubuntu1~edgy1_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

what should i do..?

---

### Post by Partyboi2 on 2008-11-11
Edgy has reached its end of life. You would be better off to upgrade to a newer release of ubuntu.

---

