---
title: "HD-Media install of 13.04-desktop-amd64 failing: Unable to find Packages.gz"
date: 2013-06-20
forum: Installation &amp; Upgrades
---

### Post by GeneralShenanigans on 2013-06-20
I'm having exactly the issue that was described in this single-post, closed thread: [http://ubuntuforums.org/showthread.php?t=1484967](http://ubuntuforums.org/showthread.php?t=1484967)

Using a USB thumb drive with a preseeding file to mount the ubuntu-13.04-desktop-amd64.iso installer (to /cdrom) and then install. 

/var/log/syslog shows that the ISO is mounting correctly:
```
Jun 20 18:13:36 iso-scan: Ubuntu ISO ./ubuntu-13.04-desktop-amd64.iso usable
```

mount shows both the USB and the ISO mounted correctly:
```
/dev/sdb1 on /hd-media type ntfs (<args>)
/dev/loop0 on /cdrom type iso9660 (ro, relatime)
```

The errors that I believe are halting the install are these:
```
Jun 20 18:28:48 cdrom-retriever: warning: unable to find main/debian-installer/binary-amd64/Packages in /cdrom/dists/raring/Release
Jun 20 18:28:48 cdrom-retriever: warning: unable to find main/debian-installer/binary-amd64/Packages.gz in /cdrom/dists/raring/Release
Jun 20 18:28:48 cdrom-retriever: warning: unable to find restricted/debian-installer/binary-amd64/Packages in /cdrom/dists/raring/Release
Jun 20 18:28:48 cdrom-retriever: warning: unable to find restricted/debian-installer/binary-amd64/Packages.gz in /cdrom/dists/raring/Release
Jun 20 18:28:48 cdrom-retriever: warning: unable to find universe/debian-installer/binary-amd64/Packages in /cdrom/dists/raring/Release
Jun 20 18:28:48 cdrom-retriever: warning: unable to find universe/debian-installer/binary-amd64/Packages.gz in /cdrom/dists/raring/Release
Jun 20 18:28:48 cdrom-retriever: warning: unable to find multiverse/debian-installer/binary-amd64/Packages in /cdrom/dists/raring/Release
Jun 20 18:28:48 cdrom-retriever: warning: unable to find multiverse/debian-installer/binary-amd64/Packages.gz in /cdrom/dists/raring/Release
Jun 20 18:28:48 anna[4246]: WARNING **: bad d-i Packages file
```

The Release file in question has references to {main,restricted,universe,multiverse}/binary-amd64/Packages{.gz}, but none reference 'debian-installer'

I'm adapting the USB install method from a working 12.04.2 LTS build (only changes were ISO, vmlinuz, and initrd.gz). 

Could this be a bug in the Raring installer? Or am I missing something obvious? 

Thanks!

---

