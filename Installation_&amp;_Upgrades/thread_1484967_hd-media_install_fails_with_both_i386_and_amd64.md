---
title: "hd-media install fails with both i386 and amd64"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by ducbian on 2010-05-16
I'm trying to install Lucid on a machine with no cd-rom from an hd-media image and followed the guide at [https://help.ubuntu.com/10.04/installation-guide/amd64/boot-usb-files.html](https://help.ubuntu.com/10.04/installation-guide/amd64/boot-usb-files.html) for details.

I formatted a 2GB stick as FAT16, installed syslinux and tried the hd-media installer images combined with the desktop isos from:

```

http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/hd-media/
http://releases.ubuntu.com/lucid/ubuntu-10.04-desktop-i386.iso

```
and

```

http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-amd64/current/images/hd-media/
http://releases.ubuntu.com/lucid/ubuntu-10.04-desktop-amd64.iso
respectively.

```
Both failed with identical circumstances during a non-graphical install with the syslog error:
```

cdrom-retriever: warning: Unable to find main/debian-installer/binary-amd64/Packages in /cdrom/dists/lucid/Release.
cdrom-retriever: warning: Unable to find main/debian-installer/binary-amd64/Packages.gz in /cdrom/dists/lucid/Release.
cdrom-retriever: warning: Unable to find restricted/debian-installer/binary-amd64/Packages in /cdrom/dists/lucid/Release.
cdrom-retriever: warning: Unable to find restricted/debian-installer/binary-amd64/Packages.gz in /cdrom/dists/lucid/Release.

```

I'm a bit stumped, I can try downloading various other cd-images but i suspect I'm doing something obvious wrong - anyone got any sugestions?

---

