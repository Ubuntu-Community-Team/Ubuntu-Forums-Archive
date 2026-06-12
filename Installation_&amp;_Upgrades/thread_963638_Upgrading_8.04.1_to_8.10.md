---
title: "Upgrading 8.04.1 to 8.10"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Zanian on 2008-10-30
Hey,
I'm trying to install the upgrade through the update manager, however, when I get to "Setting New Software Channels" I get the following error:

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

This is from /var/log/dist-upgrade/main.log:
2008-10-30 12:19:03,462 INFO release-upgrader version '0.93.32' started
2008-10-30 12:19:04,087 DEBUG svg pixbuf loader failed (Error displaying image)
2008-10-30 12:19:04,270 DEBUG Using 'DistUpgradeViewGtk' view
2008-10-30 12:19:04,356 DEBUG enable dpkg --force-overwrite
2008-10-30 12:19:04,489 DEBUG lsb-release: 'hardy'
2008-10-30 12:19:04,490 DEBUG _pythonSymlinkCheck run
2008-10-30 12:19:04,509 DEBUG openCache()
2008-10-30 12:19:06,537 DEBUG /openCache()
2008-10-30 12:19:06,538 DEBUG needServerMode(): run in 'desktop' mode, (because of key deps for 'ubuntu-desktop')
2008-10-30 12:19:06,538 DEBUG checkViewDepends()
2008-10-30 12:19:06,538 DEBUG running doUpdate() (showErrors=False)
2008-10-30 12:19:26,623 DEBUG openCache()
2008-10-30 12:19:28,826 DEBUG /openCache()
2008-10-30 12:19:28,826 DEBUG doPostInitialUpdate
2008-10-30 12:19:28,826 DEBUG quirks: running intrepidPostInitialUpdate
2008-10-30 12:19:28,826 DEBUG running intrepidPostInitialUpdate
2008-10-30 12:19:30,266 DEBUG Foreign: 
2008-10-30 12:19:30,266 DEBUG Obsolete: songbird
2008-10-30 12:19:30,267 DEBUG updateSourcesList()
2008-10-30 12:19:30,363 DEBUG rewriteSourcesList()
2008-10-30 12:19:30,366 DEBUG examining: 'deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted'
2008-10-30 12:19:30,366 DEBUG entry 'deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid main restricted' updated to new dist
2008-10-30 12:19:30,366 DEBUG examining: 'deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted'
2008-10-30 12:19:30,366 DEBUG entry 'deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid main restricted' updated to new dist
2008-10-30 12:19:30,367 DEBUG examining: 'deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted'
2008-10-30 12:19:30,367 DEBUG entry 'deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted' updated to new dist
2008-10-30 12:19:30,367 DEBUG examining: 'deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted'
2008-10-30 12:19:30,367 DEBUG entry 'deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted' updated to new dist
2008-10-30 12:19:30,367 DEBUG examining: 'deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe'
2008-10-30 12:19:30,367 DEBUG entry 'deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid universe' updated to new dist
2008-10-30 12:19:30,368 DEBUG examining: 'deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe'
2008-10-30 12:19:30,368 DEBUG entry 'deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid universe' updated to new dist
2008-10-30 12:19:30,368 DEBUG examining: 'deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe'
2008-10-30 12:19:30,368 DEBUG entry 'deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates universe' updated to new dist
2008-10-30 12:19:30,368 DEBUG examining: 'deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe'
2008-10-30 12:19:30,368 DEBUG entry 'deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates universe' updated to new dist
2008-10-30 12:19:30,368 DEBUG examining: 'deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse'
2008-10-30 12:19:30,369 DEBUG entry 'deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid multiverse' updated to new dist
2008-10-30 12:19:30,369 DEBUG examining: 'deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse'
2008-10-30 12:19:30,369 DEBUG entry 'deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid multiverse' updated to new dist
2008-10-30 12:19:30,369 DEBUG examining: 'deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse'
2008-10-30 12:19:30,369 DEBUG entry 'deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse' updated to new dist
2008-10-30 12:19:30,369 DEBUG examining: 'deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse'
2008-10-30 12:19:30,369 DEBUG entry 'deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse' updated to new dist
2008-10-30 12:19:30,370 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted'
2008-10-30 12:19:30,370 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted' updated to new dist
2008-10-30 12:19:30,370 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted'
2008-10-30 12:19:30,370 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted' updated to new dist
2008-10-30 12:19:30,370 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe'
2008-10-30 12:19:30,370 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe' updated to new dist
2008-10-30 12:19:30,370 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe'
2008-10-30 12:19:30,371 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe' updated to new dist
2008-10-30 12:19:30,371 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse'
2008-10-30 12:19:30,371 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse' updated to new dist
2008-10-30 12:19:30,371 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse'
2008-10-30 12:19:30,371 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse' updated to new dist
2008-10-30 12:19:30,380 DEBUG running doUpdate() (showErrors=True)
2008-10-30 12:20:13,545 DEBUG openCache()
2008-10-30 12:20:13,958 DEBUG /openCache()
2008-10-30 12:20:14,058 DEBUG Running KeepInstalledSection rules
2008-10-30 12:20:14,063 DEBUG Kernel uname: '2.6.24-19-generic' 
2008-10-30 12:20:14,108 DEBUG nvidiaUpdate()
2008-10-30 12:20:14,183 INFO no old nvidia driver installed, installing no new
2008-10-30 12:20:14,184 DEBUG Removing 'libflashsupport' (Distro PostUpgradeRemove rule)
2008-10-30 12:20:14,184 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2008-10-30 12:20:14,184 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2008-10-30 12:20:14,184 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2008-10-30 12:20:14,184 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2008-10-30 12:20:14,184 DEBUG Purging 'python2.3' (Distro PostUpgradePurge rule)
2008-10-30 12:20:14,185 DEBUG quirks: running intrepidPostDistUpgradeCache
2008-10-30 12:20:14,185 DEBUG running intrepidPostDistUpgradeCache
2008-10-30 12:20:14,190 DEBUG Removing 'landscape-client' (custom landscape stub removal rule)
2008-10-30 12:20:14,250 DEBUG none of the '['ubuntu-desktop', 'kubuntu-desktop', 'edubuntu-desktop', 'xubuntu-desktop', 'ubuntustudio-desktop', 'ichthux-desktop', 'mythbuntu-desktop', 'kubuntu-kde4-desktop']' meta-pkgs installed
2008-10-30 12:20:14,250 DEBUG guessing 'ubuntu-desktop' as missing meta-pkg
2008-10-30 12:20:14,251 ERROR failed to mark 'ubuntu-desktop' for install ('ubuntu-desktop')

Thanks :)

---

### Post by Zanian on 2008-10-30
Problem solved, thanks.

---

### Post by AlexH76 on 2008-10-31
Had same error.. Found workaround in [bugreport 277389]("https://bugs.launchpad.net/ubuntu/+source/kubuntu-kde4-meta/+bug/277389")

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

