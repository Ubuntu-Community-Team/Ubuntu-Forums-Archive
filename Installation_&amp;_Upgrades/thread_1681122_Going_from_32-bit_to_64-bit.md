---
title: "Going from 32-bit to 64-bit"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by wphred on 2011-02-03
I want to upgrade from 10.4.lts 32-bit to 10.4 64 bit. Do I need to backup data and take other precautions, or should the upgrade be transparent?

---

### Post by mörgæs on 2011-02-03
You can not upgrade. You need a back up of your files and a reinstall.

Have you tried running the 64 bit version as a live CD?

---

### Post by zvacet on 2011-02-03
I don´t think you can upgrade.You need fresh install.

---

### Post by him610 on 2011-02-03
> Do I need to backup data and take other precautions

Yes, if you value your data.

---

### Post by oldfred on 2011-02-03
You need to backup /home or have /home as a separate partition. You may have some system settings in /etc, but do not reinstall, save for reference only if needed.

You should make a list of all installed applications to make it easily to reinstall. (I did not do this the first time I did a new install, but installed to another partition so I had the old partition to refer to.):

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

If you have a separate /home and/or a separate /data for all your data, you can just create a new 20GB / partition and install. If programs in /home get updated, you may not have good settings if you want to go back, so have a backup either way.

---

