---
title: "[SOLVED] Could not calculate the upgrade"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by cybergalvez on 2008-10-30
I am trying to upgrade 8.04 to 8.10 using the alt disk and I am getting this error:  "Could not calculate the upgrade"  What should I do to resolve this?
Jose

---

### Post by cybergalvez on 2008-10-30
> **cybergalvez said:**
> I am trying to upgrade 8.04 to 8.10 using the alt disk and I am getting this error:  "Could not calculate the upgrade"  What should I do to resolve this?
Jose

Solved - I had to remove a package that was not behaving well, some postgres package

---

### Post by davidshere on 2008-10-30
> **cybergalvez said:**
> Solved - I had to remove a package that was not behaving well, some postgres package

How did you determine that package to be the problem?

---

### Post by pirattrev on 2008-10-30
...and out of curiosity what packages were being uncooperative?

---

### Post by cybergalvez on 2008-11-01
How rude of me, sorry for not adding what the solution really was.  
To determine what package was causing the upgrade problem I looked in /var/log/dist-upgrade/main.log for any errors.  There I found that an error stating that it could not remove the package postgresql-autodoc which needed to be removed.  So I just removed the pacakge manually with syanaptic and then the upgrade worked

Jose

---

### Post by davidshere on 2008-11-01
> **cybergalvez said:**
> How rude of me, sorry for not adding what the solution really was.  
To determine what package was causing the upgrade problem I looked in /var/log/dist-upgrade/main.log for any errors.  There I found that an error stating that it could not remove the package postgresql-autodoc which needed to be removed.  So I just removed the pacakge manually with syanaptic and then the upgrade worked

Jose

Great!  My error messages seem to be less clear.  Any suggestions?

```
2008-10-30 20:13:36,040 INFO release-upgrader version '0.93.32' started
2008-10-30 20:13:38,628 DEBUG svg pixbuf loader failed (Error displaying image)
2008-10-30 20:13:38,892 DEBUG Using 'DistUpgradeViewGtk' view
2008-10-30 20:13:39,027 DEBUG enable dpkg --force-overwrite
2008-10-30 20:13:39,262 DEBUG lsb-release: 'hardy'
2008-10-30 20:13:39,263 DEBUG _pythonSymlinkCheck run
2008-10-30 20:13:39,310 DEBUG openCache()
2008-10-30 20:13:48,724 DEBUG /openCache()
2008-10-30 20:13:48,725 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntustudio-desktop')
2008-10-30 20:13:48,725 DEBUG checkViewDepends()
2008-10-30 20:13:59,486 DEBUG useNetwork: 'True' (selected by user)
2008-10-30 20:14:00,115 ERROR No new dist found
2008-10-30 20:14:00,115 DEBUG running doUpdate() (showErrors=False)
2008-10-30 20:15:00,354 DEBUG openCache()
2008-10-30 20:15:04,266 DEBUG /openCache()
2008-10-30 20:15:04,267 DEBUG doPostInitialUpdate
2008-10-30 20:15:04,267 DEBUG quirks: running intrepidPostInitialUpdate
2008-10-30 20:15:04,267 DEBUG running intrepidPostInitialUpdate
2008-10-30 20:15:08,457 DEBUG Foreign: 
2008-10-30 20:15:08,458 DEBUG Obsolete: libcdio6 liblaunchpad-integration0 libpt-plugins-alsa libpci2 xgc bitmap libopencdk8 xvncviewer libpt-plugins-v4l lightscribeapplications hal-device-manager lightscribe ico libpisync0 vcf beforelight libpq4 libcinepaint0 python-eunuchs libmagick9 libpt-plugins-v4l2 libxklavier11 libjessie-java libdvdcss2 xf86dga gnopernicus mkisofs cinepaint-data gnome-keyring-manager libpt-1.10.0 w32codecs libdb3 libgsl0 vnc-common cdrecord rosegarden4 libneon25 libbrlapi1 libbeagle0 libldap2
2008-10-30 20:15:08,460 DEBUG updateSourcesList()
2008-10-30 20:15:08,620 DEBUG rewriteSourcesList()
2008-10-30 20:15:08,625 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted'
2008-10-30 20:15:08,625 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted' updated to new dist
2008-10-30 20:15:08,625 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted'
2008-10-30 20:15:08,626 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted' updated to new dist
2008-10-30 20:15:08,626 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted'
2008-10-30 20:15:08,626 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted' updated to new dist
2008-10-30 20:15:08,626 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted'
2008-10-30 20:15:08,626 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted' updated to new dist
2008-10-30 20:15:08,627 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy universe'
2008-10-30 20:15:08,627 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe' updated to new dist
2008-10-30 20:15:08,627 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe'
2008-10-30 20:15:08,627 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe' updated to new dist
2008-10-30 20:15:08,627 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe'
2008-10-30 20:15:08,628 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe' updated to new dist
2008-10-30 20:15:08,628 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe'
2008-10-30 20:15:08,628 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe' updated to new dist
2008-10-30 20:15:08,628 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse'
2008-10-30 20:15:08,629 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse' updated to new dist
2008-10-30 20:15:08,629 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse'
2008-10-30 20:15:08,629 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse' updated to new dist
2008-10-30 20:15:08,629 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse'
2008-10-30 20:15:08,629 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse' updated to new dist
2008-10-30 20:15:08,630 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse'
2008-10-30 20:15:08,630 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse' updated to new dist
2008-10-30 20:15:08,630 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse'
2008-10-30 20:15:08,630 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse' updated to new dist
2008-10-30 20:15:08,631 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse'
2008-10-30 20:15:08,631 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse' updated to new dist
2008-10-30 20:15:08,631 DEBUG examining: 'deb http://archive.canonical.com/ubuntu hardy partner'
2008-10-30 20:15:08,631 DEBUG entry 'deb http://archive.canonical.com/ubuntu intrepid partner' updated to new dist
2008-10-30 20:15:08,632 DEBUG examining: 'deb-src http://archive.canonical.com/ubuntu hardy partner'
2008-10-30 20:15:08,632 DEBUG entry 'deb-src http://archive.canonical.com/ubuntu intrepid partner' updated to new dist
2008-10-30 20:15:08,632 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu hardy-security main restricted'
2008-10-30 20:15:08,632 DEBUG entry 'deb http://security.ubuntu.com/ubuntu intrepid-security main restricted' updated to new dist
2008-10-30 20:15:08,632 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted'
2008-10-30 20:15:08,633 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted' updated to new dist
2008-10-30 20:15:08,633 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu hardy-security universe'
2008-10-30 20:15:08,633 DEBUG entry 'deb http://security.ubuntu.com/ubuntu intrepid-security universe' updated to new dist
2008-10-30 20:15:08,633 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu hardy-security universe'
2008-10-30 20:15:08,633 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu intrepid-security universe' updated to new dist
2008-10-30 20:15:08,634 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu hardy-security multiverse'
2008-10-30 20:15:08,634 DEBUG entry 'deb http://security.ubuntu.com/ubuntu intrepid-security multiverse' updated to new dist
2008-10-30 20:15:08,634 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse'
2008-10-30 20:15:08,634 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse' updated to new dist
2008-10-30 20:15:08,635 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu hardy-updates universe multiverse'
2008-10-30 20:15:08,635 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu intrepid-updates universe multiverse' updated to new dist
2008-10-30 20:15:08,635 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse'
2008-10-30 20:15:08,635 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse' updated to new dist
2008-10-30 20:15:08,664 DEBUG AptCdrom.add() called with '/cdrom'
2008-10-30 20:15:08,785 INFO ignoring missing '/cdrom/dists/intrepid/restricted/debian-installer/binary-i386/Packages'
2008-10-30 20:15:08,787 INFO ignoring missing '/cdrom/dists/intrepid/restricted/binary-i386/Packages'
2008-10-30 20:15:08,797 INFO ignoring missing '/cdrom/dists/intrepid/main/debian-installer/binary-i386/Packages'
2008-10-30 20:15:08,891 INFO ignoring missing '/cdrom/dists/intrepid/main/binary-i386/Packages'
2008-10-30 20:15:08,980 DEBUG AptCdrom.add() returned: True
2008-10-30 20:15:08,980 DEBUG running doUpdate() (showErrors=True)
2008-10-30 20:16:09,139 DEBUG openCache()
2008-10-30 20:16:13,637 DEBUG /openCache()
2008-10-30 20:16:19,798 DEBUG Running KeepInstalledSection rules
2008-10-30 20:16:19,812 DEBUG Kernel uname: '2.6.24-21-386' 
2008-10-30 20:16:19,847 DEBUG nvidiaUpdate()
2008-10-30 20:16:19,923 INFO no old nvidia driver installed, installing no new
2008-10-30 20:16:19,924 DEBUG Removing 'libflashsupport' (Distro PostUpgradeRemove rule)
2008-10-30 20:16:19,976 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2008-10-30 20:16:19,977 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2008-10-30 20:16:19,977 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2008-10-30 20:16:20,032 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2008-10-30 20:16:20,082 DEBUG Purging 'python2.3' (Distro PostUpgradePurge rule)
2008-10-30 20:16:20,083 DEBUG quirks: running intrepidPostDistUpgradeCache
2008-10-30 20:16:20,083 DEBUG running intrepidPostDistUpgradeCache
2008-10-30 20:16:20,096 DEBUG Removing 'landscape-client' (custom landscape stub removal rule)
2008-10-30 20:16:20,250 DEBUG Marking 'ubuntustudio-desktop' for upgrade
2008-10-30 20:16:20,254 DEBUG metapkg 'ubuntustudio-desktop' installed but markedDelete
2008-10-30 20:16:20,254 DEBUG none of the '['ubuntu-desktop', 'kubuntu-desktop', 'edubuntu-desktop', 'xubuntu-desktop', 'ubuntustudio-desktop', 'ichthux-desktop', 'mythbuntu-desktop', 'kubuntu-kde4-desktop']' meta-pkgs installed
2008-10-30 20:16:20,255 DEBUG guessing 'ubuntustudio-desktop' as missing meta-pkg
2008-10-30 20:16:31,666 ERROR failed to mark 'ubuntustudio-desktop' for install (E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.)
2008-10-30 20:17:31,830 ERROR Dist-upgrade failed: 'Can't upgrade required meta-packages'
2008-10-30 20:17:31,832 DEBUG openCache()
2008-10-30 20:17:55,891 DEBUG /openCache()

```

---

### Post by cybergalvez on 2008-11-03
> **davidshere said:**
> Great!  My error messages seem to be less clear.  Any suggestions?

```
2008-10-30 20:13:36,040 INFO release-upgrader version '0.93.32' started
2008-10-30 20:13:38,628 DEBUG svg pixbuf loader failed (Error displaying image)
2008-10-30 20:13:38,892 DEBUG Using 'DistUpgradeViewGtk' view
2008-10-30 20:13:39,027 DEBUG enable dpkg --force-overwrite
2008-10-30 20:13:39,262 DEBUG lsb-release: 'hardy'
2008-10-30 20:13:39,263 DEBUG _pythonSymlinkCheck run
2008-10-30 20:13:39,310 DEBUG openCache()
2008-10-30 20:13:48,724 DEBUG /openCache()
2008-10-30 20:13:48,725 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntustudio-desktop')
2008-10-30 20:13:48,725 DEBUG checkViewDepends()
2008-10-30 20:13:59,486 DEBUG useNetwork: 'True' (selected by user)
2008-10-30 20:14:00,115 ERROR No new dist found
2008-10-30 20:14:00,115 DEBUG running doUpdate() (showErrors=False)
2008-10-30 20:15:00,354 DEBUG openCache()
2008-10-30 20:15:04,266 DEBUG /openCache()
2008-10-30 20:15:04,267 DEBUG doPostInitialUpdate
2008-10-30 20:15:04,267 DEBUG quirks: running intrepidPostInitialUpdate
2008-10-30 20:15:04,267 DEBUG running intrepidPostInitialUpdate
2008-10-30 20:15:08,457 DEBUG Foreign: 
2008-10-30 20:15:08,458 DEBUG Obsolete: libcdio6 liblaunchpad-integration0 libpt-plugins-alsa libpci2 xgc bitmap libopencdk8 xvncviewer libpt-plugins-v4l lightscribeapplications hal-device-manager lightscribe ico libpisync0 vcf beforelight libpq4 libcinepaint0 python-eunuchs libmagick9 libpt-plugins-v4l2 libxklavier11 libjessie-java libdvdcss2 xf86dga gnopernicus mkisofs cinepaint-data gnome-keyring-manager libpt-1.10.0 w32codecs libdb3 libgsl0 vnc-common cdrecord rosegarden4 libneon25 libbrlapi1 libbeagle0 libldap2
2008-10-30 20:15:08,460 DEBUG updateSourcesList()
2008-10-30 20:15:08,620 DEBUG rewriteSourcesList()
2008-10-30 20:15:08,625 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted'
2008-10-30 20:15:08,625 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted' updated to new dist
2008-10-30 20:15:08,625 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted'
2008-10-30 20:15:08,626 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted' updated to new dist
2008-10-30 20:15:08,626 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted'
2008-10-30 20:15:08,626 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted' updated to new dist
2008-10-30 20:15:08,626 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted'
2008-10-30 20:15:08,626 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted' updated to new dist
2008-10-30 20:15:08,627 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy universe'
2008-10-30 20:15:08,627 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe' updated to new dist
2008-10-30 20:15:08,627 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe'
2008-10-30 20:15:08,627 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe' updated to new dist
2008-10-30 20:15:08,627 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe'
2008-10-30 20:15:08,628 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe' updated to new dist
2008-10-30 20:15:08,628 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe'
2008-10-30 20:15:08,628 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe' updated to new dist
2008-10-30 20:15:08,628 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse'
2008-10-30 20:15:08,629 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse' updated to new dist
2008-10-30 20:15:08,629 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse'
2008-10-30 20:15:08,629 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse' updated to new dist
2008-10-30 20:15:08,629 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse'
2008-10-30 20:15:08,629 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse' updated to new dist
2008-10-30 20:15:08,630 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse'
2008-10-30 20:15:08,630 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse' updated to new dist
2008-10-30 20:15:08,630 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse'
2008-10-30 20:15:08,630 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse' updated to new dist
2008-10-30 20:15:08,631 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse'
2008-10-30 20:15:08,631 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse' updated to new dist
2008-10-30 20:15:08,631 DEBUG examining: 'deb http://archive.canonical.com/ubuntu hardy partner'
2008-10-30 20:15:08,631 DEBUG entry 'deb http://archive.canonical.com/ubuntu intrepid partner' updated to new dist
2008-10-30 20:15:08,632 DEBUG examining: 'deb-src http://archive.canonical.com/ubuntu hardy partner'
2008-10-30 20:15:08,632 DEBUG entry 'deb-src http://archive.canonical.com/ubuntu intrepid partner' updated to new dist
2008-10-30 20:15:08,632 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu hardy-security main restricted'
2008-10-30 20:15:08,632 DEBUG entry 'deb http://security.ubuntu.com/ubuntu intrepid-security main restricted' updated to new dist
2008-10-30 20:15:08,632 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted'
2008-10-30 20:15:08,633 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted' updated to new dist
2008-10-30 20:15:08,633 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu hardy-security universe'
2008-10-30 20:15:08,633 DEBUG entry 'deb http://security.ubuntu.com/ubuntu intrepid-security universe' updated to new dist
2008-10-30 20:15:08,633 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu hardy-security universe'
2008-10-30 20:15:08,633 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu intrepid-security universe' updated to new dist
2008-10-30 20:15:08,634 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu hardy-security multiverse'
2008-10-30 20:15:08,634 DEBUG entry 'deb http://security.ubuntu.com/ubuntu intrepid-security multiverse' updated to new dist
2008-10-30 20:15:08,634 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse'
2008-10-30 20:15:08,634 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse' updated to new dist
2008-10-30 20:15:08,635 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu hardy-updates universe multiverse'
2008-10-30 20:15:08,635 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu intrepid-updates universe multiverse' updated to new dist
2008-10-30 20:15:08,635 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse'
2008-10-30 20:15:08,635 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse' updated to new dist
2008-10-30 20:15:08,664 DEBUG AptCdrom.add() called with '/cdrom'
2008-10-30 20:15:08,785 INFO ignoring missing '/cdrom/dists/intrepid/restricted/debian-installer/binary-i386/Packages'
2008-10-30 20:15:08,787 INFO ignoring missing '/cdrom/dists/intrepid/restricted/binary-i386/Packages'
2008-10-30 20:15:08,797 INFO ignoring missing '/cdrom/dists/intrepid/main/debian-installer/binary-i386/Packages'
2008-10-30 20:15:08,891 INFO ignoring missing '/cdrom/dists/intrepid/main/binary-i386/Packages'
2008-10-30 20:15:08,980 DEBUG AptCdrom.add() returned: True
2008-10-30 20:15:08,980 DEBUG running doUpdate() (showErrors=True)
2008-10-30 20:16:09,139 DEBUG openCache()
2008-10-30 20:16:13,637 DEBUG /openCache()
2008-10-30 20:16:19,798 DEBUG Running KeepInstalledSection rules
2008-10-30 20:16:19,812 DEBUG Kernel uname: '2.6.24-21-386' 
2008-10-30 20:16:19,847 DEBUG nvidiaUpdate()
2008-10-30 20:16:19,923 INFO no old nvidia driver installed, installing no new
2008-10-30 20:16:19,924 DEBUG Removing 'libflashsupport' (Distro PostUpgradeRemove rule)
2008-10-30 20:16:19,976 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2008-10-30 20:16:19,977 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2008-10-30 20:16:19,977 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2008-10-30 20:16:20,032 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2008-10-30 20:16:20,082 DEBUG Purging 'python2.3' (Distro PostUpgradePurge rule)
2008-10-30 20:16:20,083 DEBUG quirks: running intrepidPostDistUpgradeCache
2008-10-30 20:16:20,083 DEBUG running intrepidPostDistUpgradeCache
2008-10-30 20:16:20,096 DEBUG Removing 'landscape-client' (custom landscape stub removal rule)
2008-10-30 20:16:20,250 DEBUG Marking 'ubuntustudio-desktop' for upgrade
2008-10-30 20:16:20,254 DEBUG metapkg 'ubuntustudio-desktop' installed but markedDelete
2008-10-30 20:16:20,254 DEBUG none of the '['ubuntu-desktop', 'kubuntu-desktop', 'edubuntu-desktop', 'xubuntu-desktop', 'ubuntustudio-desktop', 'ichthux-desktop', 'mythbuntu-desktop', 'kubuntu-kde4-desktop']' meta-pkgs installed
2008-10-30 20:16:20,255 DEBUG guessing 'ubuntustudio-desktop' as missing meta-pkg
2008-10-30 20:16:31,666 ERROR failed to mark 'ubuntustudio-desktop' for install (E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.)
2008-10-30 20:17:31,830 ERROR Dist-upgrade failed: 'Can't upgrade required meta-packages'
2008-10-30 20:17:31,832 DEBUG openCache()
2008-10-30 20:17:55,891 DEBUG /openCache()

```

not sure , I would guess that ubuntustudio-desktop is the offending package.  Try removing that one and then reinstalling it after the upgrade

---

### Post by davidshere on 2008-11-03
Thanks... I uninstalled ubuntustudio-desktop, but that didnt' seem to fix the problem, so I uninstalled everything with "ubuntustudio" in it.  Upgrade appears to be proceeding normally now.

Seems like this shouldn't have been a problem...

---

### Post by sgeorgiev111 on 2010-07-19
hello, i have same problem. where is my log:


2010-07-19 15:52:51,749 INFO release-upgrader version '0.93.34' started
2010-07-19 15:52:51,752 DEBUG Using 'DistUpgradeViewText' view
2010-07-19 15:52:51,795 DEBUG enable dpkg --force-overwrite
2010-07-19 15:52:51,843 DEBUG lsb-release: 'hardy'
2010-07-19 15:52:51,844 DEBUG _pythonSymlinkCheck run
2010-07-19 15:52:51,844 DEBUG openCache()
2010-07-19 15:52:52,463 DEBUG /openCache()
2010-07-19 15:52:52,464 DEBUG needServerMode(): can not find a desktop meta package or key deps, running in server mode
2010-07-19 15:52:52,464 DEBUG checkViewDepends()
2010-07-19 15:52:52,464 DEBUG running doUpdate() (showErrors=False)
2010-07-19 15:52:53,454 DEBUG openCache()
2010-07-19 15:52:54,117 DEBUG /openCache()
2010-07-19 15:52:54,117 DEBUG doPostInitialUpdate
2010-07-19 15:52:54,117 DEBUG quirks: running intrepidPostInitialUpdate
2010-07-19 15:52:54,117 DEBUG running intrepidPostInitialUpdate
2010-07-19 15:52:55,641 DEBUG no PkgRecord found for 'linux-ubuntu-modules-2.6.22-15-generic', skipping 
2010-07-19 15:52:56,451 DEBUG no PkgRecord found for 'linux-ubuntu-modules-2.6.22-14-generic', skipping 
2010-07-19 15:52:56,694 DEBUG Foreign: 
2010-07-19 15:52:56,695 DEBUG Obsolete: libqtgui4 libqt4-designer truecrypt antidialer libqt4-svg libqtcore4 skype libqt4-dbus libqt4-script libqt4-xml libqt4-network libqt4-opengl libqt4-assistant adobe-flashplugin k3b-data libdvdcss2 libqt4-test libamrwb3 libntfs-3g28 libamrnb3 linux-image-2.6.27-1-generic libk3b3 live-usb-install libk3b3-extracodecs
2010-07-19 15:52:56,695 DEBUG updateSourcesList()
2010-07-19 15:52:56,739 DEBUG rewriteSourcesList()
2010-07-19 15:52:56,741 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main multiverse restricted'
2010-07-19 15:52:56,741 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main multiverse restricted' updated to new dist
2010-07-19 15:52:56,742 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe main multiverse restricted #Added by software-properties'
2010-07-19 15:52:56,742 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe main multiverse restricted #Added by software-properties' updated to new dist
2010-07-19 15:52:56,742 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main multiverse restricted'
2010-07-19 15:52:56,742 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main multiverse restricted' updated to new dist
2010-07-19 15:52:56,742 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted #Added by software-properties'
2010-07-19 15:52:56,742 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe main multiverse restricted #Added by software-properties' updated to new dist
2010-07-19 15:52:56,742 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe'
2010-07-19 15:52:56,743 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe' updated to new dist
2010-07-19 15:52:56,743 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe'
2010-07-19 15:52:56,743 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe' updated to new dist
2010-07-19 15:52:56,743 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main multiverse restricted'
2010-07-19 15:52:56,743 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security main multiverse restricted' updated to new dist
2010-07-19 15:52:56,743 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted #Added by software-properties'
2010-07-19 15:52:56,743 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security universe main multiverse restricted #Added by software-properties' updated to new dist
2010-07-19 15:52:56,743 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe'
2010-07-19 15:52:56,744 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security universe' updated to new dist
2010-07-19 15:52:56,751 DEBUG running doUpdate() (showErrors=True)
2010-07-19 15:54:07,554 DEBUG openCache()
2010-07-19 15:54:10,444 DEBUG /openCache()
2010-07-19 15:54:17,546 DEBUG Installing 'python2.4-minimal' (priority in required set 'required' but not scheduled for install)
2010-07-19 15:54:17,779 DEBUG Installing 'ash' (priority in required set 'required' but not scheduled for install)
2010-07-19 15:54:18,176 DEBUG Running KeepInstalledSection rules
2010-07-19 15:54:18,253 DEBUG Kernel uname: '2.6.24-28-generic' 
2010-07-19 15:54:18,260 DEBUG nvidiaUpdate()
2010-07-19 15:54:18,286 DEBUG Removing 'nvidia-glx-new-envy' (old nvidia driver)
2010-07-19 15:54:18,585 INFO installing nvidia-glx-177 as suggested by NvidiaDetector
2010-07-19 15:54:18,585 DEBUG Removing 'libflashsupport' (Distro PostUpgradeRemove rule)
2010-07-19 15:54:18,586 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2010-07-19 15:54:18,586 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2010-07-19 15:54:18,586 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2010-07-19 15:54:18,728 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2010-07-19 15:54:18,871 DEBUG Purging 'python2.3' (Distro PostUpgradePurge rule)
2010-07-19 15:54:18,871 DEBUG quirks: running intrepidPostDistUpgradeCache
2010-07-19 15:54:18,872 DEBUG running intrepidPostDistUpgradeCache
2010-07-19 15:54:18,941 DEBUG found nvidia-glx-177 video driver
2010-07-19 15:54:18,941 DEBUG Installing 'kdelibs5-dev' (kdelibs4-dev -> kdelibs5-dev transition)
2010-07-19 15:54:19,468 ERROR Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'
2010-07-19 15:54:19,470 DEBUG openCache()
2010-07-19 15:54:19,704 DEBUG /openCache()


what you think, why i can't upgrate from 8.-4 to 8.10?

---

