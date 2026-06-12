---
title: "Flash"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by JohanA on 2010-03-12
Can anyone help me to fix this, when I try to install Flash this show up


Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.



GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAEFailed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by plucky on 2010-03-12
> GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAEFailed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/main/binary-amd64/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/restricted/binary-amd64/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.


You seem to be mixing jaunty and karmic sources.

From a terminal ```
cat /etc/apt/sources.list
``` and post to the forum please.

Also the output of ```
sudo apt-get update
```

---

