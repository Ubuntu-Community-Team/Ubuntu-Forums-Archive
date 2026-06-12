---
title: "ubi-partman failed with exit code 10 - ASUS F555U"
date: 2016-11-16
forum: Installation &amp; Upgrades
---

### Post by Leegion on 2016-11-16
Hello, used Ubuntu for several years, switched to Windows 10 a little over a year ago and now I'm switching back.

Made a USB key for Ubuntu 16.10.  While installing, it says:

"ubi-partman failed with exit code 10.  Further information may be found in /var/log/syslog.  Do you want to try running this step again before continuing?  If you do not, your installation may fail entirely or may be broken."

Every time I try again, the same error pops back up.  I searched around for the error code, but all topics I found on it are from years ago with older versions of ubuntu and the proposed solutions do not work.

---

### Post by oldfred on 2016-11-16
When you look in /var/log/syslog what does it say? 
That will only be on live installer while installing.

Also post this:
sudo parted -l

I do prefer to partition in advance with gparted. 
But are you installing in BIOS or UEFI boot mode. How you boot installer is then how it installs.
BIOS would need MBR partitioning, and UEFI would need gpt partitioning.

Multiple thread seem to say similar models need boot parameter.
 ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)
[http://ubuntuforums.org/showthread.php?t=2327570](http://ubuntuforums.org/showthread.php?t=2327570)
Installing 15.04 on Asus N550JX, boot parameters required
[http://ubuntuforums.org/showthread.php?t=2293394](http://ubuntuforums.org/showthread.php?t=2293394)

---

### Post by Leegion on 2016-11-16
The terminal won't open for me.  I'm using UEFI partitioning, so I'll try using gparted to partition in advance.

---

