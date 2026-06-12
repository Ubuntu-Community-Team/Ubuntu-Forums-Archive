---
title: "Move Ubuntu 12.04 from one HD to another"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by pabloikba on 2012-07-05
My computer has one 1TB HD (sda) and 1 500GB HD (sdc). Ubuntu 10.10 is installed on the 1TB HD. I installed 12.04 on the 500GB HD and am now satisfied that I have moved all files I wanted from the 10.10 HD to the 500GB Ubuntu 12.04 HD.
I want to get rid of the 10.10 installation and move the 12.04 installation to the 1TB HD. Is it possible to do this and, if so, how?
Many thanks,
Pablo

---

### Post by oldfred on 2012-07-06
There are several ways to move it and each requires some editing of UUIDs, fstab and reinstall of grub2's boot loader to the MBR.

You can do image copies, but cannot have duplicate UUIDs so they have to be changed if you want both drives still connected. Some have used dd (nickname Data Destroyer) which can work but any typo destroys data and you have to edit UUIDs.

While you can do the move, I suggest a reinstall. You then can move /home and export a list of installed applications and you will have the same version on both drives. If you do not want to down load all the applications and are installing exactly the same version and have not housecleaned you can copy the .debs to the new install to save downloading. I like having fully workable systems on different drives, just in case one drive fails. Although I also have liveCD/USB and a full install on a flash drive also. :)

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I assume if system crashes I will reinstall, so my backup procedure is to have everything I need to restore.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

Location of downloaded debs
/var/cache/apt/archives/

discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

Move entire OS to another drive - but new install often easier
[http://ubuntuforums.org/showthread.php?t=1929671](http://ubuntuforums.org/showthread.php?t=1929671)

---

### Post by pabloikba on 2012-07-06
Thank you! I appreciate your time....
I will try to accomplish the task and let you know how it turns out.
Pablo

---

