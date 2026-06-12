---
title: "Upgrading from 32bit to 64 bit (backup options)"
date: 2014-10-06
forum: Installation &amp; Upgrades
---

### Post by reyes99 on 2014-10-06
Hi,

I currently have Ubuntu 14.04 32 bit and I would like to install Ubuntu 14.04 64 bit from scratch but I would like to know if there is a way to backup your apps and settings and migrate them to the 64 bit.

Thank you

---

### Post by oldfred on 2014-10-06
I did this back with 9.10 and now my backup includes everything I think I need to do a new clean install. I do not backup Ubuntu. You can export list of installed applications. It is very long as it includes all depends or lower level files. It will not reinstall anything already installed by default. It is a text file so you can manually edit it also. But generally better to houseclean with synaptic first anyway.

All your files and user settings are in /home. Only if you made specific system setting changes, such as grub or Internet might you have some settings in /etc also.

       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

You do not need temporary files & caches:
Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

      More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

If you have a separate /home, you can just reuse it, but have to use the Something Else install option. You choose existing / (root) as new / and reformat as ext4, but select /home and do NOT tick the format back.
      
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by reyes99 on 2014-10-07
Thank you so much for the info, that is exactly what I was looking for.

---

