---
title: "Install from local repository via pxelinx?"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by ACID25 on 2007-07-04
Hi

i have a problem to realize a automatic ubuntu installation. The normal installation with pxelinux works fine but if i want to choose my local repository i get an error message

```

choose a mirror of the Ubuntu archive &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
   &#9474;                          Bad archive mirror                           &#9474;
   &#9474; The specified Ubuntu archive mirror is either not available, or does  &#9474;
   &#9474; not have a valid Release file on it. Please try a different mirror.

```

i create my repository with this debmirror script 
```

#!/bin/bash
# 
# Spiegelt die Haupt-Ubuntu-Repostiories von Feisty & Dapper Drake
#
#logger -t feisty.sh.[$$] Updating Ubuntu
debmirror /var/www/html/ubuntu --passive --progress -v --nosource \
--host=ftp.inf.tu-dresden.de --root=os/linux/dists/ubuntu \
--dist=feisty,feisty-backports,feisty-proposed,feisty-security,feisty-updates,dapper,dapper-backports,dapper-proposed,dapper-security,dapper-updates \
--ignore-missing-release \
--section=main,main/debian-installer,restricted,restricted/debian-installer --arch=i386 --cleanup \
#--verbose logger -t feisty.sh

```

so i think there´s some missing parameter in this script cause if i execute this i got the following error
```

[root@srv1 html]# ./feisty.sh
Mirroring to /var/www/html/ubuntu from ftp://anonymous@ftp.inf.tu-dresden.de/os/linux/dists/ubuntu/
Arches: i386
Dists: feisty,feisty-backports,feisty-proposed,feisty-security,feisty-updates,dapper,dapper-backports,dapper-proposed,dapper-security,dapper-updates
Sections: main,main/debian-installer,restricted,restricted/debian-installer
Passive mode on.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Keeping: dists/feisty/Release
[0%] Keeping: dists/feisty/Release.gpg
gpg: Signature made Tue 17 Apr 2007 08:20:13 PM CEST using DSA key ID 437D05B5
gpg: Can't check signature: public key not found
Release signature does not verify.
[0%] Keeping: dists/feisty-backports/Release
[0%] Keeping: dists/feisty-backports/Release.gpg
gpg: Signature made Fri 22 Jun 2007 05:12:17 AM CEST using DSA key ID 437D05B5
gpg: Can't check signature: public key not found
Release signature does not verify.
[0%] Keeping: dists/feisty-proposed/Release
[0%] Keeping: dists/feisty-proposed/Release.gpg
gpg: Signature made Fri 29 Jun 2007 07:30:17 PM CEST using DSA key ID 437D05B5
gpg: Can't check signature: public key not found
Release signature does not verify.
[0%] Keeping: dists/feisty-security/Release
[0%] Keeping: dists/feisty-security/Release.gpg
gpg: Signature made Fri 29 Jun 2007 03:33:22 AM CEST using DSA key ID 437D05B5
gpg: Can't check signature: public key not found
Release signature does not verify.
[0%] Keeping: dists/feisty-updates/Release
[0%] Keeping: dists/feisty-updates/Release.gpg
gpg: Signature made Fri 15 Jun 2007 12:29:16 PM CEST using DSA key ID 437D05B5
gpg: Can't check signature: public key not found
Release signature does not verify.
[0%] Keeping: dists/dapper/Release
[0%] Keeping: dists/dapper/Release.gpg
gpg: Signature made Wed 31 May 2006 09:02:10 PM CEST using DSA key ID 437D05B5
gpg: Can't check signature: public key not found
Release signature does not verify.
[0%] Keeping: dists/dapper-backports/Release
[0%] Keeping: dists/dapper-backports/Release.gpg
gpg: Signature made Thu 03 May 2007 09:03:09 PM CEST using DSA key ID 437D05B5
gpg: Can't check signature: public key not found
Release signature does not verify.
[0%] Keeping: dists/dapper-proposed/Release
[0%] Keeping: dists/dapper-proposed/Release.gpg
gpg: Signature made Wed 13 Jun 2007 08:28:40 PM CEST using DSA key ID 437D05B5
gpg: Can't check signature: public key not found
Release signature does not verify.
...
 Download of dists/feisty-updates/restricted/debian-installer/binary-i386/Packages.gz failed: dists/feisty-updates/restricted/debian-installer/binary-i386/Packages.gz: No such file or directory
 Ignoring missing Release file for dists/dapper-backports/restricted/debian-installer/binary-i386/Packages.gz
 Download of dists/dapper-backports/restricted/debian-installer/binary-i386/Packages.gz failed: dists/dapper-backports/restricted/debian-installer/binary-i386/Packages.gz: No such file or directory
 Ignoring missing Release file for dists/dapper-proposed/restricted/debian-installer/binary-i386/Packages.gz
 Download of dists/dapper-proposed/restricted/debian-installer/binary-i386/Packages.gz failed: dists/dapper-proposed/restricted/debian-installer/binary-i386/Packages.gz: No such file or directory
Failed to download some Package, Sources or Release files!
releasing 1 pending lock... at /usr/lib/perl5/vendor_perl/5.8.3/LockFile/Simple.pm line 182.

```

so what should i do that i can realize a installation from my local repository. The repo-Server is NOT A UBUNTU OR DEBIAN machine.....any help is very welcome ;)

Best regards
ACID25

---

