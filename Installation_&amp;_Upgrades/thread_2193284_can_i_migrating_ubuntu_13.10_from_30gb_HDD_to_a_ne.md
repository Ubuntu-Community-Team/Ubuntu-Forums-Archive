---
title: "can i migrating ubuntu 13.10 from 30gb HDD to a new HDD?"
date: 2013-12-12
forum: Installation &amp; Upgrades
---

### Post by erpojoh on 2013-12-12
i have installed ubuntu 13.10 into old harddisk drive 30GB. .now i want to migrating it into new harddisk drive 120GB. can i do that?? i dont want to fresh install it because of all update and package installed. .
thanks for your help. GBU

---

### Post by oldfred on 2013-12-12
Move entire OS to another drive - but new install often easier
[http://ubuntuforums.org/showthread.php?t=1929671](http://ubuntuforums.org/showthread.php?t=1929671)

I suggest fresh install. And copy /home. You can copy downloaded .debs if you have not housecleans and make a list of installed apps to reinstall to make sure you have all of them.
 Location of downloaded debs
/var/cache/apt/archives/

 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages

I save new list of installed apps into my /home as part of my rsync backup of /home so I can reinstall and restore system to as it was.

But you can use imaging backup software like clonezilla or use dd, but have to be very careful with dd as any typo can erase data.  Clonezilla just copies data, dd will also copy all blank space and is intended for size to size copy, so you will have to resize 30GB partition after copy.

 Full image backups
[http://clonezilla.org/](http://clonezilla.org/)

 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

 

But any clone or image will duplicate everything. Are you keeping 30GB plugged in? If so you have to change UUIDs on one or the other installs.

       Files that may need manual editing or update on image copy
 fstab, reinstall grub and grub's reinstall location. Or change UUIDs

 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc

If different computer:
/etc/hostname and /etc/hosts,

 Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

---

### Post by erpojoh on 2013-12-13
thanks for reply. .now i will try it. .
if i have a problem. .i will ask you later. .

---

