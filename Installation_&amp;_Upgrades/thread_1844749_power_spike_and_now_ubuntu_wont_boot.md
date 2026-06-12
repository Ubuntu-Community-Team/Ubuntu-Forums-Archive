---
title: "power spike and now ubuntu wont boot"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by dewcansam on 2011-09-15
Just need a little help getting started. I was creating a new system and had it completely up and running when we got hit with a power spike and now it wont boot. Turns out there is nothing wrong with the hardware. I can replace the hdd (hdd2) and install ubuntu and it works fine. However, I have not been able to get my system configured the way it was. So... I really want to rescue the original hdd (hdd1), i have tested hdd1 and there is noting wrong with it either. Meaning that the problem lies within hdd1's ubuntu config. 
The system goes through the bios no problem but as soon as it starts to read hdd1 it just sits there. I can say that there may be a issue with the video card driver. I was alerted to the fact that there was a proprietary driver available and that i had installed that but had not restarted the system, so the power spike would have restarted the system using the new driver.

one more thing - is there any way that i can see all the packages that i installed on a system that is not running? I tried installing ubuntu then grabbing all the files from /var/cache/apt then just installing them on the fresh install. And it seems to really screw the system up.

If someone can just get pointed in the right direction thanks

---

### Post by oldfred on 2011-09-15
Have you tried fsck? Often any abnormal shut down needs file check if system is not damaged, but files may not have been closed correctly.

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

If you can get into system, list is just names of packages, so new install will be current version:
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

IF not try this.
Location of downloaded debs, but versions have to be the same.
/var/cache/apt/archives/

All the data on what packages are installed is contained under the /var/lib/dpkg/ directory.
It's all in the status file - every installed package has the word "installed" on it's Status: line.
However, it's probably easiest to just get the directory listing of the /var/lib/dpkg/info/ directory. Just look at all the files named *.list:
cd /var/lib/dpkg/info
ls *.list | sed 's/\.list$//'

---

