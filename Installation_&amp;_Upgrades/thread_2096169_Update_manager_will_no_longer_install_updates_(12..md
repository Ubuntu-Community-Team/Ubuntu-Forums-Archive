---
title: "Update manager will no longer install updates (12.04)"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by The_Cougar_Kid on 2012-12-19
I am having a problem on my wife's PC (Ubuntu 12.04).   Update manager says there are 108 updates to install but when we try to  install them it fails with this message:

installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
dpkg: error: parsing file '/var/lib/dpkg/available' near line 0: 
 field name `../libindicator-messages-status-provider1/changelog.Debian.gz' must be followed by colon 
localepurge: Disk space freed in /usr/share/locale: 0 KiB 
localepurge: Disk space freed in /usr/share/man: 0 KiB 
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB 
localepurge: Disk space freed in /usr/share/omf: 0 KiB 
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB 
 
Total disk space freed by localepurge: 0 KiB 
 
localepurge: Disk space freed in /usr/share/locale: 0 KiB 
localepurge: Disk space freed in /usr/share/man: 0 KiB 
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB 
localepurge: Disk space freed in /usr/share/omf: 0 KiB 
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB 
 
Total disk space freed by localepurge: 0 KiB 
 
localepurge: Disk space freed in /usr/share/locale: 0 KiB 
localepurge: Disk space freed in /usr/share/man: 0 KiB 
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB 
localepurge: Disk space freed in /usr/share/omf: 0 KiB 
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB 
 
Total disk space freed by localepurge: 0 KiB 
 
localepurge: Disk space freed in /usr/share/locale: 0 KiB 
localepurge: Disk space freed in /usr/share/man: 0 KiB 
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB 
localepurge: Disk space freed in /usr/share/omf: 0 KiB 
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB 
 
Total disk space freed by localepurge: 0 KiB






Any ideas please?

---

### Post by wladypauly on 2012-12-19
Try ```
 sudo dpkg-reconfigure libindicator-messages
``` to reconfigure the package, then do the updates as usual and see if it solved the problem.

---

### Post by The_Cougar_Kid on 2012-12-19
> **wladypauly said:**
> Try ```
 sudo dpkg-reconfigure libindicator-messages
``` to reconfigure the package, then do the updates as usual and see if it solved the problem.

Thanks for responding

I tried that and it produced:
sudo dpkg-reconfigure libindicator-messages
[sudo] password for dorothy: 
Package `libindicator-messages' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: libindicator-messages is not installed.

I tried instead 
sudo dpkg-reconfigure libindicator-messages-status-provider1

which ran without reporting errors but the updates sill would not work.  I am planning to reboot and see if it works then...

---

### Post by The_Cougar_Kid on 2012-12-19
It is still failing to install with the same message after a reboot....

---

### Post by dannyboy79 on 2012-12-19
possible answer here: [http://askubuntu.com/questions/55099/dpkg-error-parsing-file-var-lib-dpkg-available-near-line-0](http://askubuntu.com/questions/55099/dpkg-error-parsing-file-var-lib-dpkg-available-near-line-0)

---

### Post by The_Cougar_Kid on 2012-12-19
Briiliant - problem solved!!  thanks very much

---

### Post by dannyboy79 on 2012-12-19
> **The_Cougar_Kid said:**
> Briiliant - problem solved!!  thanks very much
awesome, use the thread tools and mark it solved.

---

