---
title: "Help with repository keys"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by TruthDose on 2010-04-27
I installed the ubuntu studio repository on karmic and I am unable to update. Any idea on where I can find the key to do so?


"GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead."

---

### Post by plucky on 2010-04-27
> "GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net)  karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89

Open a terminal and ```
gpg --keyserver keyserver.ubuntu.com --recv 2ED6BB6042C24D89
gpg --export --armor 2ED6BB6042C24D89 | sudo apt-key add -
```

> Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead." 

Open **System > Administration > Software Sources** and un-tick the CDrom boxes on the first page.

Good Luck

---

