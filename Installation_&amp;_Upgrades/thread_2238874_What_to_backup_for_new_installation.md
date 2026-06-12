---
title: "What to backup for new installation"
date: 2014-08-10
forum: Installation &amp; Upgrades
---

### Post by Tristan_Williams on 2014-08-10
I have the 32-bit version of Xubuntu 14.04.1 installed, and I want to do a fresh install of the 64-bit version

How can I do that so I don't lose any of the installed applications with their configurations, or home directories?

---

### Post by mastablasta on 2014-08-11
i think you will need to reinstall the applications anyway since you need the 64 bit versions of them. otherwise home has the settings and files by default. I think alt+h shortcut will show the hidden files in nautilus.

---

### Post by coldraven on 2014-08-11
I'm not sure if what you want is possible. I usually make a backup of the home folder including the hidden config files and then do a fresh install.
Don't forget to export your bookmarks and add it to your backup.

---

### Post by Tristan_Williams on 2014-08-11
> **coldraven said:**
> I'm not sure if what you want is possible. I usually make a backup of the home folder including the hidden config files and then do a fresh install.
Don't forget to export your bookmarks and add it to your backup.

Bookmarks?

---

### Post by oldfred on 2014-08-11
Firefox has bookmarks in /home if you have the standard locations of Firefox's profile.

You do want to export a list of installed apps if you have installed a lot. But list is a huge text file which you can edit. But often better to houseclean in old install before exporting list. If app is already installed in new install it will not reinstall it.

         Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

 Some temp files & folders to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

If you manually edited system files, like grub, Internet, or others you may not to save /etc. It is not huge, but do not just restore as setting may need to be different.

 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

Back with 10.10, I converted from 32 bit to 64 bit, but installed to a new 25GB / (root) partition and separated my data from /home into a separate /mnt/data partition. That did give me the convenience of finding anything I forgot in old install.

      
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

### Post by Tristan_Williams on 2014-08-11
Thanks

---

