---
title: "Upgrade from x86 to 64-bit"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by slipkid on 2013-02-21
Hey everyone,

Few days back I've installed Lubuntu 12.10 x84 version. It was going ok, but I've realised that my CPU can handle 64-bit version of the OS. 

So the question is - can I (if yes, how? I'm rather new Linux user) upgrade mu Luubntu to 64-bit version without loosing my data? 

I've tried to find something on the Internet and this forum, but no luck. I'll be gratefull for every hint and reply!

Best regards

---

### Post by oldos2er on 2013-02-21
There's no upgrade path from 32- to 64-bit, you'll need to do a fresh install.

---

### Post by oldfred on 2013-02-21
Welcome to the forums.

Do you have a separate /home. Then you can just reinstall using Something Else and when choosing /home DO NOT reformat.

Otherwise you need to backup /home. If you have installed a lot of applications you also want to make a list to make it easier to reinstall.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

    
       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

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

---

