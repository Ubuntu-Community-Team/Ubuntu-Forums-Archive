---
title: "Update Manager error : Requires installation of untrusted packages"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by _nedR on 2011-08-19
When I tried to update my ubuntu  yesterday, I got the following error:
> 
[B]Requires installation of untrusted packages
[/B]
The action would require the installation of packages from not authenticated sources.

aptdaemon aptdaemon-data firefox firefox-branding firefox-globalmenu firefox-gnome-support firefox-locale-en gnome-keyring libgcr0 libgp11-0 libpam-gnome-keyring linux-generic linux-headers-2.6.38-11 linux-headers-2.6.38-11-generic linux-headers-generic linux-image-2.6.38-11-generic linux-image-generic linux-libc-dev python-aptdaemon python-aptdaemon-gtk python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets
This error came out of the blue since Update worked fine until yesterday.

Searching online i tried the fix suggested in [http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/)  which involved fetching the Public keys for 58682E70DBF506D7 and  40976EAF437D05B5. Still no luck. When i typed **apt-get update** i got the following error :

> W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://deb.torproject.org/torproject.org/dists/natty/main/binary-i386/Packages](http://deb.torproject.org/torproject.org/dists/natty/main/binary-i386/Packages)  403  Forbidden
note: Please ignore the torproject error; Thats because the country i am in blocks it.

Any help is much appreciated,

_nedR

---

### Post by _nedR on 2011-08-20
Got this issue fixed thanks to Naptha's solution posted in : [http://ubuntuforums.org/showthread.php?t=802156](http://ubuntuforums.org/showthread.php?t=802156)

Specifically running :

>  sudo rm -r /var/lib/apt/lists 
sudo mkdir -p /var/lib/apt/lists/partial 
sudo aptitude updateNow Update works fine.

Thanks anyway,
_nedR

---

