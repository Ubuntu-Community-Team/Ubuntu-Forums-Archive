---
title: "&quot;Getting Upgrade Prerequisites failed:The system was unable to get the prerequisites&quot;"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by superyounan1 on 2007-10-18
Scroll down to see the screenshot

It was in the "preparation" phase after downloading the files. 

in /var/log/dist-upgrade i have these files:

apt.log
apt-autoinst-fixup.log
main.log
term.log (empty)

apt.log is huge, over 800 lines, here is the last bit of it:
```
Investigating libcompizconfig0
Package libcompizconfig0 has broken dep on compizconfig-plugin
  Considering compizconfig-plugin -1 as a solution to libcompizconfig0 6
  Added compizconfig-plugin to the remove list
  Fixing libcompizconfig0 via remove of compizconfig-plugin
Investigating kiba-settings
Package kiba-settings has broken dep on gset-kiba
  Considering gset-kiba 1 as a solution to kiba-settings 0
  Holding Back kiba-settings rather than change gset-kiba
Investigating gset-kiba
Package gset-kiba has broken dep on kiba-settings
  Considering kiba-settings 0 as a solution to gset-kiba 1
  Holding Back gset-kiba rather than change kiba-settings
 Try to Re-Instate gset-kiba
Done
MarkUpgrade() called on a non-upgrable pkg: 'kubuntu-desktop'
ERROR:root:gor error from PostInstallScript ./apt-autoinst-fixup.py ([Errno 2] No such file or directory: './apt-autoinst-fixup.py')
```

and my main.log
```
2007-10-18 11:53:42,920 INFO release-upgrader version '0.81' started
2007-10-18 11:53:43,881 DEBUG lsb-release: 'feisty'
2007-10-18 11:53:43,881 DEBUG _pythonSymlinkCheck run
2007-10-18 11:53:45,069 DEBUG checkViewDepends()
2007-10-18 11:53:45,069 DEBUG getRequiredBackports()
2007-10-18 11:54:02,889 DEBUG marking 'release-upgrader-apt' for install
2007-10-18 11:54:03,015 DEBUG marking 'release-upgrader-dpkg' for install
2007-10-18 11:55:57,581 DEBUG pre-requists item: '<pkgAcquire::ItemIterator object: Status: 2 Complete: 1 Local: 0 IsTrusted: 0 FileSize: 1924684 DestFile:'/tmp/tmpMabuia/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' DescURI: 'http://us.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-dpkg/release-upgrader-dpkg_1.14.5ubuntu11.2' 
2007-10-18 11:55:57,581 ERROR pre-requists item 'http://us.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-dpkg/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' is NOT trusted
```

---

### Post by wise_owl on 2007-10-18
I had an identical problem when trying to upgrade.  I have attempted to do so twice and had the same message pop up.

---

### Post by superyounan1 on 2007-10-18
Its on launchpad, please confirm the bug there and post your log. I signed up for launchpad just today to confirm it, 

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/153980](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/153980)

---

### Post by superyounan1 on 2007-10-18
bump

some people are saying this problem is due to bandwidth issues, but I'm currently upgrading another pc at home (on the same connection) without a problem.

---

