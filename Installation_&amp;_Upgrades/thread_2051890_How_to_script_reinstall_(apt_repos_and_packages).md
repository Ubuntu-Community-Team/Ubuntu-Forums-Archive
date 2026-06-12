---
title: "How to script reinstall (apt repos and packages)"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by Kurtosis on 2012-09-02
I need to wipe my hard drive and reinstall Ubuntu.  /home is on a separate partition, so I can back that up to a backup drive, then copy it back to the wiped drive, install ubuntu, and point it at the existing /home, [no problem]("http://www.ibm.com/developerworks/linux/library/l-partplan/index.html").

However, I also want to script a reinstall of all my apt repo's and the packages I currently have installed, so I don't have to waste hours doing that manually.  Anyone know a good way to do this?

PS - At least, I'm pretty sure I have to wipe the drive.  Need to reinstall factory Windows 7 to dual boot, and only have an HP system restore disk that formats the whole drive, and not a legit Windows 7 install disk that lets me install on a single partition.  If somebody know a way to trick the system restore disk to install only to a single partition, I'd love to hear it.

---

### Post by tienlbhoc on 2012-09-02
backup by aptoncd
[http://ubuntuofflineinstall.blogspot.com/2012/09/aptoncd.html](http://ubuntuofflineinstall.blogspot.com/2012/09/aptoncd.html)

---

### Post by oldfred on 2012-09-02
I use this:

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

But I have two scripts as I have other partitions I want to re-add to fstab, and some system files I edit. Then I install my applications. Some I have hardcoded, then then they are duplicated in my update from dpkg list. If installing a new version of Ubuntu you do have to check that you do not install older apps like OpenOffice when LibreOffice is now the standard as you do not need both. 

From my script where ubuntu-files is text list of apps.
```
apt-get install dselect

apt-get update
apt-get dist-upgrade
# Finally, install all the packages from previous install
# must have saved ubuntu-files from previous install to this directory
dpkg --set-selections < ubuntu-files
#dselect
apt-get -y update
apt-get dselect-upgrade

```

---

### Post by Kurtosis on 2012-09-03
Excellent, will try both, thanks so much guys!

---

### Post by Kurtosis on 2012-09-24
Now that it's done, just want to update this thread for posterity.

The manual way, using only 1st party Ubuntu/Debian/Linux tools is, in a nutshell, backup sources.list and your installed packages, do the reinstall, then restore them.

[LIST=1]
[*]sudo cp /etc/apt/sources.list ~/sources.list
[*]sudo dpkg --get-selections > ~/my-packages
[*][Great article on how to move /home among disks and partitions the easy way, with cp -ax.]("http://www.ibm.com/developerworks/linux/library/l-partplan/index.html")
[*][LiveCD/USB with BootRepair included (Official Ubuntu LiveCD/USB doesn't include this valuable tool)]("https://help.ubuntu.com/community/UbuntuSecureRemix")
[/LIST]

Only problem may be some sources won't have their keys (especially PPAs you added via 'add-apt-repository'), and you'll have to look up their key and add it with a 'sudo apt-key add'.

---

### Post by oldfred on 2012-09-24
Glad it worked. :)

You can change to solved, so others may see what worked. (see my signature).

---

