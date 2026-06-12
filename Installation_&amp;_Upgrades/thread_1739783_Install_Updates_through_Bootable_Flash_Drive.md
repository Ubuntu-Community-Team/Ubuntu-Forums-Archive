---
title: "Install Updates through Bootable Flash Drive?"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by GreenRaccoon on 2011-04-26
I have Ubuntu Natty Narwhal Beta 2.  I was installing updates this morning, but as they were installing, my hardware crashed (perfect timing).  I was forced to do a hard shut down.  Now my desktop won't load.

I thought that if I tried to reinstall the updates, the problem would (hopefully) be fixed.  Is there a way to install updates if I boot through a flash drive?  If so, how would I do it?

---

### Post by oldfred on 2011-04-26
You can use a liveCD or USB to boot and then chroot into your system. Then you can run all the updates which should finish what was started.

Instructions on chrooting:
drs305 chroot to reinstall grub2 (you probably do not need grub reinstall)
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)
kansasnoob- full chroot one line version with &&----
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
Commands once in chroot:
if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by GreenRaccoon on 2011-04-27
Problem solved. Thanks!

---

