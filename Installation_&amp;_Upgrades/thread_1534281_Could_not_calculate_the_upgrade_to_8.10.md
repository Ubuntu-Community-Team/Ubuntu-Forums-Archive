---
title: "Could not calculate the upgrade to 8.10"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by sgeorgiev111 on 2010-07-19
hello, i have problem with upgrade manager. i try upgrade fron 8.04 to 8.10. where is my main.log:


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


i think that i really have brocken package > 2010-07-19 15:52:55,641 DEBUG no PkgRecord found for  'linux-ubuntu-modules-2.6.22-15-generic', skipping 
2010-07-19 15:52:56,451 DEBUG no PkgRecord found for  'linux-ubuntu-modules-2.6.22-14-generic', skipping , but i cant uninstall it

---

### Post by ajgreeny on 2010-07-19
You can not upgrade to 8.10 because that version of Ubuntu is no longer supported and repositories are no longer available.  Support finished in April 2010, 18 months after release, as is normal for a standard Ubuntu version as opposed to a LTS version, eg. 10.04.

I think you will have to do a clean install if you want to have a newer version.  Try 10.04.

---

