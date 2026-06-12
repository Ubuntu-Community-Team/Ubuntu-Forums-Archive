---
title: "32-&gt;64 bit upgrade"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by kmand on 2012-07-04
Is it possible to upgrade from a 32 bit 12.04 to a 64 bit 12.04 without starting from scratch? I'd hate to try and remember everything thats installed and how they are configured.

---

### Post by cipherboy_loc on 2012-07-04
Reinstalling is the only way I know of to go from 32 bit to 64 bit is by re-installing. You can of course back up config settings and the like (along with installed programs) to make the transition easier, but you should wait for another person's opinion before reinstalling.


Cipherboy

---

### Post by fantab on 2012-07-04
A Fresh install is the BEST way to move from 32bit to 64bit. And it is better to install and configure everything from scratch to avoid conflicts, if any.

---

### Post by oldfred on 2012-07-05
Your user settings are in /home. If you made some system settings they will be in /etc (but I would never copy them back unless I knew I had to as a new version may have totally different settings).

You can easily export a list of installed applications and copy /home to a new partition and/or back it up.

Note that you may reinstall some older apps if upgrading to a new version. List is a text file and very long as it lists everything, but you can edit to remove old packages.
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

